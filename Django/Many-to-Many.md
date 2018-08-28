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
