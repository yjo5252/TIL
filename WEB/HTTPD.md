# HTTPD 설치와 웹 게시 

- HTTPD 프로그램 알아봄  & AWS EC2 서버에 HTTPD 데몬 설치하기 
- /var/www/html 디렉토리 접근권한 설정 변경
- html 문서를 웹 서버에 게시  

## A. HTTPD 프로그램 (for webserver)
- HTTPD (Hypertext transfer protocol daemon)
- HTTPD 서비스 제공하는 데몬서버 
  - 포트: 80 (SSH protocol은 22 번 포트 사용) 
  - 서버 패키지 : apache
  - 서버에서 웹 페이지 전송 서비스를 제공해주는 서버 프로그램 
- EC2 인스턴스 vs HTTPD 
  - EC2 인스턴스 = 물리적 서버 컴퓨터 
  - HTTPD = 서버 컴퓨터에서 웹 서비스 제공을 위해 동작하는 서버 프로그램 
### 1) putty 프로그램으로 SSH 프로토콜을 사용하여 로그인을 합니다. 
### 2) 명령 프롬프트에서 Yum 패키지 최신 버전으로 업데이트합니다. 
```
$ sudo yum update 
```
- sudo: 유닉스 계열 os에서 super 권한 유저로서 명령어 실행한다는 뜻 
- yum (Yellowdog Updater Modified) 
  - RPM(Read Hat Package Manage) 기반의 시스템을 위한 자동 업데이트 
  - 패키지 설치 / 제거 도구 
  - 온라인에서 업데이트 된 패키지들을 검사하고 다운로드하여 설치까지 처리해주는 프로그램이다. 
  - Yum 패키지를 최신으로 업데이트 한다. 
  - 업데이트 완료되면 Complete! 가 뜬다.

### 3) HTTPD 설치 (yum 프로그램을 이용하여 httpd를 설치한다)
```
$ sudo yum install httpd 
```
- 설치가 완료되면 Complete! 가 뜬다.
- 설치 완료 시 /var/www/디렉토리 생성 
  - /var/www/html 디렉토리가 웹 루트 디렉토리임
  - Html 디렉토리 안에 웹에 게시할 html 문서를 첨부함 
```
$ pwd (present working directory) → /home/ec2-user
$ cd /var/www 
```
### 4) 접근 권한 문제 (var/www/html 폴더 권한을 ec2-user에게 허용하는 설정)
- Httpd 초기 설치 시 사용자에게 /var/www 디렉토리의 수정 권한이 없음
```
$ls -l /var/www  (root ⇒ 관리자만 수정권한을 갖고 루트가 /var/www를 소유함을 보여준다.)
```
- /var/www/html 디렉토리 수정 권한 설정이 필요함 
```
$ sudo groupadd www (www 을 그룹에 추가시키는 명령어)
$ sudo usermod -a -G www ec2-user (사용자 ec2-user을 www 그룹에 포함시키는 명령어)
$ exit (putty 종료)
```
-- 다시 putty 로그인한다 --
```
$ groups  →  ec2-user ,  www (www 그룹과 ec2-user 가 있는지 확인)
```
-- ec2-user에게 root가 가진 디렉토리와 파일의 수정&접근 권한을 허락하는 명령 실행. 단, 명령어 사이에 띄어쓰기는 한칸 씩 & 대소문자 정확히 구분
```
$ sudo chown -R root: www/var/www
$ sudo chown -R ec2-user: apache /var/www
$ sudo chmod 2775 /var/www
            $ find /var/www -type d -exec sudo chmod 2775 {} \;
$ find /var/www -type f -exec sudo chmod 0664 {} \;
```

### 5) 웹 서버 인스턴스 포트 설정 
- httpd 80 번 포트 접속을 허용해준다. 
### 6) httpd 서버 프로그램을 실행
- httpd 서버 프로그램 = httpd 서비스 
  - 한 번 실행하면 파일 수정되어도 자동으로 반영된다. 
```
$ sudo service httpd start  ⇒ 실행상태가 [ ok ] 인지 확인한다. 
```
- 본인 호스트의 서버 IP 주소 입력 
   - 화면이 뜨면 정상적으로 작동했음을 의미.

## B. 브라우저로 웹 서버 게시 
- index.html 
  - 홈페이지
  - 브라우저 게시 기본 파일 
  -  /var/www/html 폴더 아래에 index.html 업로드해야 웹에 게시됨
