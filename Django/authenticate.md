# Django Authenticate

django authenicate는 DB에 User가 있을 경우 User객체를 반환, 그렇지 않을 경우 `None`을 반환한다. 

> 없는 User로 로그인했을 경우(Authenticate를 실행했을 경우)
 
<img src="../img/authenticate_none.png">

> DB에 저장된 User로 Authenticate를 실행했을 경우

<img src="../img/authenticate_true.png">