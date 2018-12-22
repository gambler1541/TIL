## Pillow

> python2에서 쓰이던 PIL이 관리가 중단되고, python3로 넘어오면서 몇몇 개발자들에 의해 다시 만들어짐

## Admin

class Meta 옵션 중

`verbose_name`, `verbose_name_plural`를 지정할 수 있음

`create_user`메서드는 create와 달리 자동으로 password를 해싱해준다.

##### hash tag

`re.compile(r'#(?P<tag>\w+)')`
> 인스타그램의 해시태그를 정규표현식으로 text만 뽑아냄

##### get\_or_create

* 만약 DB에 있다면 그 객체를 가져오고 아니라면 새 객체를 만듬
* defaults 속성을 넣을 수 있음
	* defaults속성은 만들때만 적용

```
obj, created = Person.object.get_or_create(
	first_name = 'john'
	last_name = 'lennon'
	default = {'birthday' : date(1999,10,10)
```

* 만약 first_name이 'john'이고 last_name이 'lennon'있다면 obj 그 데이터를 가져오고, created에 `False`, 생성했다면 `True`

##### comment.tags.`set`(tag_list)

>기존에 어떤 내용이 있던지 지금의 내용으로 덮어버림

##### Post중에서 해당 Post에 속한 Comment가 가진 HashTag들 중 nmae이 '<무언가>'인 Tag가 잇는 Post목록 가져오기

```
Post.object.filter(commnets__tags__name='<무언가>')
# 여러개를 가져오고 싶을 경우
Post.object.filter(commnets__tags__name__in=['',''])
```

`safe`
><span>{{ comment.html | safe }}</span>

* tag escape를 방지
* return re.sub(
            self.TAG_PATTERN,
            r'\<a href="/explore/tags/\g<tag>/">#\g<tag></a>',
            self.content,
        )
* 템플릿에서 위 코드사용 시 태그가 문자열로 나오는걸 방지 해준다.

## Custom User Model
> 기본 사용자 모델을 확장하거나 완전히 대체된 사용자 모델을 사용가능
 
 * User와 연결된 OTO필드를 만들어주면 User가 확장된것 처럼 보임
 
 > ex) User의 프로필 정보등을 새 필드에 저장
 
 * `Abstractuser`를 상속받아 사용
 * project 시작시 members모델을 만들고 시작
 
 
 * 사용자 모델 클래스에 대한 참조가 필요할 때
 	* `get_user_model()`함수 사용
 * 사용자 모델 클래스에 대한 관게를 설정할 때
 	* ex)관계필드(ForignKey,MTM,OTO)등의 관계부분
 		* `settings.AUTH_USER_MODEL`(문자열 반환)