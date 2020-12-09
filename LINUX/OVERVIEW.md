# 요약 

### 명령어 [ a-z 순 ] 

#### * 디스크 사용량 (쿼터; quota) 설정 관련 명령어 
: quotacheck, quotaon, edquota, edquota -p <u1> <u2>, quota, repquota (정보 요약 출력)

### 사용자의 명령이 쉘을 통해 실행 관련 명령어 
: Terminal -> Device Driver -> Shell -> Linux Kernel 

#### * 쉘 
: sh, csh, Tcsh, bash

#### * 특정 디렉터리 & 파일 

### 파일 속성 
: /etc/profile, /usr/local, /etc/shells, ~/.bashrc

### 명령어 chmod 옵션 
: -R  , -c, -f

#### * 명령어 unmask 
* 파일 최대 접근권한 666 / 디렉터리 최대 접근권한 777
* 리눅스 기본 unmask 값은 022, 002

#### * 특수 접근 권한 
: SetUID, SetGID, 스티키 비트 

#### * 명령어 df 옵션 
: -df, -a, -h, -t < 파일시스템 종류> , -T

#### * 명령어 du 
: du, -D, -l, -h, -s 

### * /etc/fstab 파일 
: 필드 6종류 

### 명령어 fsck 옵션
: -a, -r, -v, -s 

### 명령어 mount 
: 디스크의 파티션 생성, 파티션의 파일시스템 생성 , 파일시스템의 무결성 오류 점검
-t (파일시스템 종류 지정), -o (마운트 옵션 지정), -a (/etc/fstab 에 명시된 파일 시스템 마운트) 


### 리눅스에서 최초로 프로세스가 실행될 때 /etc/inittab 파일을 호출하는 프로세스 : init

### Bash 쉘이 자체적으로 처리하는 내부 명령이 아닌 것 : ls / cat / 

#### * 환경변수 
: export, export <쉘 변수>, export -n <환경변수> <값>, export <환경변수>=$<환경변수>: 값 추가> 


#### * 환경변수 종류 


#### * 명령어 ps **
: 옵션 -a, -e, -f, -u, -l, -a 
: 항목 TIME, RSS, VSZ, %MEM

#### * 명령어 top 옵션 
: 옵션 없으면 5초에 한번 새로운 내용으로 갱신하여 출력한다. 
: 메모리 , CPU, 부하 상태 확인 (디스크 사용량 X) 

: 옵션 d, -u <user>, -p <PID num>, -o <출력할 항목>
: 명령 실행 후 사용할 수 있는 옵션 (대소문자 구분) l , P, M, T, s/d, c, m

### 명령어 pstree 옵션 
: -h, -a, -n, -p 

### 명령어 kill 시그널 
: 시그널 (signal) : 프로세스 간의 통신수단 

:  SIGHUP, SIGINT, SIGQUIT, SIGKILL, SIGTERM, SIGTSTP

#### * 프로세스 우선순위 
: NI 값이 낮을수록 우선순위가 높다. (-20 ~ 19)

#### * standalone 타입의 데몬 
: 시스템에 독자적으로 프로세스가 구동되어 서비스를 제공하는 데몬을 말한다. 
: 메모리상에 항상 구동되어야하기 때문에 자주 호출되는 서비스 (데몬)는 standalone 타입의 데몬으로 사용하기에 적당하다. 

#### * 특수문자 
- 명령과 명령 사이에 위치 
 ; || &&

- 명령의 끝에 위치 
& 

- 명령어 
!<history Num> ex) !-1 !50 
!<명령어> 
!! 
  
#### * 명령어 crontab 
- 분, 시, 일, 월, 요일, 작업내용 

- 옵션: -l, -e, -r 

### 소스파일 설치 단계 
: configure -> make -> make install 


#### * vi 에디터 
- Ex 모드 (콜론모드) <= ESC 누르고 : (콜론)을 입력한 ㅏㅇ태 
:!<명령어> 
:%ㅇ 

- vi 에디터에서 파일을 편집 중 비정상 종료가 되었을 때 생기는 파일 

- 환경설정 적용방법 (영구 적용) 
: 사용자 홈 디렉터리에 .exrc 파일에 저장 
: 환경변수 <u>EXINIT</u> 에 지정 
-c, -R, +<NUM>
  
 - 바꾸기 
 :s/문자열1/문자열2/
 :<범위>s/문자열1/문자열2/
 :<범위>s/문자열1/문자열2/g
 
 - 복사/잘라내기/붙여넣기 
 : yy, dd, D, p, J
 
 - 검색하기 
 : /문자열, ?문자열, /, ?, n, N
 
 - 이동 단축키 
 : Ctrl +U, Ctrl +D, Ctrl +B, Ctrl +F, h, j, k, l, hjkl, w, b, G, 
 
 #### * pico 에디터 (nano)
 Ctrl + A, Ctrl + E, Ctrl + P, Ctrl  + N, Ctrl + Y, Ctrl + V, Ctrl + K, Ctrl + U, Ctrl + O, Ctrl + X
 
 
 #### * emicas 에디터 
 - 리처드 스톨만이 만든 에디터, GPL 
 - 입력모드, 명령모드가 없다.
Ctrl + A, Ctrl + E, Ctrl + P, Ctrl  + N, Alt +V, Ctrl + V, Ctrl + K, Ctrl + Y, Ctrl + X + S Ctrl + S + C
 
  
#### * 패키지 설치 
* yum 
- 로그 파일 위치 : /var/log/yum.log 
- Fedora 또는 CentOS에서 사용가능 (Redhat 계열 0) 
: -y, info, list, install, update, remove, groupinstall, grouplist

* rpm
- rpm 패키지 구조 : pkg 이름 pkg버전 pkg릴리즈 아키텍처 확장자 
: -i, -U, -e, -qa, -qd, -V, --test

* 검증 옵션 
S, M, L, U, G

* apt-get 
: 데비안에서 제공되는 명령행 기반의 유틸리티 
- 의존성 및 추동성을 해결하기 위해 관련 정보를 기록하는 파일 : /etc/apt/sources.list
- --purge, clean 

* dpkg 
: -r 패키지 삭제 









