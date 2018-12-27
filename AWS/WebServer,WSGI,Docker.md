# WebServer,WSGI,Docker

* EC2
	* 클라이언트로부터의 접속을 설정
	* Django application이 실해되고 있는 서버 컴퓨터

request -> EC2 -> (runserver:8000)(개발 서버) -> Django
> 성능이 안좋음

Cloud Server(물리 서버, 가상 서버)

-> WebServer(사용자의 Request를 받고, 응답을 보내주는데 특화, 정적)

-> WSGI application(WebServer와 python web application을 중개)

-> Python Web application(동적으로 Response를 보내주는 기능)

* WebServer가 뭐든 WSGI의 규격에 맞게 코드를 짜면 Python Web application과의 연결이 가능

```
request -> EC2 -> Nginx(WebServer:80) -> uWSGI(WSGI) -> Django
```

##### 운영체제 가상화
Docker (Ubuntu)

* linux운영체제 에서만 돌아감

##### 파이썬 환경 가상화
virtualenv (Python)
