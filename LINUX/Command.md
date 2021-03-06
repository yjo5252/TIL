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
### cmp
몇 행의 몇 번째 문자가 다른가를 확인한다. 두 파일이 동일한가를 확인한다. 
```
cmp file1 file2
    
    file1 file2 differ: byte 7, line 1 ! 첫번째행에 7바이트째부터 다름이 발생한다. 
```

### comm
지정한 두 파일의 행과 행을 비교할 때에 사용하는 명령어 
* 옵션
    * -1: 두 파일을 비교하여 첫번째 파일과 두 번째 파일의 내용과 공통내용만을 출력
    * -2: 두번째 파일과 다른 부분의 첫번째 파일내용과 공통내용을 출력 
    * -3: 두 파일의 공통된 파일은 출력하지 않음 
```
comm file1 file2 

      girls Generation
girls generation
                uzuro.com
uzzuzzu
```

### diff
실행결과 차이점이 없다면 0, 차이점이 있다면 1, 실행 시 에러가 발생하면 2 이상의 종료카드 값을 얻는다. 
* 옵션
   - --brief: 단순히 같은가 다른가를 확인 
   - -c: 지정된 포맷으로 두 파일의 차이점을 출력 
   - -d: 가장 작은 변화된 부분까지도 찾기 위해 알고리즘 변경 
```
diff file1 fiel2

  1c1 
  < girls generation 
  ---
  > girls Generation 
```

### diff3
3개의 파일차이점을 비교하여 출력하는 명령어이다. 
* 옵션
  - --text : 비교할 파일이 바이너리 파일인 경우 가능한 텍스트 포맷을 찾아서 비교작업을 수행한다. 
```java
diff3 file1 file2 file3
1:1c 
  girls generation
  
2:1c
  girls Generation 
  
3:1c
  girls geNeration
```

### fil 명령어
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
### tar (Tape ARchive)
- 여러 파일을 묶어서 하나로 만드는 기능 
- 압축은 하지 않음. (compress나 gzip과 같이 사용 가능) 
    - c: create
    - x: extract (풀어줌)
    - t: list (묶인 파일 내에 어떠한 파일들이 들어가는 지 보여줌)
    - v: verbose (긴 출력 정보 제공)
    - f: 파일 이름
``` linux
$ ls
foo.txt bar.txt
$ tar cvf files.tar foo.txt bar.txt
$ ls
foo.txt bar.txt fiels.tar
$ tar xvf files.tar
$ ls
foo.txt bar.txt
```

### type
type은 지정된 명령어가 쉘에 내장된 명령어인지, 외부명령어인지, 앨리어스 명령어인지 등을 확인하는 명령어이다.
``` bash 
type cp 

  cp is aliased to `cp -i'
```

### (un)compress / gzip 
* compress: 확장자 .Z로 파일을 압축 
```
$ compress keynote
$ ls
keynote.Z
```
* uncompress
```
$ uncompress keynote.Z
```
* zcat
```
$ zcat turkey.Z
```
* zmore
```
$ zmore turkey.Z
```
* gazip (GNU zip) : 표준 compress보다 압축률이 좋음
```
$ gzip foo.txt
$ gzip -d foo.txt.gz
```

### w (who)
* Usage: w [options] [user name]
    * 현재 시스템을 사용중인 사용자들에 대한 정보를 출력한다. 
    

### grep pattern 

### find -option file -comand
```
$ find . -name rdstat -print 
./stat/rdstat
```
query :  rdstat라는 이름의 파일의 절대 경로를 출력한다
result : 현재 dir 아래 "어느 subdir" 아래에 있다. 

```
$ find -mtime +30 -ok rm  {}\; 
```
30일보다 이전에 수정했던 파일들 찾아서 yes 하면 삭제 
