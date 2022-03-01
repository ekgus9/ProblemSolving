# AWS에서 flask 웹서버 배포



모든 과정은 <https://velog.io/@jaehyeong/Flask-%EC%9B%B9-%EC%84%9C%EB%B2%84-AWS-EC2%EC%97%90-%EB%B0%B0%ED%8F%AC%ED%95%98%EA%B8%B0>를 참고하였다. 



# AWS 서버 실행

```
cd C:\Users\user\OneDrive\바탕 화면\whdrkd  # keypair.pem가 있는 곳으로 이동
ssh -i "keypair.pem" ubuntu@ec2-3-93-181-166.compute-1.amazonaws.com  # 인스턴스 연결에 있는 ssh 명령어
cd 디렉토리 이름/  # 실행시킬 파일이 있는 폴더로 이동
sudo python3 application.py  # 서버 실행
```

# 리눅스 문법



우분투를 처음 사용해봐서 리눅스 문법이 낯설었다.



- 복사는 ctrl + shift + c, 붙여넣기는 마우스 우측 클릭. (ctrl + shift + v 나 shif + insert 로도 된다는 글을 많이 보았지만 내 경우는 작동하지 않았다.)



- 디렉토리 이동은 윈도우에서 원래쓰던 cd 문법과 동일하다. (이전 디렉토리로 이동 : cd ..)



- 디렉토리 삭제는 다음과 같고, -r을 -rf로 바꾸면 묻지 않고 바로 삭제한다.

```
rm -r <디렉토리 이름>
```

만약 'rm: cannot remove directory/: Permission denied' 의 에러가 떴다면 앞에 'sudo'를 붙이면 강제 삭제된다.



- 디렉토리 정보 보기 : ls



# AWS EC2에서 인스턴스 관리



AWS를 처음 접했을 때는 깃허브의 파일을 인스턴스로 불러와서 쓰는 법을 배웠기 때문에 파일 업로드나 수정과 같은 부분을 모두 깃허브에서 해결하였다. 그러다보니 깃허브에서 계속 커밋을 하는 게 불편하여 우분투 인스턴스를 따로 관리할 수 있는 방법이 있는지 찾아보게 되었다. filezilla를 이용하면 인스턴스 파일을 수정하고 보는 것 뿐만 아니라 로컬 파일을 인스턴스에 업로드하거나 인스턴스 파일을 다운로드할 수도 있다. 



filezilla : <https://filezilla-project.org/>



다운 받았다면 먼저 aws와 연동을 시켜줘야한다. file -> 사이트 관리자 에 들어가서 새 사이트를 만든 뒤 



- 프로토콜 : SFTP
- 호스트 : EC2 인스턴스 퍼블릭 IPv4 DNS
- 포트 : 22
- 로그온 유형 : 키 파일
- 사용자 : EC2 인스턴스 사용자 이름
- 키 파일 : EC2 인스턴스 키파일(.pem)



위 정보를 모두 입력하고 연결 버튼을 누르면 연결이 된다. 메인 창에서 왼쪽은 로컬 디렉토리를, 오른쪽은 우분투 디렉토리를 관리할 수 있게 된다. 



참고 : <https://jow1025.tistory.com/306>



# AWS EC2 우분투에 selenium 설치



```
$ sudo apt-get install python-pip
$ sudo pip install selenium
```

셀레니움은 위 코드로 설치가 된다. 그러나 셀레니움은 크롬을 이용하는 모듈이기 때문에 크롬과 크롬 드라이버를 설치해줘야 한다.



- 크롬 설치 

```
$ wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
$ sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
$ sudo apt-get update
$ sudo apt-get install google-chrome-stable
```

- chromedriver 설치



먼저 크롬의 버전을 확인해야한다.

```
$ google-chrome --version
```

그리고 <https://chromedriver.chromium.org/downloads> 에 들어가 어느 버전을 다운 받아야 할지 확인한다. 아래 코드에서 76.0.3809.68 부분을 자신의 버전으로 바꾸고 코드를 실행시킨다. 

```
$ wget -N http://chromedriver.storage.googleapis.com/76.0.3809.68/chromedriver_linux64.zip -P ~/Downloads
$ unzip ~/Downloads/chromedriver_linux64.zip

$ sudo pip install xlrd
$ sudo apt-get install xvfb
$ sudo pip install pyvirtualdisplay
```

- 정상 설치 확인법

```
$ python

>>> from selenium import webdriver
>>> from pyvirtualdisplay import Display
>>> display = Display(visible=0, size=(1024, 768))
>>> display.start()
>>> path = '/home/ubuntu/Downloads/chromedriver'
>>> browser = webdriver.Chrome(path)
```

참고 : <https://dvpzeekke.tistory.com/1>


