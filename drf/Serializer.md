# Serializer

```
pipenv install djangorestframework
pipenv install pygments
```

* 웹 API를 만드려면 클래  스의 인스턴스를 `json`같은 형태로 직렬화(serializeing)하거나 반직렬화(deserializeing)할 수 있어야 한다.
* Django의 폼과 같은 역할을 함
* create, update method를 정의
	* 역직렬화(deserializeing)할때 쓰임
	* json -> python 객체

`BytesIO` : 메모리에 있는 데이터를 대상으로 읽기, 쓰기등을 수행
* 쿼리셋도 직렬화 가능
	* many=True 옵션을 줘야함

```
serializer = SnippetsSerializer(Snippets.objects.all(), many=True) 

serializer.data                                                                                                                                    

>>> [OrderedDict([('pk', 1), ('title', ''), ('code', 'foo = "bar"\n'), ('linenos', False), ('language', 'python'), ('style', 'friendly')]), OrderedDict([('pk', 2), ('title', ''), ('code', 'print "hello, world"\n'), ('linenos', False), ('language', 'python'), ('style', 'friendly')]), OrderedDict([('pk', 3), ('title', ''), ('code', 'foo = "bar"'), ('linenos', False), ('language', 'python'), ('style', 'friendly')])]

 
```

## Serializer없이 변환
* django object를 파이썬의 딕셔너리로 변환
	* `model_to_dict(object)`

```python
with open('s1.txt', 'wt') as f:
	json.dump(model)_to_dict(s1), f)
	
data = open('s1.txt', 'rt').read()

```

* data의 결과는 json형태의 문자열
* json.loads(data)로 파이썬의 딕셔너리로 변환가능
