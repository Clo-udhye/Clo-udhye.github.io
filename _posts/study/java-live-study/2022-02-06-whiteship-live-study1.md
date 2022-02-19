---
layout: post
title: "[Java] JVM 구조와 작동"
tags: java live-study jvm 
image: 
    path: /assets/img/live-study/live-study1-cover.png
accent_color: '#344CB7'
description: >
    [dev-ujin✨](https://github.com/dev-ujin)과 함께하는 [live study📝](https://github.com/whiteship/live-study) 1주차
categories:
    - study
    - java-live-study
related_posts:    
    - /study/java-live-study/2022-02-13-whiteship-live-study2/
    - /study/java-live-study/2022-02-19-whiteship-live-study3/

---
### [Java] JVM 구조와 작동

##### JVM이란 무엇인가
운영체제는 자바 프로그램을 바로 실행할 수 없는데, 그 이유는 자바 프로그램은 완전한 기계어가 아닌, 중간단계의 바이트 코드이기 때문에 이것을 해석하고 실행할 수 있는 가상의 운영체제가 필요하다. 이것이 **자바 가상 기계(JVM : Java Virtual Machine)**이다.   

JVM은 실 운영체제를 대신해서 자바 프로그램을 실행하는 가상의 운영체제 역할을 한다. 운영체제별로 프로그램을 실행하고 관리하는 방법이 다르기 때문에 운영체제별로 자바 프로그램을 별도로 개발하는것보다는 운영체제와 자바 프로그램을 중계하는 JVM을 두어 자바 프로그램이 여러 운영체제에서 동일한 실행결과가 나오도록 설계한 것이다. 
따라서 개발자는 운영체제와 상관없이 자바 프로그램을 개발할 수 있다. 바이트 코드는 모든 JVM에서 동일한 실행 결과를 보장하지만, JVM은 운영체제 종속적이다. 자바 프로그램을 운영체제가 이해하는 기계어로 번역해서 실행해야 하므로 JVM은 운영체제에 맞게 설치되어야 한다. JVM은 JDK 또는 JRE를 설치하면 자동으로 설치되는데, JDK와 JRE가 운영체제별로 제공된다. 운영체제와 JVM 그리고 자바 프로그램의 실행단계를 그림으로 표현하면 다음과 같다.
<p align="center">
    <img src="/assets/img/live-study/JVM.png" alt="자바 프로그램의 실행단계" width="80%">
</p>
자바프로그램은 확장자가 .java인 파일을 작성하는 것부터 시작된다. 이것을 소스파일이라고 하는데, 이 소스파일을 컴파일러(javac.exe)로 컴파일하면 확장자가 .class인 바이트코드파일이 생성된다. 바이트 코드 파일은 JVM 구동 명령어(java.exe)에 의해 JVM에서 해석되고 해당 운영체제에 맞게 기계어로 번역된다. 바이트코드는 하나지만, JVM에 의해서 번역되는 기계어는 운영체제에 따라서 달라진다.

##### JDK와 JRE의 차이
자바 프로그램을 개발하기 위해서는 먼저 Java SE(Standard Edition)의 구현체를 설치해야한다. 
Java SE의 구현체는 JDK와 JRE 두가지 버전이 있다 .
- JRE(Java Runtime Environment) : JVM + 표준 클래스 라이브러리
- JDK(Java Development Kit) : JRE + 개발에 필요한 도구

JDK는 프로그램 개발에 필요한 JVM, 라이브러리 API, 컴파일러 등의 개발 도구가 포함되어있고 JR에는 프로그램실행에 필요한 JVM, 라이브러리 API만 포함되어 있다. 자바 프로그램을 개발하고자 하는 것이 아니고, 이미 개발된 프로그램만 실행한다면 JRE만 설치하면 된다.

##### 컴파일 하는 방법 & 실행하는 방법
자바 프로그램을 개발하기 위해서는 우선 파일 확장명이 .java인 텍스트 파일을 생성하고 프로그램 소스를 작성한다. 이렇게 만들어진 파일을 자바 소스 파일이라고 한다. 작성 완료된 자바 소스 파일은 컴파일러(javac.exe)로 컴파일 해야한다. 컴파일이 성공되면 확장자명이 .class인 바이트 코드 파일이 생성된다. 예를 들어, 명령프롬프트에서 Hello.java 소스파일을 다음과 같이 컴파일하면 Hello.class 파일이 생성된다. 
```
javac Hello.java
```
바이트 코드 파일은 완전한 기계어가 아니므로 단독으로 실행할수없고 JVM이 실행되어야 한다. JVM을 구동시키는 명령어는 java.exe이다. 예를 들어 Hello.class라는 바이트 코드 파일을 java.exe로 실행하려면 명령프롬프트에 다음과 같이 입력하고 `Enter`키를 누르면 된다.
```
java Hello
```
주의할점은 java.exe로 바이트 코드파일을 실행 할깨는 .class 확장명을 제외한 이름을 입력해야한다.
java.exe명령어가 실행되면 JVM은 바이트 코드 파일을 메모리로 로드하고, 최적희 기계어로 번역된다. 그리고 main()메소드를 찾아 실행시킨다. 

##### 바이트코드란 무엇인가
**자바 바이트 코드(Java bytecode)란 자바 가상 머신이 이해할 수 있는 언어로 변환된 자바 소스 코드**를 의미한다. 자바 바이트 코드의 확장자는 .class로 자바 가상 머신만 설치되어 있으면, 어떤 운영체제에서라도 실행될 수 있다.

##### JVM 구성 요소
<p align="center">
    <img src="/assets/img/live-study/JVM_elements.png" alt="JVM구성요소" width="80%">
</p>
- Class Loader
    Java Compiler 를 통해서 .class 확장자를 가진 클래스 파일은 각 디렉터리에 흩어져 있다. 
    또한, 기본적인 라이브러리의 클래스 파일들은 $JAVAHOME_ 내부 경로에 존재한다. 각각의 클래스 파일들을 찾아서 JVM 의 메모리에 탑재해주는 역할을 하는 것이 바로 ClassLoader의 역할이고 JVM에 관련된 다른 일들도 같이하게 된다. 
    ClassLoader 3가지 역할
    - Loading :  클래스 파일을 탑재하는 과정
    - Linking : 클래스 파일을 사용하기 위해 검증하고, 기본 값으로 초기화하는 과정
    - Initialization : static field 의 값들을 정의한 값으로 초기화를 하는 과정

- Runtime Data Area
    이렇게 탑재하는 클래스 파일들은 JVM 의 Run-Time Data Area 에 위치하게 된다.
    Runtime Data Area는 크게 Method Area, Heap, Java Stacks, PC registers, Native Method Stacks 가 존재한다.
    ![Runtime Data Area](/assets/img/live-study/JVM_Run-time-Data-Area.png)
    - Method Area
    Method Area 에는 인스턴스 생성을 위한 객체 구조, 생성자, 필드 등이 저장된다. 
    Runtime Constant Pool 과 static 변수, 그리고 메소드 데이터와 같은 Class 데이터들도 이곳에서 관리가 된다. 
    JVM 당 하나만 생성이 된다. 인스턴스 생성에 필요한 정보도 존재하기 때문에 JVM 의 모든 Thread 들이 Method Area 을 공유한다. JVM 의 다른 메모리 영역에서 해당 정보에 대한 요청이 오면, 실제 물리 메모리 주소로 변환해서 전달한다. 기초 역할을 하므로 JVM 구동 시작 시에 생성이 되며, 종료 시까지 유지되는 공통 영역이다.

    - Heap
    Heap 영역은 코드 실행을 위한 Java 로 구성된 객체 및 JRE 클래스들이 탑재된다. 
    문자열에 대한 정보를 가진 String Pool 뿐만이 아니라 실제 데이터를 가진 인스턴스, 배열 등이 저장이 된다. 
    JVM 당 하나만 생성이 되고, 해당 영역이 가진 데이터는 모든 Java Stack 영역에서 참조되어, Thread 간 공유한다. 
    Heap 영역이 가득 차게 되면 `OutOfMemoryError`를 발생시키게 된다.
    Heap 에서는 참조되지 않는 인스턴스와 배열에 대한 정보 또한 얻을 수 있기 때문에 GC 의 주 대상이다. 
    각 Thread 별로 메모리를 할당받는 Java Stack 영역과 달리 조금은 속도가 느리다.
    모든 Thread 들이 해당 영역인 Heap 을 공유하여 Java 의 동시성 문제가 발생하게 된다. 각각의 Thread 메모리가 따로 관리되는 것과 달리 이 부분은 Thread 에 의해서 공유가 되기 때문에 Thread Safe 하지 않다. 이 때문에 해당 영역에 있는 객체나 인스턴스를 사용하게 되면, synchronized 블록을 사용하는 방법 등을 비롯하여 동시성을 지켜주는 방법을 사용해야 한다.

    - Java Stacks
    각 Thread 별로 따로 할당되는 영역이다. 
    Heap 메모리 영역보다 비교적 빠르다. 
    각각의 Thread 별로 메모리를 따로 할당하기 때문에 동시성 문제에서 자유롭다. 
    각 Thread 들은 메소드를 호출할 때마다 Frame이라는 단위를 추가(push)한다. 메소드가 마무리되며 결과를 반환하면 해당 Frame 은 Stack 으로부터 제거(pop)된다. Frame은 메소드에 대한 정보를 가지고 있는 Local Variable, Operand Stack, Constant Pool Reference 로 구성되어있다. 
        - Local Variable 은 메소드 안의 지역 변수들을 가지고 있는 공간 
        - Operand Stack 은 메소드 내 연산을 위해서, 바이트 코드 명령문들이 들어있는 공간
        - Constant Pool Reference 는 Constant Pool 참조를 위한 공간
    이렇게 구성된 Java Stack 은 메소드가 호출될 때마다 Frame 이 쌓인다.
    Java Stack 영역이 가득 차게 되면 `StackOverflowError` 를 발생시킨다. 다만 JVM 의 전체적인 메모리가 부족하면 `OutOfMemoryError` 가 발생하기도 한다.

    - Native Method Stacks
    Java 로 작성된 프로그램을 실행하면서, 순수하게 Java로 구성된 코드만을 사용할 수 없는 시스템의 자원이나 API가 존재한다. 다른 프로그래밍 언어로 작성된 메소드들을 Native Method 라고 합니다. Native Method Stacks 는 Java 로 작성되지 않은 메소드를 다루는 영역으로 C Stacks 라고 불리기도 한다. Java Stacks 영역과 비슷하게 Native Method가 실행될 경우 Stack 에 해당 메서드가 쌓인다. 각각의 Thread 들이 생성되면 Native Method Stacks 도 동일하게 생성된다.

    - PC(Program Counter) Registers
    Java에서 Thread는 각자의 메소드를 실행하게 된다. 이때, Thread별로 동시에 실행하는 환경이 보장되어야 하므로 최근에 실행 중인 JVM에서는 명령어 주소값을 저장할 공간이 필요하다. 이 부분을 PC Registers 영역이 관리하여 추적해준다. Thread들은 각각 자신만의 PC Registers 를 가지고 있다. 만약 실행했던 메소드가 네이티브하다면 undefined가 기록이 되고 실행했던 메소드가 네이티브하지 않다면, PC Registers 는 JVM 에서 사용된 명령의 주소 값을 저장한다.
    
- Execution Engine
Class Loader에 의해 JVM으로 로드된 Class 파일(바이트코드)들은 Runtime Data Areas의 Method Area에 배치되는데, JVM은 Method Area의 바이트 코드를 Execution Engine에 제공하여, Class에 정의된 내용대로 바이트 코드를 실행시킨다. 이 때, 로드된 바이트코드를 실행하는 Runtime Module이 Execution Engine(실행 엔진)이다. 실행 엔진은 바이트코드를 명령어 단위로 읽어서 실행하는데, 두 가지 방식을 혼합하여 사용한다. 
    
    - Interpreter 방식
    바이트코드를 한 줄씩 해석, 실행하는 방식이다. 초기 방식으로, 속도가 느리다는 단점이 있다.
        
    - JIT(Just In Time) 컴파일 방식 또는 동적 번역(Dynamic Translation)
    바이트코드를 JIT 컴파일러를 이용해 프로그램을 실제 실행하는 시점(바이트코드를 실행하는 시점)에 각 OS에 맞는 Native Code로 변환하여 실행 속도를 개선하였다. 하지만, 바이트코드를 Native Code로 변환하는 데에도 비용이 소요되므로, JVM은 모든 코드를 JIT 컴파일러 방식으로 실행하지 않고, 인터프리터 방식을 사용하다 일정 기준이 넘어가면 JIT 컴파일 방식으로 명령어를 실행한다.         또한, 전체 코드의 필요한 부분만 변환한다. 기계어로 변환된 코드는 캐시에 저장되기 때문에 재사용시 컴파일을 다시 할 필요가 없다

- Garbage Collector
    Garbage Collection, GC는 JVM 상에서 더 이상 사용되지 않는 데이터가 할당되어있는 메모리를 해제시켜주는 장치이다. JVM 에서 자동으로 동작하기때문에 Java는 특별한 경우가 아니면 메모리 관리를 개발자가 직접 해줄 필요가 없다. GC 가 주로 동작하는 대상은 Heap 영역 내의 객체 중에서 참조되지 않은 데이터이다.

##### JIT 컴파일러란 무엇이며 어떻게 동작하는지
JAVA 프로그램은 여타 언어들처럼 `프로그램 → 컴파일러(최적화) → 네이티브 코드`이나, `프로그램 → 인터프리터(직접실행)` 방식이 아닌 `프로그램 → 컴파일러 → 가상머신(최적화 및 직접실행)`의 방식으로 실행된다. JIT 컴파일러는 실행시간 최적화하는데에 이용된다. 

JIT(Just-In-Time) 컴파일러는 런타임시 .class 바이트 코드를 네이티브 코드로 컴파일하여 JAVA 응용 프로그램의 성능을 향상시키는 런타임 환경의 구성 요소이다.

자바 프로그램은 여러 컴퓨터 아키텍처 환경에서 JVM이 해석할 수 있는 플랫폼 중립(platform-neutral)적인 바이트 코드를 포함하는 클래스로 구성된다. 런타임에 JVM은 클래스 파일을 로드하고 각 개별 바이트 코드를 해석하면서 적절한 계산을 수행한다. 해석 중에 추가 프로세서 및 메모리 사용을 하여 JAVA 응용 프로그램이 네이티브 프로그램보다 느리게 수행될 수 있다. JIT 컴파일러는 런타임에 바이트 코드를 네이티브 코드로 컴파일하여 JAVA 프로그램의 성능을 향상시킨다.

JIT 컴파일러의 JIT는 Just In Time (제 때) 라는 뜻이며 이는 자바 메서드를 호출할때를 말한다. 해당 메서드의 바이트코드를 기계어로 컴파일해서 Just In Time 컴파일하여 실행한다.

이 자바 메서드는 처음 호출 되자마자 바로 컴파일 되는게 아니다. JVM이 호출되는 메서드 각각에 대해 호출마다 호출 횟수를 누적해서 그 횟수가 특정 수치를 초과 할 때 컴파일하는 것이다. 즉, 얼마나 자주 호출되는지 검사한 후 '이제는 컴파일이 필요한 시점이다'라고 판단하는 어떠한 기준이 있는 것이다. 이 기준을 컴파일 임계치 라고 한다. 

<p align="center">
    <img src="/assets/img/live-study/JVM_JIT.png" width="80%">
</p>
    
- 컴파일 임계치
다음의 2가지를 합친 것을 말한다.
    - method entry counter (JVM 내에 있는 메서드가 호출된 횟수)
    - back-edge loop counter (메서드가 루프를 빠져나오기까지 돈 횟수)

두 카운터의 합계를 확인하고 메서드가 컴파일될 자격이 있는지 결정한다. 메서드가 컴파일 될 자격이 있다면 해당 메서드는 컴파일되기 위해 큐에서 대기하게 된다. 그러면 이 메서드들은 이후 컴파일 스레드에 의해 컴파일 되는 것이다.

대표적인 예시로 메서드가 실행되는 루프가 정말 길 경우 중간에 컴파일하는 경우이다. 루프의 실행을 그때그때 카운트하고 컴파일 임계치를 넘게되면 전체 메서드가 아닌 루프만을 컴파일하여 컴파일된 버전을 바로 실행시키는 것이다.

이렇게 메서드 스택상에서 컴파일된 버전을 바로 실행시키는 것을 OSR(On-Stack Replacement)이라고 한다.
<p align="center">
    <img src="/assets/img/live-study/JVM_ORS.png" art="ORS" width="80%">
</p>
스택 프레임을 컴파일된 것으로 교체해서 속도를 개선한것이라 보면 된다.


<p align="center">
    <img src="/assets/img/live-study/JVM_sequence.png" alt="JVM 동작" width="80%">
</p>


Refernce
- [이것이 자바다 - 신용권의 Java 프로그래밍 완전 정복](http://www.yes24.com/Product/Goods/15651484)
- [https://tecoble.techcourse.co.kr/post/2021-07-15-jvm-classloader/](https://tecoble.techcourse.co.kr/post/2021-07-15-jvm-classloader/)
- [https://tecoble.techcourse.co.kr/post/2021-08-09-jvm-memory/](https://tecoble.techcourse.co.kr/post/2021-08-09-jvm-memory/)
- [https://tecoble.techcourse.co.kr/post/2021-08-30-jvm-gc/](https://tecoble.techcourse.co.kr/post/2021-08-30-jvm-gc/)
- [https://m.blog.naver.com/ksw6169/221647376178](https://m.blog.naver.com/ksw6169/221647376178)
- [https://bloofer.tistory.com/21](https://bloofer.tistory.com/21)
- [https://beststar-1.tistory.com/3](https://beststar-1.tistory.com/3)
- [http://www.tcpschool.com/java/java_intro_programming](http://www.tcpschool.com/java/java_intro_programming)