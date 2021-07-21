## Linux Kernel
### Child Process 생성 
* 컴퓨터를 부팅하면 커널 프로세스가 로드된다. 
* 커널은 터미널이 켜질 때마다 그에 해당은 shell, 즉 child process를 만든다.
* shell = 사용자의 입력을 기다린다. 입력이 들어오면 그에 따른 작업을 수행해주는 프로그램이다. 
* mail이라고 입력하면 mail이라는 child proces가 생성된다. 

### Creating a child process 
1. **Allocate(공간을 할당하다)** PCB(Printed Circuit Board, 인쇄회로기판). Copy parent's PCB (inherit environment, share resource). 
2. **Allocate** memory. Copy parent's image (parent/child have same code)   
    * 목적: 프로세스 처리 과정을 간편화하기 위해 복사한다. 
    * memory의 data structure에 가서 빈 메모리 공간을 찾아 공간을 지정해준다. 
    * 지정된 공간에 Parent Process의 image을 복사해준다. 
3. Load new image from disk. 
4. Link child PCB to ready list(=queue). 
    * (아직까지 CPU는 Parent Processrk 사용중이다.)
* => two seperate system calls 
    * fork() - step 1 & step 2 
    * exec() - step 3 & step 4 

### Fork 
* fork은 한 번 호출하면 두번 리턴한다. 
    * 이때 child process가 parent process의 PCB를 복사해서 사용했기 때문에 프로그램 진행 상황이 완전히 똑같은 상태를 가지게 된다. 
    * 따라서, fork 가 parent process와 child process로 두 번 리턴하게 된다. 
    * 단 운영체제가 return 값을 다르게 해준다.
        * ```pid = fork()``` : pid = 유닉스 시스템에서 프로세스에게 할당하는 고유 식별 값이다. 
        * child : pid = 0 리턴 
        * parent : pid = 1 리턴 
