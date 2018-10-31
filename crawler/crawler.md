# Requests

> Django에서 html에 request요청을 보내기위한 써드파티 라이브러리

설치 `pipenv install requests`

* 우리가 웹 브라우저를 통해 보는 HTML문서는 GET요청의 결과

```
reponse.text에 해당하는 데이터를 weekday.html이라는 파일에 기록

with open('weekday.html', 'wt') as f:
	f.write(reponse.text)
```

select = 모든 항목을 찾음

select_one = 한 항목만 찾음

parse_qs = 하나의 Key에 여러 개의 쿼리를 