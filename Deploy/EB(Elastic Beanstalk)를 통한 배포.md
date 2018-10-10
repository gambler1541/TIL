# EB(Elastic Beanstalk)를 통한 배포

1. 초기 셋팅
	* Django project 폴더 생성
	* git ignore및 git 저장소
	* .secret폴더에 json파일로 정보저장

2. AWS
	* IAM USER 생성
	* 사용자 추가 -> 사용자 이름, 액세스 유형(프로그래밍 방식 엑세스) -> 기존 정책에 직접 연결(AWSElasticBeanstalkFullAccess) -> 액세스 키 ID, 비밀 액세스 키를 .aws/credential/에 입력 

3. Docker file 생성
	
4. CLI 

 -> `pipenv install awsebcli --dev`
 -> 