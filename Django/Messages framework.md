## Messages framework

* 일반적인 경우

	* request -> context(알림데이터) -> render(알림데이터 표시)

* redirect를 쓰는 경우

	* reqeust -> ridirect response -> 브라우저는 redirect처리(알림을 표시할 방법 없음)

* messages framework를 쓰는 경우
	* view(messages에 알림 데이터와 어떤 client에게 보내야 하는지를 저장
		* django_session테이블에 있는 특정 session\_id값과 클라이언트(브라우저의 쿠키)가 가지고 있는 session\_id값을 비교해서 client를 특정화
	* redirect
	* view(이 client에게 message가 있다면, render시 해당 데이터를 함께 context에 담아 전송)
	* render(messages가 전달한 알림데이터를 표시)


* Messages framework는 미들웨어로 존재


### Message Level

|Constant|Purpose|
|---|---|
|DEBUG|프로덕션 배포에서 무시되거나 제거되는 개발 관련 메시지|
|INFO|사용자를 위한 정보 메시지|
|SUCCESS|작업이 성공적으로 완료됐을시 메시지|
|WARNING|실패는 발생하지 않았지만 임박했을시 메시지|
|ERROR|작업이 실패하거나 다른 오류가 발생|

* `로깅`메시지 단계와 같음

### 사용법

* 메시지가 필요한 view에서 message를 담아 보냄
* template에서 messages를 이용해 사용가능
	