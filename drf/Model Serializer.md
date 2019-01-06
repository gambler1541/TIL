# Model Serializer

```python
class SnippetSerializer(serializers.ModelSerializer):
    class Meta:
        model = Snippets
        fields = (
            'pk',
            'title',
            'code',
            'linenos',
            'language',
            'style',
        )
```

* json.loads는 문자열, load는 파일 객체가 옴
* django model field를 그대로 씀