# Java Platform(Java Stand-alone Edition, J2SE)

### **정의 (Concept)**

> 데스크톱 및 서버, 최근의 고사양 임베디드 시스템을 위한 표준 자바 플랫폼으로 표준적인 컴퓨팅 환경을 지원하기 위한 자바 가상 머신 규격 및 API 집합을 포함하고 J2EE와 J2ME에 포함된다. (Reference :  [**wiki : J2SE**](https://en.wikipedia.org/wiki/Java_Platform,_Standard_Edition))

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
### **설치 (Installation)**
<hr>

#### Step1 : 다운로드 JDK (Download JDK)

1.  Java SE download site에 접속한다. (http://www.oracle.com/technetwork/java/javase/downloads/index.html).
2. "Java Platform, Standard Edition"의 최신버전을 확인하고 "DOWNLOAD" 버튼을 클릭한다.
3. "Java SE Development Kit 11.0.{x}"의 "Accept License Agreement"을 클릭한다.
4.  현재 컴퓨터의 운영체제에 맞는 JDK를 선택하고 다운로드 한다.

#### Step2 : JDK & JRE 설치 (Install JDK & JRE)

1. 다운로드된 "jdk-11.0.{x}_windows-x64_bin.exe"를 실행하고 설치를 진행한다.
2. 설치가 완료되면 default로 
    * JDK는 "C:\Program Files\Java\jdk-11.0.{x}"에
    * JRE는 "C:\Program Files\Java\jre-11.0.{x}"에 설치된다.
    * 32-bit의 경우 "Program Files" -> "Program Files (x86)"이다.

#### Step3 : 환경 변수 설정 (Include JDK's "bin" directory in the PATH)

1. JDK 설치가 완료되면 명령 프롬포트에서 사용하기 위해 환경 변수에 등록해야 한다.
2. Window의 경우 "시스템 > 고급 시스템 설정" 을 클릭한다.
3. '고급' 탭의 환경변수를 클릭한다.
    * 환경 변수는 사용자 변수와 시스템 변수로 나뉘는데, 사용자 변수에 설정한 경우 윈도우 계정에만 적용되고, 시스템 변수에 설정한 경우 모든 계정에 변수가 지정된다.
4. 시스템 변수의 '새로 만들기'를 클릭한다.
5. 변수 이름은 'JAVA_HOME' 변수 값은 JDK가 설치된 경로를 입력한다. (default : "C:\Program Files\Java\jdk-11.0.{x}")
6. '확인' 버튼을 눌러 변수를 저장한다.
7. 다시 시스템 변수에서 '새로 만들기' 버튼을 클릭하여 변수 이름은 'CLASS_PATH', 변수 값은 '%JAVA_HOME%lib'를 입력하고 '확인'버튼을 눌러 변수를 저장한다.
8. '시스템 변수' 중 'Path'를 선택한 다음 '편집' 버튼을 클릭한다.
9. '환경 변수 편집' 우측의 '새로 만들기' 버튼을 클릭한다.
10. '%JAVA_HOME%\bin'을 입력하고 '확인' 버튼을 클릭하여 변경 내용을 저장한다.

#### Step4 : JDK 설치 확인 (Verify the JDK Installation)

1. 명령 프롬포트를 실행시킨다.
2. "java -version" 을 입력한다.

    ```cmd
    C:\Users\student>java -version
    java version "1.8.0_191"
    Java(TM) SE Runtime Environment (build 1.8.0_191-b12)
    Java HotSpot(TM) 64-Bit Server VM (build 25.191-b12, mixed mode)

    C:\Users\student>_
    ```
3. 위와 같은 형태로 나오면 설치가 완료된다.


### **실행 환경(Runtime environment)**
<hr>

                                                    <JVM Architecture>
                +------------+
                | +-------+  |
                | | .java |  | 
                | +-------+  |
                |     ↓      |
                | +--------+ |                       +--------------+
                | | .class | |---------------------> | Class Loader |
                | +--------+ |                       +--------------+               
                +------------+                             ↑ ↓
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

  자바 바이트코드(byte code)를 실행할 수 있는 주체로 바이트코드 검증기(bytecode verifier)ㄹ,ㄹ 거쳐 인터프리터(Interpreter)와 JIT 컴파일 방식으로 다른 컴퓨터 위에서 바이트코드를 실행할 수 있도록 구현된다.

  * 스택 기반의 가상 머신(Stack based virtual machine)

  * 단일 상속 형태의 객체 지향 프로그래밍을 가상 머신 수준에서 구현

  * 포인터를 지원하되, C와 같이 주소 값을 임의로 조작이 가능한 포인터 연산이 불가능

  * 가비지 컬렉션(GC)을 활용한 메모리 관리

  * 모든 기본 타입의 정의를 명확히 함으로써 플랫폼 독립성 보장

  * 데이터 흐름 분석(Data flow analysis)에 기반한 자바 바이트코드 검증기(verifier)를 통해 스택 오버플로우(stack-overflow), 명령어 피연산자의 타입 규칙 위반, 필드 접근 규칙 위반, 지역 변수의 초기화 전 사용 등 많은 문제를 실행 전에 검증하여 실행 시 안전을 보장하고 별도의 부담을 줄여줌

> Reference : [wiki : Java virtual machine(자바 가상 머신)](https://en.wikipedia.org/wiki/Java_virtual_machine)

#### 클래스 로더 (Class loader)

하드 디스크에 있는 자바 컴파일러에 의해 번역된 class 파일을 메모리로 로딩(loading)시킨다. JVM이 실행되면 아래 3개의 클래스 로더들이 사용된다.

* 부트스트랩 클래스 로더(Bootstrap class loader)
* 확장 클래스 로더(Extension class loader)
* 시스템 클래스 로더(System class loader)

부트스트랩 클래스 로더는 <JAVA_HOME>/jre/lib 디렉터리에 위치한 핵심 자바 라이브러리들을 불러들인다. 핵심 JVM의 일부분인 이 클래스 로더는 네이티브 코드로 작성되어 있다.

확장 클래스 로더는 확장 디렉터리(<JAVA_HOME>/jre/lib/ext 또는 java.ext.dirs 시스템 속성에 지정된 기타 디렉터리)에 코드를 로드한다. sun.misc.Launcher$ExtClassLoader 클래스에 의해 구현되어 있다.

java.class.path에서 볼 수 있는 시스템 클래스 로더는 CLASSPATH 환경 변수에 매핑된다. 

> Reference : [wiki : Java class loader(자바 클래스로더)](https://en.wikipedia.org/wiki/Java_Classloader)

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

자바 언어는 메모리 관리를 개발자에게 위임하지 않고, GC(Garbage Collector)라는 쓰레드를 생성하여 동적 할당된 메모리 영역 가운데 유효한 참조가 없는(Unreachable) 객체를 제거(free)하도록 설계되었다. GC를 활용하여 예방(prevent)할 수 있는 버그는 다음과 같다.
* 유효하지 않은 포인터 접근(Dangling pointer bugs) : 이미 해제된 메모리에 접근하는 버그를 막는다. 
* 이중 해제(Double free bugs) : 이미 해제된 메모리를 또다시 해제하는 버그를 가리킨다. 일부 메모리 할당 알고리즘에서는, 해제된 메모리를 다시 해제하려고 시도하는 것은 오류를 일으킬 수 있다.
* 메모리 누수(Certain kinds of memory leaks): 더이상 필요하지 않은 메모리가 해제되지 않고 남아있는 버그를 가리킨다. 메모리 누수가 반복되면 메모리 고갈로 프로그램이 중단될 수 있다. (접근 가능한 메모리가 증가하여 메모리가 고갈되는 문제는 쓰레기 수집으로도 막을 수 없다)

하지만 이를 통해 발생하는 단점(disadvangtage)은 다음과 같다.
* 어떤 메모리를 해제할지 결정하는 데 비용이 든다.(consuming additional resources) 객체가 필요없어지는 시점을 프로그래머가 미리 알고 있는 경우에도 쓰레기 수집 알고리즘이 메모리 해제 시점을 추적해야 하므로, 이 작업은 오버헤드가 된다.
* 쓰레기 수집이 일어나는 타이밍이나 점유 시간을 미리 예측하기 어렵다.(unpredictable collect time) 때문에 프로그램이 예측 불가능하게 일시적으로 정지할 수 있다. 이런 특성은 특히 실시간 시스템에는 적합하지 않다.
* 할당된 메모리가 해제되는 시점을 알 수 없다.(unpredictable memory free time) 자원 할당과 변수 초기화를 일치하는 RAII(Resource Acquisition is Initialization) 스타일의 프로그래밍에서는, 이것은 자원 해제 시점을 알 수 없다는 것을 의미한다.

> Reference : [wiki : Garbage Collector(가비지 콜렉터, 쓰레기 수집가)](https://en.wikipedia.org/wiki/Garbage_collection_(computer_science))

#### JIT 컴파일러 (Just-In-Time, JIT compiler)

JIT 컴파일(just-in-time compilation) 또는 동적 번역(dynamic translation)은 프로그램을 실제 실행하는 시점에 기계어로 번역하는 컴파일 기법으로 프로그램의 실행 속도를 빠르게 하기 위해 사용된다.
JIT 컴파일러는 인터프리트(Interpret) 방식과 정적 컴파일(static compilation)을 혼합한 방식으로 생각할 수 있는데, 실행 시점에서 인터프리트 방식으로 기계어 코드를 생성하면서 그 코드를 **캐싱(caching)** 하여, 같은 함수가 여러 번 불릴 때 매번 기계어 코드를 생성하는 것을 방지한다.

#### 인터프리터 (Interpreter)

인터프리터는 프로그래밍 언어의 소스 코드를 바로 실행하는 컴퓨터 프로그램 또는 환경을 말한다. 인터프리터는 다음의 기능 중 한가지 이상을 포함하는 프로그램이다.

1. 소스 코드를 직접 실행한다.
2. 소스 코드를 효율적인 다른 중간 코드로 변환하고, 변환한 것을 바로 실행한다
3. 인터프리터 시스템의 일부인 컴파일러가 만든, 미리 컴파일된 저장 코드의 실행을 호출한다.

인터프리터는 컴파일된 프로그램들에 비해 느리게 실행되지만 줄 단위로 번역, 실행되기 때문에 시분할 시스템이나 대화형 시스템에 유용하며 원시 프로그램의 변화에 대한 반응이 빠르다.

> Reference : [wiki : Interpreter(인터프리터)](https://en.wikipedia.org/wiki/Interpreter_(computing))

#### JRE (Java Runtime Environment)

> JRE = JVM + API

#### JDK (Java Development Kit)

                    +---------------------------------JDK---------------------------------+
                    |                                                                     |
                    |    +--------------------JRE----------------+    +-------------+     |
                    |    |  +---------------+    +-----------+   |    |             |     |
                    |    |  |  Java Virtual |    |  Library  |   |    | Development |     |
                    |    |  |    machine    |    |  Classes  |   |    |    Tools    |     |
                    |    |  +---------------+    +-----------+   |    |             |     |
                    |    +---------------------------------------+    +-------------+     |
                    |                                                                     |
                    +---------------------------------------------------------------------+

[JDK](https://ko.wikipedia.org/wiki/%EC%9E%90%EB%B0%94_%EA%B0%9C%EB%B0%9C_%ED%82%A4%ED%8A%B8)는 자바 SE, 자바 EE, 또는 자바 ME 플랫폼 중 하나를 구현한 것으로 솔라리스, 리눅스, 맥 OS X, 또는 윈도 자바 개발자를 대상으로 오라클에 의해 바이너리 제품으로 제공된다. 자바 플랫폼의 등장 이래 지금까지 가장 널리 사용되는 소프트웨어 개발 키트(SDK)로 자바 실행 환경(Java Runtime Environment, JRE)이 포함된다.

> JDK = JRE + Development tool

### **데이터 타입 (Java data type)**
<hr>

자바에서 데이터를 저장하는 방법은 크게 기본값을 저장하는 **Primitive data type**과 객체의 참조를 저장하는 **Reference data type**으로 분리된다.

1. Primitive data type 
    - 기본적(일반적)인 값을 기억하는 변수의 type
    - byte, short, int, float, double, char, boolean, long
    - primitive type 중 작은 크기의 타입은 큰 크기의 타입으로 자동 형 변환된다. ex) long var = 10;
    - 정수형은 실수형으로 자동형 변환된다. ex) double d = 10;

Type | Keyword | Range 
:----: | :----: | ----
논리형 | boolean | true, false
문자형 | char | 16bit Unicode <br> 수치로는 0 ~ 65535
정수형 | byte | 8bit, -128 ~ 127
정수형 | short | 16bit, -32,768 ~ 32,767
정수형 | int | 32bit, -2,147,483,648 ~ 2,147,483,647
정수형 | long | 64bit, <br>-9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807
실수형 | float | 32bit, IEEE 754-1985 standard
실수형 | double | 64bit, IEEE 754-1985 standard

2. Reference data type
    - 객체의 참조(Reference)값을 기억하는 변수
    - class, interface, 배열
    - 자바는 객체지향 언어이기 때문에 객체가 아닌 primitive data type을 객체화 시켜주는 wrapper class 기능을 지원한다.

primitive와 reference data type은 다음과 같이 메모리에 할당된다.

```
    int a = 10;
    String str = "Hello";

  +---------------------------------------JVM Memory or Runtime Data Area--------------------------------------+
  |                                                                                                            |
  |           Object              +---Stack---+                      +---Heap---+                              |
  |  reference variable str ----> |  0x0FA02  |-----------           |          |                              |
  |                               |-----------|          |---------> | "Hello" <---- Allocated in 0xFA02       |
  |   primitive variable a  ----> |     10    |                      |          |                              |
  |                               +-----------+                      +----------+                              |
  |                                                                                                            |
  +------------------------------------------------------------------------------------------------------------+

```

primitive 기본 자료형은 stack 메모리에 값이 할당되며 a는 stack memory에 할당된 주소를 기억한다. refernce 객체 자료형은 heap memory 영역에 동적으로 할당되며 stack memory에 할당된 address값을 기억하고 str은 이 address값을 기억한다.

```java
class Person{
    private int age;
            :
}
```

Person이라는 이름의 클래스를 생성자를 이용하여 heap memory에 동적으로 할당하였을때, Person 클래스에 존재하는 멤버 변수 age는 int -> Integer 타입으로 Wrapping 시켜준다. 따라서, Person 클래스의 primitive 멤버변수 age는 Integer(Wrapper class) type으로 heap memory에 할당되게 된다. 
    


### **상수 영역(constant pool)**
<hr>

```java
public class StringTest {

	public static void main(String[] args) {
		String s = "mylimeorange";
		String t = new String("mylimeorange");
		String x = "mylimeorange";
		
		System.out.print("s == t : ");
		System.out.println(s==t);

		System.out.print("s.equals(t) : ");
		System.out.println(s.equals(t));
		
		System.out.print("s == x : ");
		System.out.println(s==x);
	}

}
```
자바 가상 머신(JVM)은 Permanent area(고정 영역)에 **String constant pool**과 **Class constant pool**을 프로세스 종료 시점까지 유지한다. 위의 코드에서 리터럴(literal) 방식으로 만든 s와 x는 String constant pool에 동일한 값을 참조하게 된다. 이는 리터럴 방식으로 생성할 경우 내부적으로 new String()을 호출한 뒤, String.intern() 메소드가 호출되어 고유 인스턴스를 공유하도록 interned 되기 때문이다. "mylimeorange"를 String constant pool에 할당하고 난 후에 동일한 데이터에 대해 x는 이미 할당된 "mylimeorange"참조를 기억하게 된다. new 키워드를 이용한 t의 "mylimeorange"의 경우 constant pool이 아닌 heap memory에  할당되므로 s와 x가 가르키고 있는 주소값과는 다른 주소에 할당되게 되므로 s==t 연산은 false를 반환한다.

```cmd
s == t : false
s.equals(t) : true
s == x : true
```
하지만, 아래의 String class의 재정의된 equals의 경우 char[]을 통해 비교 연산을 수행하므로 참값을 반환하게 된다. 따라서, 각 String 문자열 내용 자체를 비교하기 위해서는 주소 비교 연산을 수행하는 '=='이 아닌 재정의된 equals 메소드를 호출하여 비교 연산을 수행해야 올바른 결과를 도출할 수 있다.
```java
 /**
     * Compares this string to the specified object.  The result is {@code
     * true} if and only if the argument is not {@code null} and is a {@code
     * String} object that represents the same sequence of characters as this
     * object.
     *
     * @param  anObject
     *         The object to compare this {@code String} against
     *
     * @return  {@code true} if the given object represents a {@code String}
     *          equivalent to this string, {@code false} otherwise
     *
     * @see  #compareTo(String)
     * @see  #equalsIgnoreCase(String)
     */
    public boolean equals(Object anObject) {
        if (this == anObject) {
            return true;
        }
        if (anObject instanceof String) {
            String anotherString = (String)anObject;
            int n = value.length;
            if (n == anotherString.value.length) {
                char v1[] = value;
                char v2[] = anotherString.value;
                int i = 0;
                while (n-- != 0) {
                    if (v1[i] != v2[i])
                        return false;
                    i++;
                }
                return true;
            }
        }
        return false;
    }
```

Constant pool(상수 영역)은 이외에도 다양한 기능을 수행한다.

![**constant pool**](http://blog.jamesdbloom.com/images_2013_11_17_17_56/JVM_Internal_Architecture_small.png)

 위의 그림에서 프레임(Frame)은 피연산자(조작 명령)등이 존재하는 곳이며, 동적 연결(Dynamic linking)이 발생한다. 이 영역은 클래스와 멤버를 빠르게 추적하기 위해 상수 영역을 사용한다.

 각 프레임은 런타임 상수 영역(Runtime constant pool)에 대한 참조는 동적 연결을 지원하는 역할을 한다. 자바의 경우 컴파일 될 때에 변수 및 메소드에 대한 모든 참조가 클래스의 상수 영역에 기호 참조(symbolic reference)로 저장된다. 기호식 참조는 실제 메모리 위치를 가리키는 참조가 아닌 논리적 참조를 의미한다.

### **클래스 활용 (Class)**
<hr>

1. **생성자 (Constructor)**
     ```
    [Modifier] class identifier(...){
        // Initializing
    }
    ```   
    생성자는 객체 생성시 자동 호출되는 특별한 기능으로 주로 객체 초기화 작업을 수행한다. 정의하는 방식은 클래스와 이름이 동일하고 리턴 타입이 없으며, 반드시 존재해야 한다. 필요에 의해 개발자가 정의하지 않은 경우 컴파일러가 기본 생성자(Default constructor, No parameters)를 코드에 삽입한다. 
    
    만약 parameter가 존재하는 생성자를 개발자가 정의하였을 경우에 컴파일러는 더이상 기본 생성자를 추가하지 않기 때문에 개발자가 코드에서 기본 생성자를 호출할 경우 에러가 발생할 수 있다. 따라서, 생성자를 정의할 때에는 기본 생성자도 같이 정의하는 것이 바람직하다. *추가적으로 기본 생성자를 정의하여 멤버 변수를 초기화할 때, 기본 값(default value)이 아닌 의미있는 값(meaningful value)으로 초기화하는 것이 바람직하다.*

    * this 참조 : 객체를 생성하면 그 객체의 참조(reference)를 저장하기 위한 this 참조가 자동 생성된다. 메소드나 멤버 변수등을 사용할 때 현재 수행중인 객체의 참조 정보를 가지고 있는 this를 활용한다. 메소드에서 사용되는 변수에 대해 JVM은 해당 변수가 로컬(local)로 존재하는지 확인하고 없을 경우 this 참조의 객체에 접근하여 변수를 확인한다. this 참조는 재정의 메소드(Override)의 동적 바인딩(Dynamic binding) 개념에 적용된다.

2. **메소드 (Method)**
    ```
    [Modifier] return_type method_name(parameter list){
        // Function execute
    }
    ```
    메소드는 객체가 가져야 할 기능을 구현한다. 이 때 필요한 데이터(Data)를 paramater list를 통해 받을 수 있다. 원하는 기능을 수행한 후에는 결과 값을 필요에 따라 method를 호출한 측에 return을 이용하여 결과를 반환한다. 자바의 경우 Reference 타입의 parameter를 전달할 때, 변수가 가지는 값이 참조 값(address)이므로 call by value 방식에 의해 참조 값이 전달된다. 즉, 일반적으로 모든 파라미터 데이터를 복사하는 call by value 방식이 아닌, 참조 값의 주소 값만을 복사하므로 **파라미터 전달 시 모든 데이터가 복사되지 않는다**.
     
     
     추가적으로, 자바에서는 다형성을 위해 메소드 오버로딩(Overloading)과 오버라이딩(Overriding)을 지원한다. 
    
    * 오버로딩(Overloading) : 한 클래스 내에 메소드 명이 같고 시그니처(signature, Method + parameters) 다르게 정의하여 동일한 이름으로 다양한 기능 수행을 가능하게 한다.
    * 오버라이딩(Overriding) : 상속 관계의 하위 클래스(Derived class)에서 부모 클래스(Base class)에서 물려받은 메소드 기능을 확장(Extend) 또는 변경(Update)한다.

3. **접근 제어자 (Access modifier)**

    Access modifier | Same class | Same package | Sub class | External  
    :----: | :----: | :----: | :----: | :----: 
    private | O | 
    (default) | O | O | 
    protected | O | O | O |
    public | O | O | O | O |
    (O : accessible, X : inaccessible)

    * private : 같은 클래스 내에서만 접근 가능하다.

    * (default) : 아무것도 정의하지 않은 경우 같은 패키지 내부에서는 접근 가능하나 상속받은 객체에서 활용 불가하다.

    * protected : 패키지가 다르면 사용할 수 없으나, 상속받았을 경우 사용 가능하다.

    * public : 어디에서나 접근 가능하다.

    이외에도 추가적으로 주로 사용하는 Usage modifier(사용 제한자)에는 static, final, abstarct 등의 키워드가 존재한다. 
    
    이 중 **static**의 경우 객체 생성 없이 사용할 경우에 활용하며 모든 객체가 공유한다는 의미를 포함한다. static block의 경우 클래스가 메모리에 로딩될 때 한번만 실행된다. 또한, static이 붙은 멤버 변수는 객체 instance 시 마다 여러번 생성되지 않고 여러 객체 instance가 공유하는 변수가 된다. 이 변수들은 객체 내부가 아닌 별도의 공간에 생성되며 클래스 로딩 시에 멤버가 생성되어 프로그램 종료 시까지 클래스와 동일하게 메모리에서 항상 상주하게 된다. 이러한 특성 때문에 객체가 생성되는 시점에 만들어지는 this, super 참조를 통해서는 static에 접근할 수 없다. 

4. **캡슐화 (Encapsulation)**
    
    클래스 설계 시에 데이터와 기능을 클래스에 넣어 설계하고, 중요한 데이터나 내부 구현을 숨기고(private) 필요한 기능만 노출(public)시켜 정의하는 기법을 캡슐화(Encapsulation)이라고 한다.

### **상속과 다형성(Inheritance & Polymorphism)**
<hr>

1. **상속 (Inheritance)**

    클래스를 설계할 때, 특정 클래스를 상속받아 그 클래스의 변수(data)와 기능(method)를 사용하도록 하는 기능이다. 상속에는 다음과 같은 두 가지 개념이 적용된다.

    * Generalization : 추출된 class의 공통적인 기능을 모아 super class로 정의할 수 있다.

    * Specialization : 비슷한 속성과 기능을 가지고 있는 다른 class를 상속받아 새로운 class를 정의할 수 있다.

    상속받는 클래스에서는 객체 생성시 부모 객체의 참조 값을 갖는 super 키워드를 통해 부모 클래스(Base class)의 모든 속성과 기능을 상속받아 사용할 수 있게 되며 원하는 기능에 대해 재정의(Overriding)할 수 있고, 필요한 기능을 추가로 작성할 수 있다. 
    
    ```java
    public class Dervied_name extends Base_name{
        ...
    }
    ```
    자식(Derived class)에서는 extends 키워드를 통해 상속 기능을 구현할 수 있다. 자바는 단일 상속(single inheritance)만을 지원하므로 다중 상속(multiple inheritance) 기능을 구현하기 위해서는 인터페이스(interface)를 활용해야 한다.
    
2. **다형성 (Polymorphism)**

    다형성(Polymorphism)은 객체 다형성(Object polymorphism)과 메소드 다형성(Method polymorphism)으로 구분된다.

    * 객체 다형성 (Object polymorphism) : sub 객체 생성시 super도 같이 생성되어지기 때문에 memory에 존재하는 supert type으로 변수를 선언할 수 있다.
        ```java
        Base derived = new Derived();
        ```
    
    * 메소드 다형성 (Method polymorphism) : 메소드 호출 시 가상머신은 해당 메소드의 재정의(Overriding) 여부를 확인하고 생성된 객체에 대하여 가장 마지막에 Overriding 된 메소드를 호출한다.(*=**this** 참조에 우선하여 호출한다.*)
        ```java
        class Base{
            public void run(){
                System.out.println("Base run.");
            }
        }
        public class Derived extends Base{
            @Override
            public void run(){
                System.out.println("Derived run.");
            }
        }
        ```
        위의 정의된 내용에 대해

        ```java
        public static void main(String[] args){
            Base derived = new Derived();
            derived.run();
        }
        ```
        이와 같은 프로그램을 실행시켰을 때에 객체 초기화 시점에 Base 타입으로 up-casting이 이루어지더라도 VM이 this 참조에 우선한 Derived의 메소드를 실행 시점에 동적으로 바인딩(Dynamic binding)한다.
    
    자바에서는 다형성을 구현하기 위해 인터페이스(Interface)를 활용하기도 한다. 
    
    * 인터페이스(Interface) : 상수와 구현되지 않은 public abstract 메소드로만 구성되며 객체를 생성할 수 없다. 특히 인터페이스는 자바의 단일 상속(single inheritance) 문제를 보완하는 다중 implements를 허용한다. 
    
        인터페이스는 다음과 같은 특징을 갖는다.
        
        * 객체를 생성할 수 없다.
        * 구현되지 않은 메소드(abstract)를 포함한다.
        * 상속을 받은 sub class가 모든 메소드를 재정의(Overriding)해야 한다. (Definition delegate)
        * 상속한 class 들의 명세서 역할로 사용한다.

        ```java
        interface Run{
            void run(); // = public abstract void run();
        }
        class Base implements Run{
            @Override
            public void run(){  // if do not implements run, Derived must be implemented run.
                System.out.println("Base run.");
            }
        }
        public class Derived extends Base{
            @Override
            public void run(){  // implements run or not, because Base implemented.
                System.out.println("Derived run.");
            }
        }
        ```
        위의 코드에서 Base에서 Run의 메소드를 재정의하였을 경우 자식에서의 재정의는 선택적이지만, Base에서 재정의하지 않았을 경우 Derived의 재정의는 필수적이다.

위의 두 가지 개념(Inheritance, Polymorphism)을 적절히 활용하여 클래스를 설계하고 구현하는 것이 다형성을 구현하는 방식이다.

### **API (Application Programming Interface)**
<hr>
 API는 응용 프로그램에서 사용할 수 있도록, 운영 체제나 프로그래밍 언어가 제공하는 기능을 제어할 수 있게 만든 인터페이스를 뜻하며, 이를 활용하여 프로그래머가 손쉽게 프로그램을 개발할 수 있다. API는 다음과 같이 활용할 수 있다.
 
 * **라이브러리와 프레임 워크(Library & Framework)** : 단일 API는 동일한 프로그래밍 인터페이스를 공유하는 여러 라이브러리의 형태로 구현할 수 있다. 또한, 한 언어의 기능을 다른 언어로 구현 된 인터페이스에 매핑하면 언어 바인딩(Language binding)을 통해 한 언어로 작성된 라이브러리나 서비스를 다른 언어로 개발할 때 사용할 수 있다.

 * **운영체제(Operating systems)** : API는 응용 프로그램과 운영 체제 간의 인터페이스를 지정할 수 있다. 예를 들어, Linux 및 Berkeley Software Distribution 은 POSIX API를 구현하는 운영 체제이다.

 * **원격 API (Remote APIs)** : 원격 API를 사용하면 개발자가 언어나 플랫폼에 관계없이 프로토콜, 통신 표준을 통해 원격 리소스를 조작 할 수 있다. 따라서 원격 API는 객체 지향 프로그래밍에서 객체 추상화를 유지하는 데 유용하다. 프록시 객체에서 로컬로 실행되는 메소드 호출은 원격 프로토콜을 사용하여 원격 객체에서 해당 메소드를 호출하고 반환한 결과 값을 조작할 수 있다.

* **웹 API (Web APIs)** : 웹 개발의 컨텍스트에서 사용되는 경우 API는 일반적으로 [HTTP(Hypertext Transfer Protocol)](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) 요청 메시지 와 같은 일련의 사양으로 정의되며 대개 XML(Extensible Markup Language) 형식 또는 JSON (JavaScript Object Notation )형식의 응답 메시지를 활용한다. 

    *"정보 숨기기(Information Hiding)의 원칙은 모듈 사용자가 모듈 내부의 복잡성을 이해할 필요가 없도록 모듈의 구현 세부 사항을 숨김으로써 모듈 프로그래밍을 가능하게하는 프로그래밍 인터페이스의 역할을 설명합니다." <br>
    "The principle of information hiding describes the role of programming interfaces as enabling modular programming by hiding the implementation details of the modules so that users of modules need not understand the complexities inside the modules."*
* **java.lang API** : 표준 API의 package 구조로 자바의 가장 기본적인 클래스를 제공한다. 대표적으로 자바의 모든 클래스가 기본적으로 상속받는 Object클래스가 이에 해당한다. 이 클래스에서는 모든 클래스의 공통적인 기능을 정의하고, 자주 사용되는 Method를 정의하여 필요 시 Overriding(재정의)하도록 권장한다. ex) toString(), hashCode(), equals()..

> Reference : [API](https://en.wikipedia.org/wiki/Application_programming_interface)

### **JUnit**
<hr>
