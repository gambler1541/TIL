# Serializer View

```
def snippet_list(request):
    if request.method == 'GET':
        snippet = Snippets.objects.all()
        serializer = SnippetSerializer(snippet, many=True)
        return JsonRespo
```

* Postman 설치
* 클라이언트에게 request요청을 보내듯 할 수 있음
* `JsonResponse`에 serializer.data를 인수로 넣음
	* safe = False
	* 딕셔너리가 아니여도 인수로 넣을 수 있게함
* 따로 Template이 필요없음
* `@csrf_exempt` : CSRF검증에서 제외

### detail
> detail과 list를 나눈 이유는 pk값이 필요하냐 안하냐로 나뉘기 때문
 
`GET` : 객체 한개를 가져옴

`PUT` : 객체 한개를 업데이트

`DELETE`: 객체 하나를 삭제

* status를 따로 지정하지 않으면 무조건 `200`

* `.validate_<field_name>`으로 유효성 검사를 한다.
	* djnago `.clean_<field_name>`과 같음 
* `PUT` -> 전체를 수정할 때, required필드가 반드시 들어감
* `PATCH` -> required필드와 상관없이 일부만 수정
	* serializer에 `partial=True`옵션을 줌

* `GET, POST, PUT, PATCH, DELETE`의 5개 요청을 사용
