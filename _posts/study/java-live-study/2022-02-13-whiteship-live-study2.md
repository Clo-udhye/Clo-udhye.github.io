---
layout: post
title: "자바의 프리미티브 타입, 변수 그리고 배열을 사용하는 방법"
image: 
    path: /assets/img/live-study/live-study2-cover.png
accent_color: '#00B8A9'
description: >
    [dev-ujin✨](https://github.com/dev-ujin)과 함께하는 [live study📝](https://github.com/whiteship/live-study) 2주차
categories:
    - study
    - java-live-study
related_posts:    
    - /study/java-live-study/2022-02-06-whiteship-live-study1/    
---
### 자바의 프리미티브 타입, 변수 그리고 배열을 사용하는 방법

### 변수란?
**변수(Variable) : 하나의 값을 저장할 수 있는 메모리 공간**   
변수는 한가지 타입의 값만 저장할 수 있다. 예를 들어 정수 타입의 변수에는 정수값만 저장할 수 있고, 실수 타입의 변수에는 실수값만 저장할 수 있다.

### 변수의 선언
변수를 사용하기 위해서는 먼저 변수를 선언해야 한다. 변수 선언은 어떤 타입의 데이터를 저장할 것인지 그리고 변수이름이 무엇인지를 결정한다.
```java
/*타입  변수이름*/
int     age;        //정수(int)값을 저장할 수 있는 age 변수 선언
double  value;      //실수(double)값을 저장할 수 있는 value 변수 선언
```
**타입 : 변수에 저장되는 값의 종류와 범위를 결정짓는 요소**   
같은 타입의 변수는 콤마`,`를 이용해서 한번에 선언할 수도 있다.
```java
int x, y, x;
```
**변수 이름: 메모리 주소에 붙여진 이름**   
프로그램은 변수 이름을 통해서 메모리 주소에 접근하고, 그곳에 값을 저장하거나 있는 값을 읽는다. 변수이름은 자바 언어에서 정한 명명규칙(naming convention)을 따라야한다.   

작성 규칙|예
:---|:---
첫 번째 글자는 문자이거나 `$`.`_`이어야하고 숫자로 시작할 수 없다.**(필수)**|가능: price, $price, _companyName 안됨: 1v, @speed, $#value
영어 대소문자가 구분된다.**(필수)**|firstname과 firstName은 다른 변수
첫 문자는 영어 소문자로 시작하되, 다른 단어가 붙을 경우 첫 문자를 대문자로 한다.(관례)|maxSpeed, firstName, carBodyColor
문자 수(길이)의 제한은 없다.|  
자바 예약어는 사용할 수 없다.**(필수)**| 아래 표 참조

자바는 다음 표에 언급되어 있는 예약어를 가지고 있다. 예약어로 변수 이름을 지정하면 컴파일 에러가 발생하기 때문에 주의해야 한다. 

분류|예약어
:---|:---
기본 데이터 타입|`boolean, byte, char, short, int, long, float, douvle`
접근 지정자|`private, protected, public`
클래스와 관련된 것|`class, abstract, interface, extends, implements, enum`
객체와 관련된 것|`new, instanceof, this, super, null`
메소드와 관련된 것|`void, return`
제어문과 관련된 것|`if, else, switch, case, default, for, do, while, break, continue`
논리값|`true, false`
예외 처리와 관련된 것|`try, catch, finally, throw, throws`
기타|`transient, volatile, package, import, synchronized, native, final, static, strictfp, assert`
{:.scroll-table}
개발자는 변수의 이름을 보고, 이 변수가 어떤 값을 저장하고 있는지 쉽게 알 수 있도록 의미 있는 변수 이름을 지어주는 것이 좋다. 변수 이름의 길이는 프로그램 실행과는 무관하기 때문에 충분히 길어도 상관없다. 필수적인 것은 아니지만 명명 규칙과 관련된 자바 개발자들 간에 지켜져오는 관례가 있는데, 개발자 간의 코드 작성 패턴을 공유하고자 하는 약속이기 때문에 가급적 지켜주는 것이 좋다. 변수 이름에 한글도 사용이 가능하지만 가급적이면 한글을 포함하지 않는 것이 좋다.

### 변수의 사용
#### 변수값 저장
변수에 값을 저장할 때에는 대입 연산자`=`를 사용한다. 우측의 값을 좌측 변수에 저장한다는 의미를 갖는다. 변수를 선언하고 처음 값을 저장할 경우, 이 값을 **초기값**이라 하고 변수에 초기값을 주는 행위를 **초기화**라고 한다.
```java
int score;  //변수 선언
score = 90; //값 저장
```
```java
int score = 90; //변수의 선언과 초기화를 동시에 할 수 있다.
```
변수의 초기값은 코드에서 직접 입력하는 경우가 많은데, 소스 코드 내에서 직접 입력된 값을 **리터럴(literal)**이라고 부른다. 리터럴은 종류에 따라 정수 리터럴, 실수 리터럴, 문자 리터럴, 논리 리터럴로 구분된다. 이 리터럴들은 정해진 표기법대로 작성되어야한다. 

사실 리터럴은 상수(constant)와 같은 의미지만, 프로그램에서는 상수를 값을 한 번 저장하면 변경할 수 없는 변수로 정의하기 때문에 이와 구분하기 위해 리터럴이라는 용어를 사용한다. 
{:.note}

- **정수 리터럴**   
소수점이 없는 정수 리터럴은 10진수로 간주한다.
```java
0, 75, -100
```
0으로 시작하는 리터럴은 8진수로 간주한다.
```java
02, -04
```
0x또는 0X로 시작하고 0~9 숫자나 A,B,C,D,E,F 또는 a,b,c,d,e,f로 구성된 리터럴은 16진수로 간주한다.
```java
0x5, 0xA, 0xB3, 0xAC08
```

정수 리터럴을 저장할 수 있는 타입 : byte, char, short, int, long
{:.faded}

- **실수 리터럴**   
소수점이 있는 리터럴은 10진수 실수로 간주한다.
```java
0.25, -3.14
```
E 또는 e가 있는 리터럴은 10진수 지수와 가수로 간주한다.
```java 
5E7     //5 x 10^7
0.12E-5 //0.12 x 10^-5
```
실수 리터럴을 저장할 수 있는 타입 : float, double
{:.faded}

- **문자 리터럴**   
작은 따옴표`'`로 묶은 텍스트는 하나의 문자 리터럴로 간주한다.
```java
'A', '한', '\t', '\n'
```
역슬래쉬`\`가 붙은 리터럴은 이스케이프(escape)문자라고도 하는데, 다음과 같이 특수한 용도로 사용된다.   

이스케이프 문자|용도|유니코드   
:---|:---|:---   
'\t'|수평 탭|0x0009   
'\n'|줄 바꿈|0x000a   
'\r'|리턴|0x000d   
'`\"`'|"(큰따옴표)|0x0022   
'`\'`'|'(작은따옴표)|0x0027   
'`\\`'|\\(역슬래시)|0x005c   
'\u16진수'|16진수에 해당하는 유니코드|0x0000 ~ 0xffff   

문자 리터럴을 저장할 수 있는 타입 : char
{:.faded}

- **문자열 리터럴**   
큰따옴표`"`로 묶은 텍스트는 문자열 리터럴로 간주한다. 큰따옴표 안에는 텍스트가 없어도 문자열 리터럴로 간줃한더. 문자열 리터럴 내부에서도 이스케이프 문자를 사용할 수 있다.
```java
"대한민국"
"탭 만큼 이동 \t 합니다"
"한줄 내려 쓰기 \n 합니다"
```

문자열 리터럴을 저장할 수 있는 타입 : String
{:.faded}

- **논리 리터럴**   
true와 false는 논리 리터럴로 간주한다.
```java
true, false
```

논리 리터럴을 저장할 수 있는 타입 : boolean
{:.faded}

#### 변수값 읽기
초기화 되지 않은 변수는 읽을 수 없다. 
```java
/*잘못된 코딩 예(컴파일 에러)*/
int value;                  //변수 value 선언(초기화 안됨)
int result = value + 10;    //변수 value 값을 읽고 10을 더한 결과값을 변수 result에 저장
```
```java
/*올바른 코딩 예*/
int value = 30;             //변수 value가 30으로 초기화됨
int result = value + 10;    //변수 value 값을 읽고 10을 더한 결과값(40)을 변수 result에 저장
```

### 변수의 사용 범위   
변수는 중괄호{} 블록 내에서 선언되고 사용된다.중괄호 블록을 사용하는 곳은 클래스, 생성자, 메소드인데 메소드 블록 내에서 선언된 변수를 특히 **로컬 변수(local variable)**라고 부른다. 로컬 변수는 메소드 실행이 끝나면 메모리에서 자동으로 없어진다. 변수는 메소드 블록 어디에서든 선언할 수 있지만 **변수가 선언된 블록 내에서만 사용이 가능하다**.
```java
public class VariableExample{/*클래스 블록*/
    public static void main(String[] srgs){/*메소드 블록*/
        int value = 10;
        int sum = value + 20;
        System.out.println(sum)
    }/*메소드 블록*/
}/*클래스 블록*/
```
메소드 블록 내에서도 여러 가지 중괄호{} 블록들이 있을수 있다. 
제어문 if(){}, for(){}, while(){}안에서 선언된 변수는 제어문 블록 내에서만 사용이 가능하다. 따라서 변수를 선언할 때에는 변수가 어떤 범위에서 사용될 것인지를 생각하고, 선언 위치를 결정해야한다. 
```java
public static void main(String[] srgs){
    int var1;       // 메소드 블록에서 선언

    if(...){
        int var2;   // if 블록에서 선언
        //var1, var2 사용가능
    }

    for(...){
        int var3;   // for 블록에서 선언
        //var1, var3 사용가능
    }
    
    //var1 사용가능
}
```


### 데이터 타입
모든 변수에는 타입(type:형[形])이 있으며, 타입에 따라 저장할 수 있는 값의 종류와 범위가 달라진다. 변수를 선언할 때 주어진 타입은 변수를 사용하는 도중에 변경할 수 없다. 따라서 변수를 선언할 때 어떤 타입을 사용할지 충분히 고려해야 한다.

#### 기본(원시:primitive) 타입
**기본(원시) 타입: 정수, 실수, 문자, 논리 리터럴을 직접 저장하는 타입**   
각 기본 타입의 메모리 크기와 저장되는 값의 범위   

|값의 종류|기본 타입|메모리 사용크기||저장되는 값의 범위|기본값
|:---|:-----|:-----|:-----|:----------------------|:---
|정수|btye  |1 byte|8 bit|$$-2^7$$～$$(2^7-1)$$(-128～27)|0
|    |char  |2 byte|16 bit|0～$$2^{16}$$ (유니코드:\u0000～\uffff, 0~65535)|'\u0000'
|    |short |2 byte|16 bit|$$-2^{15}$$～$$(2^{15}-1)$$(-32768～32767)|0
|    |int   |4 byte|32 bit|$$-2^{31}$$～$$(2^{31}-1)$$(-2147483648～2147483647)|0
|    |long  |8 byte|64 bit|$$-2^{63}$$～$$(2^{63}-1)$$|0L
|실수|float |4 byte|32 bit|±1.4E-45～±3.4028235E38|0.0f
|    |double|8 byte|64 bit|±4.9E-324～±1.7976931348623157E308|0.0
|논리|boolean|1 byte|8 bit|true, false|false

메모리에는 0과 1을 조정허눈 최소 기억 단위인 비트(bit)가 있다. 그리고 8개의 비트를 묶어서 바이트(byte)라고한다. 기본 타입은 정해진 메모리 사용 크기(바이트 크기)로 값을 저장하는데 바이트 크기가 클수록 표현하는 값의 범위가 크다. 각 타입에 저장되는 값의 범위를 정확히 외울 필요는 없지만, 메모리 사용 크기 정도는 알고있는것이 좋다. 
{:.note}
정수 타입일 경우 $$-2^n$$-1~$$2^{n-1}$$-1의 값을 저장할 수 있는데, 여기서 n이 메모리 사용 크기(bit수)이다. 
{:.note}

##### 정수 타입(byte, char, short, int, long)
정수타입에는 모두 다섯개의 타입이 있으면 저장할 수 있는 값의 범위가 서로 다르다.

|정수타입   |byte|char|short|int|long|
|:---------|:---:|:---:|:---:|:---:|:---:|
|바이트 수  |1  |2  |2  |4  |8  |

자바는 기본적으로 정수 연산을 int타입으로 수행한다. 그렇기 때문에 저장하려는 값이 정수 리터럴이라면 특별한 이유가 없는 한 int타입 변수에 저장하는 것이 좋다. byte와 short이 int 보다는 메모리 사용 크기가 작아서 메모리를 절약할 수 는 있지만, 값의 범위가 작은 편이라서 연산 시에 범위를 초과하기 쉽다.
{:.note}

- **byte 타입**   
byte타입은 색상 정보 및 파일 또는 이미지 등의 이진(바이너리) 데이터를 처리할 때 주로 사용된다. byte타입은 정수 타입 중에서 가장 작은 범위의 수를 저장하는데, 표현할 수 있는 값의 범위는 -128～127($$2^7$$～$$2^7-1$$)이다. 만약 범위를 초과하는 값이 byte변수에 저장될 경우 컴파일 에러 (`Type mismatch: cannot convert from int to byte`)가 발생한다.

    양수가 $$2^7-1$$인 이유는 0이 포함되기 때문이다.
    {:.faded}
byte타입은 1byte, 즉 8bit 크기를 가지므로 다음과 같이 0과 1이 8게로 구성된 이진수로 표현이 가능하다.
![바이트 타입의 이진수 표현](/assets/img/live-study/byteType.png/){: width="80%" height="80%"}   
최상위 비트(MSB: Most Significant Bit)는 정수값의 부호를 결정한다. 최상위 비트가 0이면 양의 정수, 1이면 음의 정수를 뜻한다. 실제 정수값은 나머지 7개의 bit로 결정된다. 
최상위 비트가 1인 음수의 경우에는 모두 1의 보수(1은 0으로, 0은 1로)로 바꾸고 1을 더한 값에 -를 붙여주면 십진수가 된다. 
![이진수의 십진수 변환](/assets/img/live-study/byteTypeBinaryConvert.png/){: width="80%" height="80%"}   
byte타입보다 크기가 큰 short, int, long 타입도 전체 바이트 수만 다를 뿐 동일한 원리로 정수값을 표현한다.
```java
public class ByteExample{
    public static void main(String[] args){
        byte var1 = -128;
        byte var2 = -30;
        byte var3 = 0;
        byte var4 = 30;
        byte var5 = 127;
        //byte var6 = 128;  //컴파일 에러
    }
}
```
코드에서 정상적으로 변수에 올바른 값을 저장하더라도 프로그램 실행중에 저장할 수 있는 값의 범위를 초과하면 최소값부터 다시 반복 저장된다.   
byte의 경우 -128(최소값)부터 시작해서 127(최대값)을 넘으면 다시 -128부터 시작하게 된다. 또다른 정수 타입인 short, int, long 역시 저장할 수 있는 범위를 넘어서면 같은 방식으로 처리된다.    
이와 같이 저장할 수 있는 값의 범위를 초과해서 값이 저장될 경우 엉터리 값이 변수에 저장되는데, 이러한 값을 쓰레기값이라고 한다. 개발자는 쓰레기값이 생기지 않도록 주의해야한다. 
```java
public class GarbageValueExample{
    public static void main(String[] args){
        byte var1 = 125;
        int var2 = 125;

        for(int i=0; i<5; i++){
            var1++;
            var2++;
            System.out.println("var1: "+var1+"\t"+"var2: "+var2);
        }
    }
}
```

```
var1: 126   var2: 126
var1: 127   var2: 127
var1: -128  var2: 128
var1: -127  var2: 129
var1: -126  var2: 130
```
실행 결과
{:.figcaption}

- **char 타입**   
자바는 모든 문자를 유니코드(Unicode: 세계 각국의 문자들을 코드값으로 매핑한 국제 표준 규약)로 처리한다. 유니코드는 하나의 문자에 대해 하나의 코드값을 부여하기 때문에 영문 'A' 및 한글 '가'도 하나의 코드값을 갖는다. 유니코드는 0～65535범위의 2byte 크기를 가진 정수값이다.    

    [유니코드에 대한 자세한 정보 참고](https://home.unicode.org/)   
    0～127 : 아스키(ASCII)문자 (특수기호 및 영어 알파벳)   
    44032～55203: 한글 11172자   
    {:.note}

    자바는 하나의 유니코드를 저장하기 위해 2byte 크기인 char 타입을 제공한다. 유니코드는 음수가 없기 때문에 char 타입의 변수에는 음수 값을 저장할 수 없다. char 타입에 저장할 수 있는 값은 0~65535까지 $$2^{16}$$개이다. char타입 변수에 작은따옴표`'`로 감싼 문자를 대입하면 해당 문자의 유니 코드가 저장된다.
```java
char var1 = 'A';    //유니코드: 0x0041 => 2진수 00000000 01000001
char var2 = 'B';    //유니코드: 0x0042 => 2진수 00000000 01000010
char var3 = '가';   //유니코드: 0xAC00 => 2진수 10101100 00000000
char var4 = '각';   //유니코드: 0x0041 => 2진수 10101100 00000001
```
char 변수에 작은따옴표로 감싼 문자가 아니라 직접 유니코드 정수값을 저장할 수도 있다.
```java
char c = 65;
char c = '\u0041';
```
char 타입변수를 int 타입 변수에 저장하면 char 타입 변수에 저장된 유니코드를 알 수 있다.
```java
char c = 'A';
int uniCode = c;
```
```java
public class CharExample{
    public static void main(String[] args){
        char c1 = 'A';      // 문자를 직접 저장
        char c2 = 65;       // 10진수로 저장
        char c3 = '\u0041'; // 16진수로 저장
        int uniCode = c1;

        System.out.println(c1);
        System.out.println(c2);
        System.out.println(c3);
        System.out.println(uniCode);
    }
}
```

```
A
A
A
65
```
실행 결과
{:.figcaption}

char 타입 변수는 단 하나의 문자만 저장한다. 만약 문자열을 저장하고 싶다면 String 타입을 사용하고 큰따옴표`"`로 감싼 문자열 리터럴을 대입하면 된다.
{:.note}
```java
String name = "홍길동";
```
char 타입의 변수에 어떤 문자를 대입하지 않고 단순히 초기화를 할 목적으로 빈(empty) 문자를 대입하면 컴파일 에러가 발생한다. 그렇기 때문에 공백(유니코드:32) 하나를 포함해서 초기화해야한다.
```java
char c = '';    // 컴파일 에러 
char c = ' ';
```

String 변수는 빈문자를 대입해도 괜찮다.
{:.note}
```java
String str="";
```

- **short 타입**   
short 타입은 2byte(16bit)로 표현되는 정수값을 저장할 수 있는 데이터 타입니다. 저장 할 수 있는 값의 범위는 -32,768～32,767($$-2^{31}$$～($$2^{31}-1$$))이다. 

C언어와의 호환을 위해 사용되며 자바에서는 비교적 잘 사용하지 않는 타입이다.
{:.note}

- **int 타입**
int 타입은 4byte(32bit)로 표현되는 정수값을 저장할 수 있는 데이터 타입이다. 저장할 수 있는 값의 범위는 -2,147,483,648～2,147,483,647($$-2^{31}$$～$$(2^{31}-1)$$)이다. int 타입은 자바에서 정수 연산을 하기위한 기본 타입이로 byte터압 또는 short 타입의 변수를 연산하면 int 타입으로 변환된 후 연산되고 연산의 결과 역시 int 타입이 된다. 이것은 자바에서 정수 연산을 4byte로 처리하기 때문이다. 따라서 byte타입이나 short타입으로 변수를 선언한 것과 int 타입으로 변수를 선언한 것의 성능 차이는 거의 없다.   
정수값을 직접 코드에서 입력할 경우 8진수, 10진수, 16진수로 표현 할 수 있다.
```java
public class IntExample{
    public static void main(String[] args){
        int number = 10;        // 10진수로 저장
        int octNumber = 012     // 8진수로 저장
        int hexNumber = 0xA;    // 16진수로 저장

        System.out.println(number);
        System.out.println(octNumber);
        System.out.println(hexNumber);
    }
}
```

```
10
10
10
```
실행 결과
{:.figcaption}

int가 4byte의 크기를 가지기 때문에 변수에 어떤 진수로 입력을 하더라도 동일한 값이 2진수로 변환되어 총 32bit로 메모리에 저장된다.   
![10이 저장된 int 타입의 메모리](/assets/img/live-study/intTypeMemory.png){: width="80%" height="80%"}

- **long 타입**   
long 타입은 8byte(64bit)로 표현되는 정수밗을 저장할수 있는 데이터 타입이다. 저장할 수있는 값의 범위는 $$-2^{63}$$～$$(2^{63}-1)$$로 수치가 큰 데이터를 다루는 프로그램에서는 long 타입이 필수적으로 사용된다. long타입의 변수를 초기화 할 때에는 정수값 뒤에 l이나 L을 붙일수 있다. 이것은 4byte 정수 데이터가 아니라 8byte 정수 데이터임을 컴파일러에게 알려주기 위함이다. 
```java
public class LongExample{
    public static void main(String[] args){
        long var1 = 10;
        long var2 = 20L;
        //long var3 = 10000000000000;       //컴파일 에러(The literal 10000000000000 of type int is out of range)
                                            //int 타입의 저장범위를 넘어서는 정수 리터럴에 L을 붙이지 않았기 때문
        long var4 = 10000000000000L;

        System.out.println(var1);
        System.out.println(var2);
        System.out.println(var3);
    }
}
```

```
10
20
10000000000000
```
실행 결과
{:.figcaption}

#### 실수 타입(float, double)
실수 타입은 소수점이 있는 실수 데이터를 저장할 수 있는 타입으로, 메모리 사용 크기에 따라 float과 double이 있다.

실수 타입|float|double
:---|:---|:---
바이트수|4|8
float과 double의 메모리 사용 크기는 각각 int, long의 크기와 같지만, 정수 타입과는 다른 저장 방식때문에 정수보다 훨씬 더 큰 범위의 값을 저장할 수 있다. 실수는 정수와 달리 부동 소수점(floating-point)방식으로 저장된다.  
![floating-point 방식](/assets/img/live-study/floating-point.png){: width="50%" height="50%"}   
가수 m은 0≤ m ＜1 범위의 실수이어야 한다. 1.2345 => 0.12345×$$10^1$$
![float과 double의 비트 사용](/assets/img/live-study/usingBit.png){: width="80%" height="80%"}   
float보다 double이 가수 표현에 있어서 많은 자릿수가 배정되어 있어서 더 정밀한 값을 저장할 수 있다. 따라서 높은 정밀도를 요구하는 계산에서는 double을 이용해야 한다. 자바는 실수 리터럴의 기본타입을 double로 간주한다. 실수 리터럴을 float타입 변수에 저장하려면 리터럴 뒤에 f나 F를 붙여야한다.
```java
double var1 = 3.14;
float var2 = 3.14;  //컴파일에러(Type mismatch: cannot convert from double to float)
float var3 = 3.14F;
```
정수 리터럴이 10의 지수를 나타내는 E나 e를 포함하고 있으면 실수 타입에 저장해야 한다. 
```java
int var4 = 3000000; //3000000
double var5 = 3e6;  //3000000
float var6 = 3e6f;  //3000000
double var7 = 2e-3; //0.002 
```

#### 논리 타입(boolean)
boolean 타입은 1byte(8bit)로 표현되는 논리값(true, false)을 저장할 수 있는 데이터 타입이다. 두가지 상태값을 저장할 필요가 있을 경우에 사용되며, 상태값에 따라 조건문과 제어문의 실행흐름을 변경하는데 주로 이용된다.
```java
public class BooleanExample{
    public static void main(String[] args){
        boolean stop = true;
        
        if(stop){
            System.out.println("중지합니다.")
        } else{
            System.out.println("시작합니다.")
        }
    }
}
```

```
중지합니다.
```
실행 결과
{:.figcaption}

### 타입 변환   
타입변환 : 데이터 타입을 다른 데이터 타입으로 변환하는 것
- **자동(묵시적) 타입 변환**   
자동 타입 변환(Promotion)은 프로그램 실행 도중에 자동적으로 타입 변환이 일어나는 것을 말하며 작은 크기를 가지는 타입이 큰 크기를 가지는 타입에 저장될 때 발생한다.   
`byte(1) < short(2) < int(4) < long(8) < float(4) < double(8)`

표현 할수 있는 값의 범위가 float가 더 크기 때문에 `long(8) < float(4)`이다.
{:.note}
```java
byte byteValue = 10;
int intValue = byteValue;   //자동 타입 변환 발생
```
![자동 타입 변환](/assets/img/live-study/promotion.png/){: width="80%" height="80%"}   
자동 타입 변환이 발생되면 변환 이전의 값과 변환 이후의 값은 동일하게 손실없이 그대로 보존된다. 정수 타입이 실수 타입으로 변환하는 것은 무조건 자동 타입변환이 된다. 실수 타입으로 변환된 이후의 값은 정수값이 아닌 .0이 붙은 실수값이 된다.
```java
int intValue = 200;
double doubleValue = intValue;  //200.0
```
char 타입의 경우 int 타입으로 자동 변환 되면 유나코드값이 int 타입에 저장된다.
```java
char charValue = 'A';
int intValue = charValue;   //65
```
자동 타입 변환에서 단 하나의 예외가 있는데, char는 2byte의 크기를 가지지만, char의 범위는 0~65535이므로 음수가 저장될 수 없다. 따라서 음수가 저장될 수 있는 byte타입을 char타입으로 자동 변환시킬 수 없다.
```java
byte byteValue = 65;
char charValue = byteValue;     // 컴파일 에러
char charData = (char)byteValue;// 강제 타입 변환
```

- **강제(명시적) 타입 변환**     
큰 크기의 타입은 작은 크기의 타입으로 자동 타입 변환을 할 수 없다. 강제적으로 큰 데이터 타입을 작은 데이터 타입으로 조개어서 저장하는 것을 **강제 타입 변환(캐스팅:Casting)** 이라고 한다. 강제 타입 변환은 캐스팅 연산자()를 사용하는데, 괄호 안에 들어가는 타입은 쪼개는 단위이다.
```java
int intValue = 103029110;
byte byteValue = (int)intValue; // 강제 타입 변환(캐스팅)
```
![강제 타입 변환](/assets/img/live-study/casting.png/){: width="80%" height="80%"}   
4byte의 int 타입을 강제적으로 (byte)연산자를 사용해서 1byte씩 쪼개고, 끝에 있는 1byte만 저장하므로 원래 int값은 보존되지 않는다. 하지만 int값이 끝 1byte만으로만 표현이 가능하다면 byte타입으로 변환해도 같은 값이 유지될 수 있다.
```java
long longValue = 300;
int intValue = (int)longValue;      // 끝 4byte로 표현할 수 있기 때문에 300 그대로 유지
```
```java
int intValue = 'A';                 //65 저장
char charValue = (char)intValue;    //A
```
```java
double doubleValue = 3.14;
int intValue = (int)doubleValue;    //3
```

강제 타입 변환은 사용자로부터 입력받은 값을 변환할 때 값의 손실이 발생하면 안된다. 강제 타입 변환을 하기전에 우선 안전하게 값이 보존될 수 있는지 검사하는 것이 좋다.
{:.note title="Attention"}
```java
public class CheckValueBeforeCasting{
    public static void main(String[] args){
        int i = 128;

        if((i<Byte.MIN_VALUE) || (i>Byte.MAX_VALUE)){
            System.out.println("byte 타입으로 변환할 수 없습니다.");
            System.out.println("값을 다시 확인해 주세요");
        } else{
            byte b = (byte)i;
            System.out.println(b);
        }
    }
}
```

```
byte 타입으로 변환할 수 없습니다.
값을 다시 확인해 주세요
```
실행 결과
{:.figcaption}

실수타입을 정수타입으로 강제 타입 변환 할 때 정밀도 손실을 피해야한다. 
{:.note title="Attention"}
```java
int num1 = 123456780;
int num2 = 123456780;

float num3 = num2;
double num4 = num2

num2 = (int)num3;
System.out.pritnln(num1-num2);  //-4

num2 = (int)num4;
System.out.pritnln(num1-num2);  //0
```
int 값을 손실 없이 float타입의 값으로 변할 수 있으려면 가수 23비트로 표현 가능한 값이어야 한다. 123456780은 23비트로 표현할 수 없기 때문에 근사치로 변환되어 정밀도 손실이 발생한다. double의 가수는 52비트로 int의 크기 32bit보다 크기때문에 어던한 int 값이라도 안전하게 정밀도 손실없이 double 타입으로 변환될 수 있다.   

- **연산식에서의 자동 타입 변환**   
연산은 기본적으로 같은 타입의 피연산자(operand) 간에만 수행되기 때문에 서로 다른 타입의 피연산자가 있을 경우 두 피연산자 중 크기가 큰 타입으로 자동 변환된 후 연산을 수행한다.
```java
int intValue = 10;
double doubleValue = 5.5;
double result1 = intValue + doubleValue;    // 10.0+5.5 = 15.5 , 자동 타입 변환
int result2 = intValue + (int)doubleValue;  // 10+5 = 15, 결과값을 int로 해야한다면 강제 타입 변환
```
자바는 정수 연산일 경우 int타입을 기본으로 한다. 그 이유는 피연자를 **4byte 단위**로 저장하기 때문이다. 크기가 4byte보다 작은 타입은 4byte인 int 타입으로 변환 후 연산이 수행된다.
```java
char ai = 'A';
int result = ai + 1;    //'A'의 유니코드보다 1이 큰 유니코드가 저장
char ni = (char)result; //'B'가 저장됨
```
만약 피연산자 중 하나가 long 타입이라면 다른 연산자도 long 타입으로 자동 타입 변환 되고 연산 결과는 long 타입이 된다.   
float타입과 float을 연산하면 연산의 결과는 float타입으로 나오지만, 피연산자 중에 실수 리터럴이나 double 타입이 있다면 다른 피연산자도 double 타입으로 변환 타입 변환되어 연산되므로 결과는 double 타입으로 산출된다.
```java
public class OperationsPromotionExample{
    public static void main(String[] args){
        byte byteValue1 = 10;
        byte byteValue2 = 20;
        //byte byteValue3 = byteValue1 + byteValue2;    //컴파일 에러
        int intValue1 = byteValue1+byteValue2;
        System.out.println(intValue1);

        char charValue1 = 'A';
        char charValue2 = 1;
        //char charValue3 = charValue1 + charValue2;    //컴파일 에러
        int intValue2 = charValue1+charValue2;
        System.out.println("유니코드="+intValue2);
        System.out.println("출력문자="+(char)intValue2);

        int intValue3 = 10;
        int intValue4 = intValue3 / 4;
        System.out.println(intValue4);

        int intValue5 = 10;
        //int intValue6 = intValue5 / 4.0;              //컴파일 에러
        double doubleValue = intValue5 / 4.0;
        System.out.println(doubleValue);
    }
}
```

```
30
유니코드=66
출력문자=B
2
2.5
```
실행 결과
{:.figcaption}



### 참조타입
자바의 데이터 타입에는 크게 기본타입 (원시타입:primitive type)과 참조 타입(reference type)으로 분류된다. 
![데이터타입 분류](/assets/img/live-study/dataType.png){: width="60%" height="60%"}   
참조타입이란 객체(Object)의 번지를 참조하는 타입으러 배열, 열거, 클래스, 인터페이스타입을 말한다. 기본타입과 참조타입으로 선언된 변수의 차이점은 저장되는 값이 무엇이냐이다. 기본타입을 이용해서 선언된 변수는 실제 값을 변수안에 저장하지만, **참조타입을 이용해서 선언된 변수는 메모리의 번지를 값으로 갖는다.** 번지를 통해 객체를 참조한다는 뜻에서 참조타입이라고 부른다.
```java
/*기본 타입 변수*/
int age = 25;
double price = 100.5;

/*참조 타입 변수*/
String name = "홍길동";
String hobby = "독서";
```
![데이터 타입 메모리](/assets/img/live-study/dataTypeMemory.png){: width="70%" height="70%"}   
기본타입변수는 직접 값을 저장하고 있지만, 참조변수는 힙 영역의 객체 주소 값을 가지고 있다. 
- **참조 변수의 ==, != 연산**   
기본 타입 변수의 ==, != 연산은 변수의 값이 같은지, 아닌지를 조사하지만 참조 타입 변수들 간의 ==, != 연산은 동일한 객체를 참조하는지, 다른 객체를 참조하는지 알아볼때 사용된다. 참조 타입 변수의 값인 힙영역의 객체 주소를 비교하는 것이 된다.    
![참조 타입 메모리](/assets/img/live-study/referenceTypeMemory.png){: width="70%" height="70%"}     

```java
refVar1 == refVar2  //false
refVar1 != refVar2  //true

refVar2 == refVar3  //true
refVar2 != refVar3  //false
```

- **null과 NullPointerExeption**   
참조타입변수는 힙 영역의 객체를 참조하지 않는다는 뜻으로 null(널) 값을 가질 수 있다. null값도 초기값으로 사용할 수 있기 때문에 null로 초기화된 참조변수는 스택 영역에 생성된다.
![null 메모리](/assets/img/live-study/nullMemory.png){: width="70%" height="70%"}     

```java
refVar1 == null  //false
refVar1 != null  //true

refVar2 == null  //true
refVar2 != null  //false
```
자바는 프로그램 실행 중에 발생하는 오류를 예외(Exception)라고 부른다. 예외는 사용자의 잘못된 입력으로 발생 할 수도 있고, 프로그래머가 코드를 잘못 작성해서 발생 할 수도 있다. 참조 변수를 사용하면서 가장 많이 발생하는 예외중 하나로 `NullPointerException`이 있다. 이 예외는 null을 가지고 있는 참조 타입 변수를 사용하려고 할 때 발생한다. 참조 타입 변수를 사용하는 것은 곧 객체를 사용하는 것을 의미하는데 참조할 객체가 없으므로 사용할 수 없는 것이다.
```java
int[] intArray = null;
intArray[0] = 10;       //NullPointerException
```
- **String 타입**   
자바는 문자열을 String 변수에 저장하기 때문에 다음과 같이 String 변수를 우선 선언해야 한다.
```java
String str;
```
String 변수에 문자열을 저장하려면 큰따옴표로 감싼 문자열 리터럴을 대입하면 된다.
```java
str ="문자열";
```
변수선언과 동시에 문자열을 저장할 수도 있다.
```java
String str = "문자열";
```
**사실 String변수에 문자열을 저장한다는 말은 틀린 표현이다.** 문자열이 직접 변수에 저장되는 것이 아니라, 문자열은 String 객체로 생성되고 변수는 String 객체를 참조한다. 자바는 문자열 리터럴이 동일하다면 String객체를 공유하도록 되어있다. 
```java
String name1 = "홍길동";
String name2 = "홍길동";
```
![String메모리](/assets/img/live-study/stringMemory.png){: width="70%" height="70%"}     
일반적으로 변수에 문자열을 저장 할 경우에는 문자열 리터럴을 사용하지만, **new 연산자**를 사용해서 직접 String 객체를 생성 시킬 수도 있다.

new 연산자는 힙영역에 새로운 객체를 만들때 사용하는 연산자로 객체 생성 연산자라고한다.
{:.note}
```java
String name1 = new String("홍길동");
String name2 = new String("홍길동");
```
![String메모리](/assets/img/live-study/stringMemory2.png){: width="70%" height="70%"}   

문자열 리터럴로 생성하느냐 new 연산자로 생성하느냐에 따라 비교연산자의 결과가 달라질 수 있다.
```java
public class StringEqualsExample{
    public static void main(String[] args){
        String strVar1 = "홍길동";
        String strVar2 = "홍길동";

        if(strVar1 == strVar2){
            System.out.println("strVar1과 strVar2는 참조가 같음");
        } else{
            System.out.println("strVar1과 strVar2는 참조가 다름");
        }

        if(strVar1.eqauls(strVar2)){
            System.out.println("strVar1과 strVar2는 문자열이 같음");
        }

        String strVar3 = new String("홍길동");
        String strVar4 = new String("홍길동");

        if(strVar3 == strVar4){
            System.out.println("strVar3과 strVar4는 참조가 같음");
        } else{
            System.out.println("strVar3과 strVar4는 참조가 다름");
        }

        if(strVar3.eqauls(strVar4)){
            System.out.println("strVar3과 strVar4는 문자열이 같음");
        }
    }
}
```

```
strVar1과 strVar2는 참조가 같음
strVar1과 strVar2는 문자열이 같음
strVar3과 strVar4는 참조가 다름
strVar3과 strVar4는 문자열이 같음
```
실행 결과
{:.figcaption}

- **배열 타입**   
배열 : 같은 타입의 데이터를 연속된 공간에 나열시키고, 각 데이터에 인덱스(index)를 부여해 놓은 자료구조. 배열의 인덱스는 각 항목의 데이터를 읽거나 저장하는데 사용되며 배열 이름 옆에 대괄호[]에 기입된다. **배열은 같은 타입의 데이터만 저장할 수 있고 한번 생성된 배열은 길이를 늘리거나 줄일 수 없다.** `타입[] 변수;`또는 `타입 변수[];`의 형태로 선언할 수 있다.

배열 변수는 참조변수로 배열도 객체미으로 힙영역에 생성되고 배열 변수는 배열 객체를 참조하게 된다. 참조 할 배열이 없다면 배열 변수는 null값으로 초기화 될 수 있으며 이때 변수[인덱스]로 값을 읽거나 저장하게되면 `NullPointerException`이 발생한다.

- **값 목록으로 배열 생성**   
`데이터타입[] 변수 = {값0, 값1, 값2, 값3, ...};` 형태로 중괄호{}는 주어진 값들을 항목으로 가지는 배열 객체를 힙에 생성하고, 배열 객체의 번지를 리턴한다. 배열 변수는 리턴된 번지를 저장함으로써 참조가 이루어진다.
```java
String[] names = {"홍길동", "이몽룡", "박문수"};
```
![배열메모리](/assets/img/live-study/arrayMemory.png){: width="70%" height="70%"}   

```java
public class ArrayCreateByListExample{
    public static void main(String[] args){
        int[] scores = {83, 90, 87};

        System.out.println("scores[0] : " + score[0]);
        System.out.println("scores[1] : " + score[1]);
        System.out.println("scores[2] : " + score[2]);

        int sum = 0;
        for(int i=0; i<3; i++){
            sum += scores[i];
        }
        System.out.println("총합 : " + sum);
        double avg = (double)sum/3;
        System.out.println("평균 : " + avg);
    }
}
```

```
scores[0] : 83   
scores[1] : 90   
scores[2] : 87   
총합 : 260   
평균 : 86.66666666666667   
```
실행 결과
{:.figcaption}

배열 변수를 이미 선언한 후에 다른 실행문에서 중괄호를 사용한 배열 생성은 허용되지 않는다. 메소드의 매개값이 배열일 경우도 마찬가지이다.

```java
int[] scores = null;
scores = {83, 90, 87};          //컴파일 에러
scores = new int[]{83, 90, 87};

int add(int[] scores){...}
int result = add({83, 90, 87}); //컴파일 에러
int result = add(new int[]{83, 90, 87});
```

- **new 연산자로 배열 생성**   
값의 목록을 가지고 있지 않을 때, 배열을 만들고 싶다면 `타입[] 변수 = new 타입[길이]`의 형태로 선언이 가능하다. 길이는 배열이 저장할 수 있는 값의 개수를 말한다. 

```java
int[] array = new int[5]; //길이가 5인 int[]배열을 생성
```   
![배열메모리](/assets/img/live-study/arrayMemory2.png){: width="70%" height="70%"}   
new 연산자로 배열을 처음 생성할 경우, 배열은 자동적으로 기본값으로 초기화된다.   

|분류|데이터 타입|초기값
|:-----------------|:-------|:----
|기본 타입(정수)    |btye[]   |0
|                  |char[]   |'\u0000'
|                  |short[]  |0
|                  |int[]    |0
|                  |long[]   |0L
|기본 타입(실수)    |float[]  |0.0f
|                  |double[] |0.0
|기본 타입(논리)    |boolean[]|false
|참조 타입          |클래스[] |null
|                  |인터페이스[]|null

배열의 길이를 얻으려면 배열 객체의 length 필드를 읽으면 된다. `배열변수.length`
```java
public class ArrayCreateByNewExample{
    public static void main(String[] args){
        int[] arr1 = new int[3];
        for(int i=0; i<arr1.length; i++){
            System.out.println("arr1["+i+"] : " + arr1[i]);
        }
        for(int i=1; i<=arr1.length; i++){
            arr1[i] = i*10;
        }
        for(int i=0; i<arr1.length; i++){
            System.out.println("arr1["+i+"] : " + arr1[i]);
        }

        String[] arr2 = new int[3];
        for(int i=0; i<arr2.length; i++){
            System.out.println("arr2["+i+"] : " + arr2[i]);
        }
        for(int i=1; i<=arr2.length; i++){
            arr2[i] = i+"월";
        }
        for(int i=0; i<arr2.length; i++){
            System.out.println("arr2["+i+"] : " + arr2[i]);
        }
    }
}
```

```
arr1[0] : 0
arr1[1] : 0
arr1[2] : 0
arr1[0] : 10
arr1[1] : 20
arr1[2] : 30
arr2[0] : null
arr2[1] : null
arr2[2] : null
arr2[0] : 1월
arr2[1] : 2월
arr2[2] : 3월
```
실행 결과
{:.figcaption}

- 커맨드 라인 입력 `public static void main(String[] args){...}`   
`java 클래스`로 프로그램을 실행하면 JVM은 길이가 0인 String 배열을 먼저 생성하고 `main()` 메소드를 호출할 때 매개값으로 전달한다. `java 클래스 문자열1 문자열2 ... 문자열n-1`처럼 뒤에 문자열 목록을 주고 실행하면, 문자열 목록읋 구성된 String[] 배열이 생성되고 `main()` 메소드를 호출할 때 매개값으로 전달한다. `main()` 메소드는 `String[] args` 매개변수를 통해서 커맨드 라인에 입력된 데이터의 수(배열의 길이)와 입력된 데이터(배열의 항목 값)를 알 수 있게 된다.

```java
public class MainStringArrayArgument{
    public static void main(String[] args){
        if(args.length != 2){
            System.out.println("프로그램의 사용법");
            System.out.println("java MainStringArrayArgument num1 num2");
            System.exit(0); //강제종료
        }

        String strNum1 = args[0];
        String strNum2 = args[1];

        int num1 = Integer.parseInt(strNum1);   //문자열을 정수로 변환
        int num2 = Integer.parseInt(strNum2);

        int result = num1 + num2;
        System.out.println(num1+" + "+num2+" = "+result);
    }
}
```
`java MainStringArrayArgument`
```
프로그램의 사용법
java MainStringArrayArgument num1 num2
```
실행 결과1
{:.figcaption}

`java MainStringArrayArgument 10 20`
```
10 + 20 = 30
```
실행 결과2
{:.figcaption}


- **다차원 배열**  
행과 열로 구성된 배열은 2차원 배열이라고 한다. 수학의 행렬을 떠올리면 되는데, 가로 인덱스와 세로 인덱스를 사용한다. 자바는 2차원 배열을 중첩 배열 방식으로 구현 한다. 
```java
int[] scores = new int[2][3];  //2x3 행렬구조의 배열
```
![배열메모리](/assets/img/live-study/arrayInArrayMemory.png){: width="70%" height="70%"}   

```java
scores.length       // 2
scores[0].length    // 3
scores[1].length    // 3
```

자바는 일차원 배열이 서로 연결된 구조로 다차원 배열을 구현하기 때문에 수학 행렬구조가 아닌 계단식 구조를 가질수 있다.   
```java
int[] scores = new int[2][];
socres[0] = new int[2];
socres[1] = new int[3];

scores.length       // 2
scores[0].length    // 2
scores[1].length    // 3
```

이런 형태의 배열에서 주의 할 점은 정확한 배열의 길이를 알고 인덱스를 사용해야 한다. 유효하지 않은 인덱스로 배열에 접근하면 `ArrayIndexOutOfBoundsException`을 발생시킨다. 값의 목록을 가지고 있다면 중괄호를 사용해 값 목록을 나열해 다차원 배열을 선언할 수 있다.

```java
{% raw %}int[][] scores = {{95, 80}, {92, 96}};{% endraw %}
```

- **객체를 참조하는 배열**   
```java
String[] array = new String[3];
array[0] = "Java";
array[1] = "C++";
array[2] = "C#";
```

![2차원배열메모리](/assets/img/live-study/referenceTypeArrayMemory.png){: width="70%" height="70%"}   

```java
String[] array = new String[3];
array[0] = "Java";
array[1] = "Java";
array[2] = new String("Java");

array[0] == array[1]        //true
array[0] == array[2]        //false
array[0].equals(array[2])   //true
```

![2차원배열메모리](/assets/img/live-study/referenceTypeArrayMemory2.png){: width="70%" height="70%"}   

- 배열 복사
배열은 한번 생성하면 크기를 변경할 수 없기 때문에 더 많은 저장 공간이 필요하다면 보다 큰 배열을 새로 만들고 이전 배열로부터 항목값들을 복사해야 한다. 또는 `System.arraycopy(Object src, int srcPos, Object dest, int destPos, int length);` 메소드를 이용할 수 있다.

`src`: 원본 배열   
`srcPos`: 원본 배열에서 복사할 항목의 시작 인덱스    
`dest`: 새 배열    
`destPos`: 새 배열에 붙여넣을 시작 인덱스    
`length`: 복사할 개수   
{:.note}

```java
public class ArrayCopyExample{
    public static void main(String[] args){
        int[] oldIntArray = {1,2,3};
        int[] newIntArray1 = new int[5];
        int[] newIntArray2 = new int[5];

        for(int i=0; i<oldIntArray.length; i++){
            newIntArray1[i] = oldIntArray[i];
        }
        for(int 0; i<newIntArray1.length; i++){
            System.out.print(newIntArray[i]+", ");
        }

        System.arraycopy(oldIntArray, 0, newIntArray2, 0, oldIntArray.length);
    }
}
```
참조 타입 배열의 경우, 배열 복사가 되면 복사되는 값이 객체의 주소이므로 새 배열의 항목은 이전 배열의 항목이 참조하는 객체와 동일하다. 이것을 **얕은 복사(shallow copy)**라고 한다. 반대로 참조하는 객체도 별도로 생성하는 것을 **깊은 복사(deep copy)**라고 한다.

- 향상된 for문   
자바5부터 배열 및 컬렉션 객체를 좀더 쉽게 처리할 목적으로 향상된 for문을 제공한다.

```java
int[] scores = {95, 71, 84, 93, 87};
for(int score: scores){ //for(타입변수 : 배열)
    sum = sum + score;
}
```

- 타입 추론
타입 추론(type-inference) :개발자가 변수의 타입을 명시적으로 적어주지 않아도 컴파일러가 알아서 이 변수의 타입을 대입된 리터럴로 추론하는 것. 

자바 10 부터 제공
{:.note}

변수를 선언할 때 타입을 명시하지 않고 var를 이용해서 선언할 수 있다. 그리고 컴파일 시점에 컴파일러가 초기값 리터럴로 타입을 추론한다.
```java
var str = "Hello";
if(str instanceof String){ //str가 어떤 String타입의 변수인지 검사 true
    System.out.println("str변수의 타입은 String 입니다.");
}
```
var로 선언된 변수는 초기값이 있는 로컬 변수로만 선언이 가능하다. 멤버변수, 메소드의 파라미터, 리턴 타입으로는 사용이 불가능하다. var는 키워드가 아니다. 즉, 어떠한 타입도 아니고, 클래스에서 사용할 수 있는 예약어가 아니다. 따라서 int를 변수 이름으로 만들 수는 없지만, var 라는 문자를 변수로 사용할 수 있다. 컴파일러가 자바 소스를 바이트 코드로 변경할 때, 모든 var를 초기값으로 타입을 추론해서 바이트코드에는 타입을 명시적으로 표시해 놓기때문에 타입 추론 변수를 읽을 때 마다 타입을 알아내기위한 연산을 하지 않는다. var로 선언된 변수는 중간에 타입이 변경되지 않는다.

```java
public Class TypeInferenceExample{
    //private var str = "error";  //컴파일 에러, 멤버변수
    public static void main(String[] args){
        //var add(var num1, num2){...} //컴파일 에러, 메소드의 파라미터, 리턴 타입
        //var str;  //컴파일 에러, 초기값X
        //var str = null;  //컴파일 에러, 초기값은 null일수 없다.
        //var arr = {1,2,3} //컴파일 에러, 배열을 선언 할 수 없다.
        
        int var; 
        var typeInf = 1;
        //typeInf = "문자열로 변경";    //컴파일 에러, 중간에 타입을 변경할 수 없다.
    }
}
```

Refernce
- [이것이 자바다 - 신용권의 Java 프로그래밍 완전 정복](http://www.yes24.com/Product/Goods/15651484)
- [https://catch-me-java.tistory.com/19](https://catch-me-java.tistory.com/19)