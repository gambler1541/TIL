# FileField와 Storage

`Storage` : 파일의 저장,검색등을 중간에서 처리

```
FileField
	접근
		FieldFile(ImageFieldFile)인스턴스를 얻을 수 있음
		
class Post
	file = FileField()

p = Post.objects.first()
p.file
>>> Feildfile이 출력
```

```
파일 저장
(기본설정)
	-> MEDIA_ROOT에 지정된 폴더
	파일 저장을 위한 Storage로
	FileSystemStorage를 사용
	-> 파일이 현재 Django프로젝트가 존재하는 파일시스템에 저장 (local)

	Storage가 가진 기능
		- 파일 읽기
		- 파일 쓰기

FileField -> 파일 업로드 요청 -> 
(시스템의 어떤 부분에 저장) -> 해당 경로를 DB에 기록
-> FileSystemStorage.write(<파일내용>, <파일이름>)
   open(MEDIA_ROOT, <파일이름>, 'wb').write(<파일내용>)
	(Dropbox의 어떤 부분에 저장)
-> DropboxStorage.write(<파일내용>, <파일이름>)
	Dropbox가 제공하는 기능을 사용해서 파일을 특정위치에 업로드
-> 읽을때
	Dropbox가 제공하는 기능을 사용해서 파일을 가져오고, 데이터(이진데이터)를 파이썬상에서 사용할 수 있	도록 파일객체로 인스턴스화
	
FileField(storage옵션 설정) 
-> FieldFile(실제 파일에 대한 Proxy)를 얻음
-> FieldFile객체는 자신에게 지정된 storage가 가지고 있는
	write, read등의 메서드를 사용할 수 있음
```

```
`.url`속성
	FileSystemStorage
		URL: settings.MEDIA_URL/<파일 경로>
	DropboxStorage
		URL: <이 스토리지에 정의된 Dropbox서비스에서 자동으로 생성해줄 Base URL>/<파일의 경로>
```


# !!! 우리가 FileField에서 쓰는 URL은 기본적으로 Storage에 저장된 절대경로
