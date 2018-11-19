# Form Class

* `forms.py`를 생성
* 원하는 이름의 form class 생성
* view에서 form객체를 생성 후 
* context에 담아 render
* template에선 `{{ form }}`으로 불러옴

##### Form class 사용 시 bootstarp css를 사용하기 위해 widget속성을 사용


# django의 form
1. HTML위젯 생성
2. 요청(request)으로부터 데이터를 받는 역할
3. 받아온 데이터를 유효성 검증
4. 검증에 실패한 원인을 출력

Form에 데이터를 넣은상태를 bound form이라고 한다.

바운딩된 폼은 `is_vaild`를 사용가능

form에 request.POST의 데이터들이 담겨있기 때문에 input들이 채워져있음

        