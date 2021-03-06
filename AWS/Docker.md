## Docker

>컨테이너 기반의 오픈소스 가상화 플랫폼

* 컨테이너 : 다양한 프로그램, 실행환경을 컨테이너로 추상화하고 동일한 인터페이스를 제공하여 프로그램의 배포 및 관리를 단순하게 해줌
	* 격리된 공간에서 프로세스가 동작하는 기술

* 기존의 가상화 방식 -> `OS`를 가상화
	* VMware, VirtualBox
	* 호스트 OS위에 게스트 OS 전체를 가상화하여 사용하는 방식
	* ex)리눅스에서 윈도우를 돌리는 등
	* 사용법이 간단하지만 무겁고 느림(운영환경에선 사용할 수 없음)

* CPU의 가상화 기술(HVM)
	* KVM(Kernerl-based Virtual Machine)과 반 가상화(Paravirtualization)방식의 Xen등장
	* 게스트 OS가 필요하긴 하지만 전체 OS를 가상화하는 방식은 아님
	* 호스트형 가상화 방식에 비해 성능이 향상
	* ex) OpenAStack, AWS,Racksapce같은 클라우드 서비스에서 가상 컴퓨팅 기술의 기반이 됨

* 전가상화든 반가상화든 추가적인 OS를 설치하여 가상화하는 방법은 성능문제가 있고, 이를 개선하기 위해 `프로세스`를 격리하는 방식이 등장

* 리눅스에서는 이 방식을 리눅스 컨테이너라고 하고 단순히 프로세스를 격리시키기 때문에 가볍고 빠르게 동작

* CPU나 메모리는 딱 프로세스가 필요한 만큼만 추가로 사용하고 성능적으로도 거의 손실이 없음

> 도커의 기본 네트워크 모드는 `Bridge`모드로 약간의 성능 손실이 있다. 네트워크 성능이 중요한 프로그램의 경우 `--net=host`옵션을 고려해야 함

* 하나의 서버에 여러개의 컨테이너를 실행하면 서로 영향을 미치지 않고 독립적으로 실행됨
	* 마치 가벼운 VM을 사용하는 느낌을 줌

* 실행중인 컨테이너에 접속하여 명령어를 입력할수 있고 `apt-get`이나 `yum`으로 패키지를 설치할 수 있으며 사용자도 추가하고 여러개의 프로세스를 백그라운드로 실행할 수도 있음
* CPU나 메모리 사용량을 제한할 수 있고 호스트의 특정 포트와 연결하거나 호스트의 특정 디렉토리를 내부 디렉토리인 것처럼 사용할 수도 있음
* 컨테이너를 만드는데 시간이 얼마 걸리지 않는다.(가상머신과 비교 x)

##### Docker Image

`image` : 컨테이너 실행에 필요한 파일과 설정값등을 포함하고 있는 것

* 컨테이너는 이미지를 실행한 상태라고 볼 수 있고 추가되거나 변하는 값은 컨테이너에 저장
* 같은 이미지라도 여러개의 컨테이너를 생성할 수 있고 컨테이너의 상태가 바뀌거나 컨테이너가 삭제되더라도 이미지는 변하지 않고 그대로 남아있음
* 이미지는 컨테이너를 실행하기 위한 모든 정보를 가지고 있기 때문에 더이상 의존성 파일을 컴파일하고 이것저것 설치할 필요가 없음
* 새로운 서버가 추가되면 미리 만들어 놓은 이미지를 다운받고 컨테이너를 생성만 하면 됨
* 한 서버에 여러개의 컨테이너를 실행할 수 있고, 수십, 수백, 수천대의 서버도 문제없음



