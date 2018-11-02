# Auth User Model

`authentication` : 사용자를 인증(Login)

`authorization` : 사용자가 가지고 있는 권한(게시판에 글쓰기등의 권한)

## session

* 우리가 쓰는 HTTP프로토콜(통신)은 비연속적
 
> ex) 방금 요청을 보낸 유저를 기억하지 못함
 
서버에서 클리이언트에 대한 unique한 value를 저장 -> `세션`
> ex) 서버에 'pmb'라는 key가 전달되면 유저는 '박명배'인 것으로 처리하도록 저장해놓음
>
> 클라이언트는 본인이 누구인지에 대한 key를 항상 서버에 보내줘야함
> 
> 이 때 브라우저가 쓰는 방식은 쿠키(cookie)

## cookie

* 브라우저에 저장된 값

* HTTP요청을 보낼 때 마다 해당 값을 항상 요청에 담아서 보냄(`Header`, 도메인 기준)
 
```
서버에서 HTTP Response를 보내줄 때 해당 HTTP응답에
	Set-Cookie라는 헤더로 'key'와 'value', '만료시간'을 보내주면
	브라우저가 해당 쿠키를 저장
```

* 클라이언트

```
-> 서버로 인증요청(username/password)
-> 서버는 해당 username/password를 확인해서 특정 User가 맞는지 확인
-> 맞다면, 해당 User와 연결되는 특별한 값을 서버에 저장(SessionID)
-> 그리고 그 SessionID를 브라우저에게 Set-Cookie Response헤더로 전달
-> 브라우저는 해당 SessionID를 자신의 쿠키공간에 저장
-> 이후 브라우저가 해당 서버에 Request를 보낼떄는 항상 SessionID를 함께 전달하게 됨
-> 서버는 받은 요청의 SessionID를 확인하고 특정 User와 연결된다면 그 User가 보낸 요청이라 생각
```

* MIDDLEWARE
```
django
	SessionMiddleware(sessionID를 관리해줌)
	AuthenticationMiddleware(인증을 관리)
	
Request -> Middleware -> View(Controller) -> Middleware ->Response

```



	
