## Django login required

`@login_required` 데코레이터 함수로 로그인이 안됐을 경우 뷰가 작동하지 않게 할 수 있음

* settings.LOGIN_URL로 리디렉션하고 쿼리 문자열에 현재 절대 경로를 전달(login을 한 후 원래 하려고 했던 url을 next값을 쿼리값으로 가지고 있음) 
* `LOGIN_URL` : login_required 데코레이터에 의해 로그인 페이지로 이동해야 할 때, 그 이동할 URL

### GET parameter에 'next'가 전달되었다면

`request.GET`에 `next`속성을 `next_path`로 지정 후 redirect가능