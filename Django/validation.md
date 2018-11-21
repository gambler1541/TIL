## Validation
> 유효성 검사

일반적으로 처리중인 데이터에 문제가 있으면 ValidationError를 발생시킴

`to_python` : 모든 유효성 검사의 첫 번째 단계, 값을 올바른 데이터 유형으로 강제 변환하고, 가능하지 않은 경우 ValiddationError를 발생 시킴

* Field차원에서 검사함(모델이 아닌 Form)

`clean()` : field에 있는 method, to_python(), validate()및 run\_validators()를 실행하고 오류를 전파, cleand_data에 데이터를 삽입


* validation 과정

```
class Form
	field1 = fomrs.CharField()
	field2 = forms.IntegerField()

form = Form(request.POST)
form.is_valid()

filed1.clean() 호출됨
	field1.to_python()
	field1.validate()
	field1.run_validators()
	return	field1의 value
		-> form.cleaned_data['field1']
		
form.clean_field1<field_name>(self):
	value = self.cleaned_data[field1]
	# username을 받기로 한 field
	if User.objects.filter(value=value).exists():
		raise ValidationError('User name already exists')
	return value
	
field2.clean()
form.clean_field2()

form.clean()
# 전체 Form에 대한 데이터의 유효성 검사
# field A가 제공되면 필드 B는 유요한 전자 메일 주소를 포함해야한다
```

##### Password의 경우 password1이 먼저 cleaned_data에 들어가기 때문에, clean_password2로 유효성 검사를 할 수있다.





