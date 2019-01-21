# Yapen Django ver.

##### 2019/1/21 월


무슨 프로젝트를 할까 하다가 너무 많은 시간이 지나버렸다.
이대로는 여태했던 모든게 흐지부지 될거 같아서 패스트캠퍼스 프로젝트로 했던 야놀자펜션 COPY site를 Django만 사용하여 만들어 보기로 했다. <del>(다행히 달라진건 없는듯..)</del>

##### 오늘 한일

1. 프로젝트 정하기
2. Django 기본 셋팅
3. User model을 기본 User모델을 상속받게 한 후 migration 


##### 에러

1. User model을 AbstractUser를 상속받고 바로 makemigration하는 과정에서 에러발생
	* settings.py에 `AUTH_USER_MODEL`을 추가해줌으로써 에러를 처리


##### 구현해야할 기능

1. 회원가입 및 로그인
	* 가능하다면 이메일, 모바일 인증과 페이스북 외 다른 소셜로그인
2. 펜션리스트, 디테일
3. 개인정보 디테일
	* 패스워드 변경등등
4. 예약 및 조회
5. Template은 Bootstrap을 이용할 예정 

