# 야놀자 펜션 Django Ver.

`url` : 우선 각 지역별 펜션의 이름, 대표img url등을 크롤링할 수 있는 페이지

```
params = {
    'location': '012',
    'subLocation': '1.012008'
}
url = 'http://www.yapen.co.kr/region?' + parse.urlencode(params)

===

url == http://www.yapen.co.kr/region?location=012&subLocation=1.012008
```

