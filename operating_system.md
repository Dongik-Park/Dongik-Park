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

## 2.프로세스와 스레드의 차이(Difference between process and thread)
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

## 3. 스레드 동기화 방식 (Thread synchrozied mechanism)

Exit/join, Mutex, Reader-writer lock, Condition Variable, Spin lock, Barrier, Semaphore를 활용한다. 세마포어는 Wait(lock연산)와 signal(unlock연산)이 존재한다. 
각 스레드가 lock을 획득할 수 없는 상태에서 lock을 시도하여 영원이 교착되는 현상이 발생한다.

## 4. 프로세스 간 자원 공유 (Sharing resources between processes)
시그널, Local IPC와 Remote IPC, 병행 서버 모델, RPC 등으로 프로세스 간 통신할 수 있다. 
하나의 OS 위에서 수행되는 시그널은 인터럽트를 활용한 통신이고 Local IPC에서 파이프(단방향통신)를 이용한 자원 공유와 공유 메모리(양방향통신)에서 세마포어와 같은 동기화 메커니즘을 통해 자원을 공유할 수 있다. 또한, 안드로이드처럼 서버 process의 호출을 지원하는 API가 내장되어 있는 Remote IPC도 있다.

## 5. 세마포어란? (Counting semaphore)
여러 개의 프로세스가 공유 자원에 동시에 접근할 때, 하나의 프로세스만 한 개의 자원을 점유하도록 제한하는 메커니즘. 동시에 리소스에 접근할 수 있는 '허용 가능한 Counter의 갯수'를 가지고 있다.

## 6. 뮤텍스란? (Mutex,binary semaphore)
한 공유자원을 여러 스레드가 접근하고자 할 때, 임의의 한 순간에 한 스레드만 접근할 수 있도록 제어한다. 즉, 한 개의 스레드만 critical section에 진입하도록 원자적 연산(lock)을 지원하고 다른 스레드들은 unlock할 때까지 대기한다. 자바의 synchronized는 이렇게 동작한다.

우선 뮤텍스, 모니터와 세마포어의 차이는 개념적으로 전자(뮤텍스,모니터)는 상호배제(
Mutual exclusion)를 함으로써 임계구역(critical section)에 하나의 스레드만 들어갈 수 있다는 것이고 후자(세마포어)는 프로세스 카운트를 기준으로 하기 때문에 여러개의 스레드의 진입이 가능하다.

## 7. Monitor 기법
Mutex(Lock)와 Condition Variables(Queue라고도 함)을 가지고 있는 Synchronization 메카니즘이다. 예를 들어 자바에서 모든 객체는 Object 클래스를 상속 받는다. 이 Object 클래스에는 wait(), notifyAll(), notify() 메소드를 가지고 있는데 이게 바로 Condition Variables 역할이라고 보면 된다. 고로 모든 자바 객체는 Monitor를 가지고 있다. 자바에서는 Mutual Exclusion 해결을 위한 구현체로 Synchronized 키워드가 있다. 예를 들어 Synchronized가 메소드에 선언되어있고, 스레드A가 이미 Lock을 획득해서 Critical Section(메소드)을 수행중이라고 가정하자. 스레드B가 동일한 메소드를 수행하기 위해 해당 Object의Lock을 획득해야 할 것이다. 이 Lock이 반환될 때까지 대기를 해야하는데 그 때 사용되는게 바로 Monitor다. 스레드A가 Lock을 반환하면 스레드B는 기다렸다가 Lock을 획득하게 된다. 그리고 Critical Section인 메소드를 수행할 수 있게 된다. 물론 Synchronized 키워드를 사용했을 때 자동적으로 수행되는 내부 동작이고, 별도로 명시적인 Monitor를 구현할 수도 있다.아무튼 Monitor는 이렇게 Mutex(Lock)과 Condition Variables을 이용해서 Mutual Exclustion을 해결하고 있다. 그 외 Monitor의 다른 정의로는 공유자원에 안전하게 접근하기 위해 Mutual Exclusion가 랩핑된 Thread-Safe한 클래스, 객체, 모듈들을 의미하기도 한다.

## 8. 레이스 컨디션은 무엇인가? (What is race condition?)
한정된 자원을 동시에 이용하려는 프로세스 간 경쟁을 벌이는 현상으로 이것을 이용하여 root 권한을 얻는 공격이다. 
프로세스 권한은 SETUID로 Root 권한으로 상승된다. 이 공격을 위해서는 파일 소유자가 root이고 SetUID가 설정된 프로그램이어야 한다. 또 생성되는 임시 파일의 이름을 알고 있어야 한다. 이 때 임시 파일과 동일한 이름으로 심볼릭 링크를 생성하고 원본 파일을 지운다. 이 후 심볼릭 링크를 건 파일과 같은 파일이 생성될 때를 기다렸다가 심볼릭 링크를 이용해 파일내용을 변경한다. 시스템은 변경된 파일이 자신이 생성한 임시파일이라 생각하고 프로세스를 진행하므로 공격자가 관리자 권한을 얻게 된다.

## 9. 정적 할당과 동적 할당의 차이(Ditfference between static and dynamic allocation)

### 정적할당 (Static)
    
정적 메모리 할당은 메모리의 크기가 하드 코딩되어 있기 때문에 **프로그램이 실행 될 때 이미 해당 메모리의 크기가 결정**되는 것이 특징이다.

- 장점: 할당된 메모리 미해제로 인한 메모리 누수와 같은 문제를 신경쓰지 않아도 된다. 정적 할당된 메모리는 실행 도중에 해제되지 않고, 프로그램이 종료할 때 알아서 운영 체제가 회수한다.

- 단점: 메모리의 크기가 하드 코딩되어 있어서 프로그램 실행 중 변경할 수 없다. 스택에 할당된 메모리이므로 동적 할당에 비해 할당 받을 수 있는 최대 메모리에 제약을 받고, 과도하게 사용할 경우 프로그램 실행 시 스택 오버플로우를 야기한다.

### 동적할당 (Dynamic)

동적 메모리 할당은 **프로그램 실행 시간 동안 사용할 메모리 공간을 할당**하는 것을 말한다. 동적으로 할당된 메모리 공간은 프로그래머가 직접 해제하거나 GC(Garbage Collector)가 회수하기 전 까지 유지된다. C/C++와 같이 GC(Garbage Collector)를 지원하지 않는 언어의 경우, 동적 할당하면 프로그래머가 해제하기 전까지는 메모리 공간이 계속 유지된다. 이 메모리 공간은 프로세스 종료 시 운영 체제에 의해 해제되지만 사용 완료한 메모리 공간은 재할당 또는 힙 오버플로우를 막기 위해 즉시 반납하는 것이 유리하다.

- 장점: 실행 시점에 필요한 크기만큼의 메모리를 유동적으로 할당하고 회수할 수 있으므로 경제적이다. GC(Garbage Collector)를 지원하는 언어는 개발자가 메모리 관리로부터 자유로워 진다.

- 단점: 더 이상 사용하지 않을 때 명시적으로 메모리를 해제해 주어야 하고, 이 기능을 지원하는 GC(Garbage Collector)의 경우 메모리 해제 시점을 명확하게 파악할 수 없다.

