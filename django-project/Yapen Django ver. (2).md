# Yapen Django ver. (2)

##### 2019/1/22/ 화

오늘은 크롤링을 시작 할 예정

그 전에 어떤식으로 구성을 할지 적어봄

* 먼저 크롤링을 완성한 후 DB에 저장
* 각 지역별로 20개 정도(프로젝트때랑 비슷)
* Pension관련 모델 구상

* location과 sublocation을 입력(object or list)
* <del>location -> sublocation을 중첩 for문으로 순회하며 그 페이지마다 get요청 후 펜션들 크롤링</del>
	* 이 때는 펜션의 이름과 대표 이미지, 각 펜션의 고유번호(ypidx) 크롤링
	* location을 큰 class로 두고 sub_location과 pension이 속하게 모델링

테마도 바로 나오게 할 수 있으면 좋을텐데 테마는 각 펜션의 디테일 페이지에 나와있음 디테일 페이지 크롤링 이후 템플릿에 뿌려주는걸 해야할 듯

##### 오늘 한일

오늘 한일은 별로 없는거 같다. 어떻게 모델링을 해야할지 아직 감이 안잡힌다. 원래 했던 프로젝트랑 다르게 하고 싶어서 고민중인데.. 좀더 생각해봐야겠다.
 
