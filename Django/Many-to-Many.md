# Many-To-Many
> 피자와 토핑의 관계

* 양쪽이 동일한 중요도를 가짐
* Many-to-Many는 새로운 테이블을 생성(각각의 id를 가지고 있음)
* 어디에 선언해도 상관없음(User가 읽기에 편한곳에 선언)

##### 중계테이블(Through)
* 기본 중계테이블은 생성 시 각 테이블의 pk값만 저장
* 추가사항이나 수정사항이 있을경우 테이블 속성값으로 `through`를 넣어주고, 그 이름에 해당하는 테이블을 만든 뒤 추가 및 변경사항 입력
* 원본모델(Many-to-Many가 명시된 모델)에 대해 단 하나의 `ForeignKey`필드를 가져야 한다.

```
person = models.ForeignKey(Person, on_delete=...)
group = models.ForeignKey(Group, on_delete=...)

*** recommender = models.ForeignKey(Person, on_delete=...)

# 이 경우 어떤 Person이 이 클래스를 생성할 때 쓰는지 알 수 없다.
# 이 때 원본모델에 `through_fields`속성을 넣어줌(첫번째 속성:source model, 두번째 속성:target model)
# related_name을 중계모델에 지정
# 중계모델을 직접 생성(create)해야
```

##### Many to Many에서 자기 자신을 속성으로 갖기
> ex)친구 추가기능(서로의(대칭적인) 관계가 생김)

* 각각의 pk값을 가진다.
`symmetrical=False`: 대칭관계를 원하지 않을 때 사용되는 속성


# Many to Many관계에서 자기자신을 참조하면서, 대칭적이지 않고 중계모델을 사용하는 경우(Many to Many self symmetrical=false intermediate)
> 언제 follow했는지 기록, User의 관계(follow, block)
