# ForeignKey(Many-to-One)
> `ForeignKey` field의 이름은 해당 모델의 lowercase

다 대일(Many to One)관계를 정의하기 위해선 ForeignKey를 사용한다.


* recursive relation ship(재귀 관계)

```
class User(models.Model):
  name = models.CharField(max_length=50)
  instructor = models.ForeignKey(
    'self',
    on_delete=models.SET_NULL,
    blank=True,
    null=True,
    )

# 'self'라는 문자열을 가지면 자기자신을 참조
# SET_NULL = instructor가 삭제되면 instructor를 NULL값으로 바꿈
# on_delete의 다른옵션
- PROTECT : 지우는걸 막음
- SET_DEFAULT : 삭제되면 default값으로(반드시 있을것이라 생각) -> 미리 검사하는 과정이 필요
- SET : 함수를 지정(동작을 다르게 행동)
- DO_NOTHING : 아무것도 하지않음(Database에서 오류발생)

```

* `related_name` : 역참조할 때 그 관계에 대한 이름(default=`model-name_set`)
* 아직 정의되지 않은 모델에 관계를 작성해야 할 경우 모델오브젝트가아닌 모델명(문자열)으로 사용한다.
* `related_query_name` : 역참조할 때 필터링을 할 수있음(default=`related_name`)
