# Ask Django

* 아임포트
* 쇼핑몰

### 이니시스(PG)

```
User -> Service -> PG -> Service -> User
```

많은 PG사들은 ASP/PHP/JSP 샘플만 제공

* 결제부분만 `php-cli`를 통해 PHP로 처리하기도 함
* UTF-8이 아닌 euc-kr 인코딩을 쓰기도 함

### 아임포트(IAMPORT)

* 각 PG사들에 대한 Gateway
* 단일 API로 국내 많은 PG사들을 커버
	* 개발환경에 중립적
	
```
Service -> Iamport -> Pg -> Iamport -> Service
```

> 카카오페이, 이니시스(웹표준결제), 나이스페이..

* JavaScript 코드 하나로 PC/Mobile/In-App 결제 모두 지원

* 기본기능에 대해서 FREE
	* 1개 PG사 연동
	* 기본 관리자 대시보드
	* 기본 기능 사용 제약 없음
* 유료부분
	* 2개 이상 PG사 연동(최초 1회만 10만원)
	* 결제 데이터 분석(월 39,000원)

### Process

1. 구매자는 카드사 웹페이지를 통해 카드번호/유효시간/비밀번호를 입력하여 카드를 확인
	* 이때, 카드정보의 보호를 위해 별도의 프로그램 설치를 요구
2. 카드정보가 확인되면, 카드사는 `1회성 인증키`를 PG사에 제공하며, 이 인증키가 실제 결제에 사용됨
3. 가맹점 서버: 인증단계에서 사용된 주문번호, 구매자 연락처 등의 정보를 PG사 서버로 전송
4. PG사는 카드사로부터 전달된 인증키와 함께 해당 카드사로 승인요청을 진행
	* <b> 실제 카드사로부터 결제승인에 대한 결과를 알 수 있다.</b> 결제승인 혹은 결제실패(한도초과/분실카드 등의 사유)가 판단됨

### 안심클릭/ISP 결제모듈

* PC에서는 계열에 상관없이 동일한 인터페이스
* 모바일에서는 연동방식의 차이가 있음

`안심클릭`: 카드번호, CVC, 안심클릭 비밀번호를 입력하여 카드정보를 인증
- 별도의 앱이 필요없음, 모바일 브라우저나 WEbView 앱결제가 동일한 처리

`ISP`: 공개키 기반의 전자인증서를 통해 사전에 등록된 카드정보를 인증

- ISP앱 설치.인증서복사를 요구
- ISP를 거쳤다가, 다시 래 결제프로세스로 이동
- 다시 앱으로 돌아오기 위해, `URL Scheme` 정의/처리가 필요
	* http://로 요청을 할경우 웹요청인것을 앎
	* baemin://으로 시작하는 URL Scheme를 쓰겠다고 설정(앱의 경우)

### 비인증결제

* Key-in 결제: 전화를 통한 비대면 상황에서 카드정보 + 개인정보를 활용해 결제
* 빌링 결제: 정기 결제

개발자는 아임포트(IAMPORT)가 제공하는 표준화된 API로 간편히 연동

1. PG창 결제창 호출 -> 결제 결과 수신`IAMPORT-UID`
2. 결제 조회/검증(REST API)

### 방어적으로 코딩하기
> 결제프로세스 상 금액정보가 사용자에 의해 변경되어 시작될 수 있는 가능성이 있음

`가맹점 서버`단에서 <b>결제정보 조회 API</b>를 통한 체크가 필수 

```
if payment status == 'paid' and apyment.amount == 결제되었어야할금액:
	print('결제 성공')
elif payment.status == 'ready' and payment.pay_method == 'vbank':
	print('가상계좌 발급성공')
else:
	print('결제 실패')
	
```

`status` : Iamport측에서 결제상태를 알려줌

결제취소는 `REST API`를 이용하여 쉽게 가능

# 결제요청 파라미터
> <a href="https://admin.iamport.kr/">https://admin.iamport.kr </a>

* pg : PG사 미지정시에 아임포트 관리자에서 지정한 기본PG가 호출(string)
* pay_method : 결제수단(default:'card')(string)
* merchant_uid : 가맹점에서 생성/관리하는 고유 주문번호(string)
	* 결제가 실패하더라도, 재생성해야 함 
* name : 주문명(string)
* amount(필수) : 결제금액(number)
* buyer_name : 주문자명(string)
* buyer_tel(필수) : 주문자 연락처(string)
* buyer_email : 주문자 이메일(string)
* buyer_addr : 주문자 주소(string)
* buyer_postcode : 주문자 우편번호(string)
* buyer_postcode : 주문자 우편번호(string)
* notice_url : (string/ array of string)


