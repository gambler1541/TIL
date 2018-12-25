### AWS EC2(Ubuntu)에 Nginx와 uWSGI를 이용해 배포

##### locale 설정
서버에서 편집 후 재접속함

```
sudo vi /etc/default/locale

```

```
LC_CTYPE="en_US.UTF-8"
LC_ALL="en_US.UTF-8"
LANG="en_US.UTF-8"

```

ssh 연결 후 기본 설정

```
# 패키지 정보를 업데이트
sudo apt-get update

# 설치되어 있는 패키지들을 의존성 검사하여 업그레이드
sudo apt-get dist-upgrade

# zsh 설치
sudo apt-get install zsh

# oh-my-zsh 설치
sudo curl -L http://install.omyz.sh | sh

# zsh이 설치 된 경로 확인
which zsh

# Default shell 변경
# shell 변경 후엔 exit로 연결을 종료한 후 재연결
sudo chsh ubuntu -s (which zsh경로)
```

* ubuntu에는 python3가 설치되어 있음

```
# pip 설치
sudo apt install python3-pip
```

* 홈 폴더나 루트 폴더에서 프로젝트 폴더 생성 후 
* `pip3 install django`로 django 설치

##### pip로 설치된 path 설정

```
~/.zshrc 
	-> export PATH=$HOME/.local/bin:$PATH 등록 후 저장
```

* 외부요청을 받기 위해 8000번 포트를 보안그룹에 등록(runserver)
	* 외부에서 8000으로 이 컴퓨터에 접속시 접속을 허용
