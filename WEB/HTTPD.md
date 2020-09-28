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


