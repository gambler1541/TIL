* 중간 모델중 필터 조건을 만족하지 않아도 django는 error를 일으키지 않는다.

#### F 표현식

> 파이썬의 연산을 DB에서

#### Q object

* Q object로 연산을 하면 또다른 Q object가 생성


```
Poll.object.get(
	Q(pub_date=date(2005, 5, 2)) | Q(pub_date=date(2005, 5, 6)),
	question__startwith='Who',
)


Poll.object.get(
	question__startwith='Who',
	Q(pub_date=date(2005, 5, 2)) | Q(pub_date=date(2005, 5, 6))
	)

```

아래 연산은 불가능

`why?`

파이썬 함수차원에서 함수의 인자는 위치인자, 키워드인자 순으로 

---

#### ORM

`.select_related` < 테이블을 한번만 경유

` prefetch_related` < 역방향
