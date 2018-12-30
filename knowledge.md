# 운영체제(Operating System)
## 1. 일반적인 프로세스 생성 과정(General process creation process)
1. 운영체제가 실행 가능한 파일(exe)의 코드를 Memory Context의 한 부분인 code segment로 exe 파일의 코드들을 읽어 들인다.
2. exe 파일의 전역 변수 및 static 변수를 data segment에 할당한다.
   > -> 프로그램 로드 과정 (program load process)
3. 힙(Heap)과 스택(Stack)은 초기 메모리 주소만 초기화한다.
4. 프로세스 정보를 포함한 PCB(Process Control Block)를 malloc하여 필요한 정보를 기록한다.
5. PCB(Process Control Block)를 Ready Queue에 삽입하고 CPU 할당을 대기한다.
* UNIX 계열 프로세스는 최초 프로세스 외에 나머지 프로세스는 fork() system call을 통해 생성한다.

> 참고 : http://yimoyimo.tk/OS-Process-Creation-and-Termination/
<hr>

## 2.프로세스와 쓰레드의 차이(Difference between process and thread)
### 프로세스(Process)
> "컴퓨터에서 연속적으로 실행되고 있는 컴퓨터 프로그램"

1. 프로세스는 각각 독립된 메모리 영역(Code, Data, Stack, Heap의 구조)을 할당받는다. 
2. 기본적으로 프로세스당 최소 1개의 스레드(메인 스레드)를 가지고 있다.
3. 각 프로세스는 별도의 주소 공간에서 실행되며, 한 프로세스는 다른 프로세스의 변수나 자료구조에 접근할 수 없다.
4. 한 프로세스가 다른 프로세스의 자원에 접근하려면 프로세스 간의 통신(IPC, inter-process communication)을 사용해야 한다.

    Ex) 파이프, 파일, 소켓 등을 이용한 통신 방법 이용

### 스레드(thread)
> 스레드(thread)는 어떠한 프로그램 내에서, 특히 프로세스 내에서 실행되는 흐름의 단위를 말한다.

1. 스레드는 프로세스 내에서 각각 Stack만 따로 할당받고 Code, Data, Heap 영역은 공유한다.
2. 스레드는 한 프로세스 내에서 동작되는 여러 실행의 흐름으로, 프로세스 내의 주소 공간이나 자원들(힙 공간 등)을 같은 프로세스 내에 스레드끼리 공유하면서 실행된다.
3. 같은 프로세스 안에 있는 여러 스레드들은 같은 힙 공간을 공유한다. 반면에 프로세스는 다른 프로세스의 메모리에 직접 접근할 수 없다.
4. 각각의 스레드는 별도의 레지스터와 스택을 갖고 있지만, 힙 메모리는 서로 읽고 쓸 수 있다.
5. 한 스레드가 프로세스 자원을 변경하면, 다른 이웃 스레드(sibling thread)도 그 변경 결과를 즉시 볼 수 있다.

>참고 : https://gmlwjd9405.github.io/2018/09/14/process-vs-thread.html

### 요약(Summary)
<hr>

* **프로세스** : 실행중인 프로그램으로 문맥교환(Context switching) 일어난다. 문맥 교환시 가상 주소 공간의 교환을 요구하기 때문에 page table교환, 캐시, TLB miss, process warm-up 등으로 인한 많은 비용을 초래한다.

* **스레드** : 여러 프로그램들을 시분할 방식으로 서비스하기 위한 것이다. 프로세스의 자원(파일 디스크립터)을 공유하며 page table switch가 이루어지지 않고 가상 주소 공간을 공유하는 경량의 작업(task)이다.
