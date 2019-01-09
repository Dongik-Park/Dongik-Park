# Java Platform(Java Stand-alone Edition, J2SE)

### **정의 (Concept)**

> 데스크톱 및 서버, 최근의 고사양 임베디드 시스템을 위한 표준 자바 플랫폼으로 표준적인 컴퓨팅 환경을 지원하기 위한 자바 가상 머신 규격 및 API 집합을 포함하고 J2EE와 J2ME에 포함된다. (Reference :  [**J2SE**](https://en.wikipedia.org/wiki/Java_Platform,_Standard_Edition))

### **자바 특징 (Java Characteristic)**
<hr>

#### 1. 플랫폼에 독립적 (Platform independent)
자바로 작성된 응용프로그램은 [**JVM(Java Virtual Machine, 자바 가상머신)**](https://en.wikipedia.org/wiki/Java_virtual_machine) 위에서 실행된다. 따라서, 서로 다른 실행 환경을 가진 시스템 간에 프로그램을 옮겨서 실행할 수 있다. 자바 언어로 개발된 프로그램은 소스 파일을 수정하지 않아도, 자바 실행 환경(JRE)이 설치되어 있는 모든 운영 체제에서 실행 가능하다. 작성된 자바 코드의 컴파일 및 실행 과정은 다음과 같다.
    
                                Compile(javac HelloWorld.java)      Execution(java HelloWorld)
                                        |                              |    
                +-----------------+     |     +------------------+     |     +------------------------+
                | HelloWorld.java | --------> | HelloWorld.class | --------> | JVM executes on any OS |
                +-----------------+           +------------------+           +------------------------+
                                                       |
                                                       |
                                                   byte code(JVM이 실행하는 명령어)
    
자바 컴파일러는 자바 언어로 작성된 코드를 JVM이 인식 가능한 코드인 byte code로 번역한다. 이때, 컴파일러는 문법 체크 및 생략된 부분의 코드를 삽입과 상수연산 등을 수행하고 실행 성능 최적화 작업을 진행한다. JVM은 컴파일된 byte code를 읽어 한 문장씩 OS가 실행 가능한 코드(기계어)로 번역하여 최적화 작업을 함께 실행([**JIT컴파일**](https://ko.wikipedia.org/wiki/JIT_%EC%BB%B4%ED%8C%8C%EC%9D%BC) 방식)한다.

#### 2. 동적 로딩 지원 (Dynamic Loading)

  자바의 경우 애플리케이션이 실행될 때 모든 객체가 생성되지 않고, 각 객체가 필요한 시점에 클래스를 동적 로딩해서 생성한다. 또한 유지보수 시 해당 클래스만 수정하면 되기 때문에 전체 애플리케이션을 다시 컴파일할 필요없기 때문에 유지보수가 쉽고 빠르다.

#### 3. 분산 프로그래밍 지원 (Distributed-programming)

 1990년대에 설계된 언어로 네트워크를 이용한 프로그래밍을 지원하고, 원격 접속을 위한 다양한 기술 집합을 보유하고 있다.

#### 4. 멀티스레드 지원 (Multi-thread)

자바는 스레드 생성 및 제어와 관련된 라이브러리 API를 제공함에 따라 운영체제에 종속적이지 않은 독립적인 설계와 JVM에 의해 스케줄링 되도록 구현되어 있다.


#### 5. 오픈소스 라이브러리 풍부 (Various open source libraries)

자바는 오픈소스 언어이기 때문에 자바 프로그램에서 활용할 수 있는 라이브러리 또는 오픈소스가 많다. 검증된 오픈소스와 라이브러리를 이용하여 개발 시간을 단축할 수 있을 뿐만 아니라 안정성있는 애플리케이션을 개발할 수 있다.

#### 6. 상대적으로 느림 (Relatively slow)

 위에서 보듯 자바는 컴파일 이후 바로 기계어가 아닌 byte code로 번역되고 이후 JVM에 의해 다시 기계어로 번역되고 실행되는 과정을 거치기 때문에 C나 C++ 같이 컴파일 단계에서 만들어지는 완전한 기계어보다 속도가 느리다. 하지만 근래에는 JIT 컴파일러와 같은 기술과 HW 성능 발전으로 인해 JVM의 기능이 향상되어 속도 차이가 감소하였다.

### **실행 환경(Runtime environment)**
<hr>

                  +-------+
                  | .java |   
                  +-------+
                    ↓   
                  +--------+                         +--------------+
                  | .class | ----------------------> | Class Loader |
                  +--------+                         +--------------+               
                                                           ↑ ↓
                                                           ↑ ↓
      +---------------------------------------JVM Memory or Runtime Data Area--------------------------------------+
      |                                                                                                            |
      |       +----------+         +----------+        +----------+        +----------+        +----------+        |
      |       |   Class  |         |          |        |   JVM    |        |          |        |  Native  |        |
      |       | (Method) |         |   Heap   |        | Language |        |    PC    |        |  Method  |        |
      |       |   Area   |         |          |        |  Stacks  |        | Registers|        |  Stacks  |        |
      |       +----------+         +----------+        +----------+        +----------+        +----------+        |
      |                                                                                                            |
      +------------------------------------------------------------------------------------------------------------+
                              ↑ ↓                                         ↑ ↓
                              ↑ ↓                                         ↑ ↓
      +-----------------Execution Engine------------------+     +---------------------+     +----------------------+ 
      |                                                   |     |                     |     |                      |
      |  +-------------+  +-----+  +-------------------+  |  ←  |    Native Method    |  ←  |        Native        | 
      |  | Interpreter |  | JIT |  | Garbage Collector |  |  →  |      Interface      |  →  |       Libraries      | 
      |  +-------------+  +-----+  +-------------------+  |     |                     |     |                      |
      +---------------------------------------------------+     +---------------------+     +----------------------+

#### JVM (Java Virtual Machine)

  자바 바이트코드(byte code)를 실행할 수 있는 주체로 인터프리터(Interpreter)나 JIT 컴파일 방식으로 다른 컴퓨터 위에서 바이트코드를 실행할 수 있도록 구현된다.

  * 스택 기반의 가상 머신(Stack based virtual machine)

  * 단일 상속 형태의 객체 지향 프로그래밍을 가상 머신 수준에서 구현

  * 포인터를 지원하되, C와 같이 주소 값을 임의로 조작이 가능한 포인터 연산이 불가능

  * 가비지 컬렉션(GC)을 활용한 메모리 관리

  * 모든 기본 타입의 정의를 명확히 함으로써 플랫폼 독립성 보장

  * 데이터 흐름 분석(Data flow analysis)에 기반한 자바 바이트코드 검증기(verifier)를 통해 스택 오버플로우(stack-overflow), 명령어 피연산자의 타입 규칙 위반, 필드 접근 규칙 위반, 지역 변수의 초기화 전 사용 등 많은 문제를 실행 전에 검증하여 실행 시 안전을 보장하고 별도의 부담을 줄여줌

> Reference : [Java virtual machine(자바 가상 머신)](https://en.wikipedia.org/wiki/Java_virtual_machine)

#### 클래스 로더 (Class loader)

하드 디스크에 있는 자바 컴파일러에 의해 번역된 class 파일을 메모리로 로딩시킨다. JVM이 실행되면 아래 3개의 클래스 로더들이 사용된다.

* 부트스트랩 클래스 로더(Bootstrap class loader)
* 확장 클래스 로더(Extension class loader)
* 시스템 클래스 로더(System class loader)

부트스트랩 클래스 로더는 <JAVA_HOME>/jre/lib 디렉터리에 위치한 핵심 자바 라이브러리들을 불러들인다. 핵심 JVM의 일부분인 이 클래스 로더는 네이티브 코드로 작성되어 있다.

확장 클래스 로더는 확장 디렉터리(<JAVA_HOME>/jre/lib/ext 또는 java.ext.dirs 시스템 속성에 지정된 기타 디렉터리)에 코드를 로드한다. sun.misc.Launcher$ExtClassLoader 클래스에 의해 구현되어 있다.

java.class.path에서 볼 수 있는 시스템 클래스 로더는 CLASSPATH 환경 변수에 매핑된다. 

> Reference : [Java class loader(자바 클래스로더)](https://en.wikipedia.org/wiki/Java_Classloader)

#### 메모리 구조 (Memory Structure)
      +---------------------------------------JVM Memory or Runtime Data Area--------------------------------------+
      |                                                                                                            |
      |       +----------+         +----------+        +----------+        +----------+        +----------+        |
      |       |   Class  |         |          |        |   JVM    |        |          |        |  Native  |        |
      |       | (Method) |         |   Heap   |        | Language |        |    PC    |        |  Method  |        |
      |       |   Area   |         |          |        |  Stacks  |        | Registers|        |  Stacks  |        |
      |       +----------+         +----------+        +----------+        +----------+        +----------+        |
      |                                                                                                            |
      +------------------------------------------------------------------------------------------------------------+

* **Class(Method) area** : 메모리로 읽어온 클래스의 정보를 기록하는 곳으로 class 정보와 static 정보 등 초기화되는 대상 정보를 저장하고 GC(Garbage Collector)에 의해 관리된다.

* **Heap** : 클래스 객체를 생성하여 저장하는 곳으로 reference 타입의 instance 객체를 저장하고 GC(Garbage Collector)에 의해 관리된다.

* **JVM Stack(Java Stack)** : 메소드 수행 시 프레임(frame)이 할당되어 필요한 지역 변수(local variable), 리턴 값(return value) 등을 임시 기억하는 장소로 메소드 종료 시 할당 메모리가 자동으로 제거 된다.

* **PC Register** : 스레드(thread)가 시작될 때 생성되며 이때마다 생성되는 공간으로 스레드마다 한개씩 존재한다. 스레드가 어떤 부분의 명령어를 실행 해야할지를 기록하는 부분으로 JVM 명령의 주소를 갖는다.

* **Native Method Stack** : 번역된 바이트코드(byte code)가 아닌 실제 실행 가능한 기계어로 작성된 프로그램을 실행시키는 영역으로 자바가 아닌 다른 언어로 작성된 코드를 위한 공간이다. 네이티브 메소드(Native method)를 지원하는 JVM에는 네이티브 메소드 스택이 있어 스레드마다 사용된다. 네이티브 메소드가 JVM에 의해로드 될 수없는 경우 네이티브 메소드 스택을 가질 필요가 없다. 메모리 크기는 고정 또는 동적 같은 일반적인 JVM 스택과 비슷하게 관리되며 JVM은 그에 따라 StackOverflowError 또는 OutOfMemoryError를 발생시킨다.

#### GC (Garbage Collector)
자바 언어는 메모리 관리를 개발자에게 위임하지 않고, GC(Garbage Collector)라는 쓰레드를 생성하여 동적 할당된 메모리 영역 가운데 참조 count가 0인 객체를 제거하도록 설계되었다. GC를 활용하여 예방할 수 있는 버그는 다음과 같다.
* 유효하지 않은 포인터 접근(Dangling pointer bugs) : 이미 해제된 메모리에 접근하는 버그를 막는다. 
* 이중 해제(Double free bugs) : 이미 해제된 메모리를 또다시 해제하는 버그를 가리킨다. 일부 메모리 할당 알고리즘에서는, 해제된 메모리를 다시 해제하려고 시도하는 것은 오류를 일으킬 수 있다.
* 메모리 누수(Certain kinds of memory leaks): 더이상 필요하지 않은 메모리가 해제되지 않고 남아있는 버그를 가리킨다. 메모리 누수가 반복되면 메모리 고갈로 프로그램이 중단될 수 있다. (접근 가능한 메모리가 증가하여 메모리가 고갈되는 문제는 쓰레기 수집으로도 막을 수 없다)

하지만 이를 통해 발생하는 단점은 다음과 같다.
* 어떤 메모리를 해제할지 결정하는 데 비용이 든다.(consuming additional resources) 객체가 필요없어지는 시점을 프로그래머가 미리 알고 있는 경우에도 쓰레기 수집 알고리즘이 메모리 해제 시점을 추적해야 하므로, 이 작업은 오버헤드가 된다.
* 쓰레기 수집이 일어나는 타이밍이나 점유 시간을 미리 예측하기 어렵다.(unpredictable collect time) 때문에 프로그램이 예측 불가능하게 일시적으로 정지할 수 있다. 이런 특성은 특히 실시간 시스템에는 적합하지 않다.
* 할당된 메모리가 해제되는 시점을 알 수 없다.(unpredictable memory free time) 자원 할당과 변수 초기화를 일치하는 RAII(Resource Acquisition is Initialization) 스타일의 프로그래밍에서는, 이것은 자원 해제 시점을 알 수 없다는 것을 의미한다.

> Reference : [Garbage Collector(가비지 콜렉터, 쓰레기 수집가)](https://en.wikipedia.org/wiki/Garbage_collection_(computer_science))

#### JIT 컴파일러 (Just-In-Time, JIT compiler)

#### JDK (Java Development Kit)

#### JRE (Java Runtime Environment)
> JRE  =  JVM ( Interpreter + JIT Compiler + GC )  +  Class Loader  +  Java API


### **설치 (Installation)**
<hr>

### **데이터 타입 (Data type)**
<hr>
    primitive, reference

### **클래스 활용 (Class)**
<hr>
    생성자, 메소드
    접근 제어자를 활용한 캡슐화
    상속과 다형성
    인터페이스 활용

### **API (Application Programming Interface)**
<hr>

### **TRY & CATCH**
<hr>

### **JUnit**
<hr>