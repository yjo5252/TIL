# 명령어 

### cd 
``` linux
$cd .  // 현재 디렉토리 
$cd .. // 한 단계 상위 디렉토리 
$cd /  // 최상위 디렉토리 
$cd $변수명 // 변수에 저장된 경로 
$cd ~  or $cd $HOME or $cd // 사용자 홈 디렉토리로 이동 
$cd - // 이전 경로로 이동 
$cd ~계정명 // 입력한 사용자의 홈 디렉토리로 이동 
```

### fiel 명령어
지정된 파일의 종류(타입)을 확인하는 명령어이다. file은 /usr/share/file 디렉토리의 magic 파일을 참조하여 파일종류를 표시해준다. 
* 옵션 
   * -C: 매직파일의 포맷을 검사하는 옵션
   * -f 목록파일: 많은 파일들을 한 번에 확인하기 위하여 파일리스트인 목록파일을 만들어서 그 안에 입력된 모든 파일을 한꺼번에 확인하는 옵션
   * -m 매직파일: 지정된 매직파일로 대상파일을 확인하는 것 
```bash
$file index.html
    index.html: UTF-8 Unicode text
```


### ifconfig 명령어 
네트워크 인터페이스를 설정하는 명령어 

* 옵션 
  - up / down : 인터페이스를 활성화/비활성화한다. 
  - netmask 주소: 넷마스크 주소를 설정한다. 
  - broadcast 주소: 브로드캐스트 주소를 설정한다. 
```
$ifconfig  //현재 설치된 네트워크 인터페이스 설정 확인. IP 주소 확인
$ifconfig eth0 inet xxx.xxx.xxx.xxx netmask 255.255.25.0 // IP 주소 변경. 
service network restart //임시적으로변경한IP 주소를 원래대로 돌린다. 
ifconfig lo down  // 인터페이스 비활성화 
ifconfig lo up  // 인터페이스 활성화 
service network stop // 네트워크에 연결된 모든 인터페이스가 비활성화 
service network start // 네트워크에 연결된 모든 인터페이스가 활성화


```

### type
type은 지정된 명령어가 쉘에 내장된 명령어인지, 외부명령어인지, 앨리어스 명령어인지 등을 확인하는 명령어이다.
``` bash 
type cp 

  cp is aliased to `cp -i'
```
