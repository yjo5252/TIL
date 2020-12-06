# Shell 
* 로그인 시 자동 실행된다. 

* Shell 이란? 
  * Shell 프롬프트 한 줄 입력: 명령어 실행기 (command line interpreter) 
  * File 에 command를 입력 & 실행권한 준다: 프로그래밍 언어 (job control language)  
  * 프로그램 작성: 운영체제 커널과 사용자를 연결시켜주는 매개체
  * 입력값 받음: 일종의 user level 프로그램 
  
* Shell의 command 처리 
  1. 키보드 또는 파일로부터 입력을 받아들인다. 
  1. 입력문을 명령어와 연산자 등의 token으로 분리한다. 
    (Alias 가 있을 경우 토큰으로 분리할 때 변환된다)
  1. 분리된 token 들을 단순 또는 복합 명령어로 변환한다. 
  1. Shell 확장법에 따라 token을 확장한 후, command 이름, file name, argument 등으로 구분한다. 
  1. I/O direction 을 수행한 후, argument로부터 I/O redirection 연산자를 제거한다. 
  1. command를 수행한다. 
  (Searches files in PATH variable PATH=/bin:/usr/bin:.:
  If a file matches command name, load the file, and run it as a child. 
  1. Child 의 종료를 기다린 후, wake up 하여 프롬프트를 띄운다. 
  
* 내부 명령어 (Shell Built-in Command)
  * Shell이 별도의 실행파일을  실행시키지 않고 자체적으로 수행하는 명령어  
  * 환경을 변경시키는 명령어는 모두 내부 명령어이다. 
    (예) set, cd, history 
    - set: 현재 수행중인 shell의 변수 표시 
    - history: 과거의 command 입력을 Shell 이 기억한다. 
        * history 단어 지정자 (0 ^ ... n $)
        * history 확장 : !!, !n , !-n, !string
    - set : 
