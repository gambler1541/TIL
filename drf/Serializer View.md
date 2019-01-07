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
	* 