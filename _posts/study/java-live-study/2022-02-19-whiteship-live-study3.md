---
layout: post
title: "[Java] 연산자"
tags: java live-study operator
image: 
    path: /assets/img/live-study/live-study3-cover.png
accent_color: '#00B8A9'
description: >
    [dev-ujin✨](https://github.com/dev-ujin)과 함께하는 [live study📝](https://github.com/whiteship/live-study) 3주차
categories:
    - study
    - java-live-study
related_posts:    
    - /study/java-live-study/2022-02-06-whiteship-live-study1/  
    - /study/java-live-study/2022-02-13-whiteship-live-study2/    
---

### [Java] 연산자  

## 1. 연산자와 연산식
- **연산(operations)** : 프로그램에서 데이터를 처리해서 결과를 산출하는 것  
- **연산자(operator)** : 연산에 사용되는 표시나 기호  
- **피연산자(operand)** : 연산되는 데이터  
- **연산식(expressions)** : 연산자와 피연산자를 이용하여 연산의 과정을 기술한 것  

다음 연산식에서 `+`, `-`, `*`, `==`은 연산자이고, `x`,`y`,`z` 변수는 피연산자이다. 

```java
x + y
x - y
x * y + z
x == y
```

- **연산자들은 피연산자를 연산해서 값을 산출하는데, 산출되는 값의 타입은 연산자별로 다르다.**  

|연산자 종류|연산자|피연산자 수|산출값|기능 설명|
|---|---|---|---|---|
|산술|`+`, `-`, `*`, `/`, `%`|이항|숫자|사칙연산 및 나머지 계산|
|부호|`+`, `-`|단항|숫자|음수와 양수의 부호|
|문자열|`+`|이항|문자열|두 문자열을 연결|
|대입|`=`, `+=`, `-=`, `*=`, `/=`, `%=`, `&=`, `^=`, `!=`, `<<=`, `>>=`, `>>>=`|이항|다양|우변의 값을 좌변의 변수에 대입|
|증감|`++`, `--`|단항|숫자|1만큼 증가/감소|
|비교|`==`, `!=`, `>`, `<`, `>=`, `<=`, `instanceof`|이항|`boolean`|값의 비교|
|논리|`!`, `&`, `|`, `&&`, `||`| 단항, 이항|`boolean`|논리적 NOT, AND, OR 연산|
|조건|`(조건식)?A:B`|삼항|다양|조건식에 따라 A 또는 B 중 하나를 선택|
|비트|`~`, `&`, `|`, `^`|단항, 이항|숫자, `boolean`|비트 NOT, AND, OR, XOR 연산|
|쉬프트|`<<`,`>>`,`>>>`|이항|숫자|비트를 좌측/우측으로 밀어서 이동|


- **연산자는 필요로 하는 피연산자의 수에 따라 단항, 이항, 삼항 연산자로 구분된다.**   
    - 단항 연산자 : 부호 연산자와 증가/감소 연산자는 피연산자 하나만을 요구   
    - 삼항 연산자 : 조건 연산자는 조건식, A, B와 같이 세 개의 피연산자가 필요   
    - 이항 연산자 : 그 이외의 연산자는 두 개의 피연산자를 요구   


- **연산식은 반드시 하나의 값을 산출한다.**   
연산자 수가 아무리 많아도 두개 이상의 값을 산출하는 연산식은 없다. 그렇기 때문에 하나의 값이 올 수 있는 곳이면 어디든지 값 대신에 연산식을 사용할 수 있다. 보통 연산식의 값은 변수에 저장하는데, 다음과 같이 `x`와 `y` 변수의 값을 더하고 나서 `result` 변수에 저장한다.

```java
int result = x + y;
```

- **연산식은 다른 연산식의 피연산자 위치에도 올 수 있다.**    
다음과 같이 비교 연산인 `<` 의 좌측 피연산자 `(x + y)`라는 연산식이 사용되어, `x`와 `y`의 변수의 값을 더하고 나서 5보다 작은지 검사한 후 결과값 (`true` 혹은 `false`)을 변수 `result`에 저장한다.   

```java
boolean result = (x + y) < 5
```

## 2. 연산의 방향의 우선순위

| 연산자 | 연산 방향 | 우선순위 |
|--------|----------|---------|
|증감(`++`,`--`), 부호(`+`,`-`), 비트(`~`), 논리(`!`)|⬅️|높음|
|산술(`*`,`/`,`%`)|➡️|⬆️|
|산술(`+`,`-`)|➡️||
|쉬프트(`<<`,`>>`,`>>>`)|➡️||
|비교(`<`,`>`,`<=`,`>=`,`instanceof`)|➡️||
|비교(`==`,`!=`)|➡️||
|논리(`&`)|➡️||
|논리(`^`)|➡️||
|논리(`|`)|➡️||
|논리(`&&`)|➡️||
|논리(`||`)|➡️||
|조건(`?:`)|➡️|⬇️|
|대입(`=`,`+=`,`-=`,`*=`,`/=`,`%=`,`&=`,`^=`,`!=`,`<<=`,`>>=`,`>>>=`)|⬅️|낮음|
 
예제)   
>   ```java
    x > 0 && y < 0
    ```   
    1. `x > 0`과 `y < 0`   
    2. `&&`   


>   ```java
    100 * 2 / 3 % 5
    ```   
    1. `100*2`   
    2. `200 / 3`   
    3. `66 % 5`   

>   ```java
    a = b = c = 5;
    ```   
    1. `c=5`   
    2. `b=c`   
    3.`a=b`   

- **괄호`()`를 사용해서 먼저 처리해야 할 연산식을 묶는 것이 좋다.**   
괄호 부분 연산은 최우선순위를 갖기 때문에 다른 연산자보다 우선 연산된다.   

```java
int var1 = 1;
int var2 = 2;
int var3 = 3;

int result1 = var1 + var2 * var3;   // 7
int result2 = (var1 + var2) * var3; // 9
```

<success>
<strong>📝정리</strong><br>
&nbsp;&nbsp;&nbsp;&nbsp;1. 단항 > 이항 > 삼항<br>
&nbsp;&nbsp;&nbsp;&nbsp;2. 산술 > 비교 > 논리 > 대입 <br>
&nbsp;&nbsp;&nbsp;&nbsp;3. 단항, 대입의 연산 방향 ⬅️ / 그 외 ➡️ <br>
&nbsp;&nbsp;&nbsp;&nbsp;4. 최우선순위 : '()'<br>
</success>


## 3. 단항 연산자   
### 3.1 부호 연산자(`+`,`-`)
부호 연산자는 양수 및 음수를 표시하는 `+`, `-`를 말한다. `boolean`타입과 `char`타입을 제외한 나머지 기본 타입에 사용 할 수 있다.    

|연산식||설명|
|:-----:|---|-----|
|`+`|피연산자|피연산자 부호 유지|
|`-`|피연산자|피연산자 부호 변경|

`+`, `-`는 산술 연산자이기도 하고, 부호 연산자이기도 하다. 부호 연산자로 쓰일때에는 하나의 피연산자만 필요하다. 일반적으로 부호 연산자는 정수 및 실수 리터럴 앞에 붙여 양수 및 음수를 표현한다.

```java
int i1 = +100;
int i2 = -100;
double d1 = +3.14;
double d2 = -10.5;
```
부호연산자를 정수 또는 실수 타입 변수 앞에 붙일수도 있다. 이 경우는 변수를 양수 및 음수로 표현한 것이 아니고, 변수 값의 부호를 유지하거나 바꾸기위해 사용된다.   

```java
int x =100;
int result1 = +x;   //100
int result2 = -x;   //-100
```

#### 부호연산자의 산출타입은 `int`타입이다.   

```java
short s =100;
//short result = -s;  //컴파일 에러
int result = -s;  
```

### 3.2 증감 연산자(`++`,`--`)   
증감 연산자는 변수의 값을 1 증가(`++`)시키거나 1 감소(`--`)시키는 연산자를 말한다. `boolean`타입을 제외한 모든 기본타입의 피연산자에 사용할 수 있다.   

|연산식||설명|
|---|---|---|
|`++`|피연산자|다른 연산을 수행하기 전에 피연산자의 값을 1 증가시킴|
|`--`|피연산자|다른 연산을 수행하기 전에 피연산자의 값을 1 감소시킴|
|피연산자|`++`|다른 연산을 수행한 후에 피연산자의 값을 1 증가시킴|
|피연산자|`--`|다른 연산을 수행한 후에 피연산자의 값을 1 감소시킴|

#### 연산식에서 증감연산자만 있는 경우에는 증감연산자가 변수 앞 또는 뒤 어디든 위치해도 상관없다.

```java
++i;        // 둘 다 i = i+1;
i++;
```

```java
--i;        // 둘 다 i = i-1;
i--;
```
#### 다른 연산자와 함께 사용하는 연산식에서는 증감 연산자의 위치에 따라 연산식의 결과가 다르다.

```java
int x = 10;
int y = 10;
int z;

x++;
++x;
System.out.println(x);  //12

y--;
--y;
System.out.println(y);  //8

z = x++;
System.out.println(z);  //12
System.out.println(x);  //13

z = ++x;
System.out.println(z);  //14
System.out.println(x);  //14

z = ++x + y++;
System.out.println(z);  //23
System.out.println(x);  //15
System.out.println(y);  //9
```

많은 사람들이 `++i;`가 `i=i+1;`보다 연산 속도가 빠르다고 알고있다. 그 이유는 `i=i+1;`은 `=`연산자와 `+`연산자가 있기 때문에 두번의 연산이 필요하지만 `++`은 하나의 연산만 수행하기 때문이다. 하지만 `++i;`와 `i=i+1;`은 실제로 컴파일하면 동일한 바이트 코드가 생성된다. 그렇기 때문에 둘 중 **어떤것이 연산 속도가 빠르다고 할 수 없다.**   
{:.note}

### 3.3 논리 부정 연산자(`!`)
논리 부정 연산자는 `true`를 `false`로, `false`를 `true`로 변경하기 때문에 `boolean`타입에만 사용할 수 있다.   

|연산식||설명|
|---:|---|---|
|`!`|피연산자|피연산자가 `true`이면 `false`값을 산출<br>피연산자가 `false`이면 `true`값을 산출

논리부정 연산자는 조건문과 제어문에서 사용되어 조건식의 값을 부정하도록 해서 실행흐름을 제어할 때 주로 사용된다. 또한 두가지 상태(`true`, `false`)를 번갈아가며 변경하는 토글(toggle) 기능을 구현할 때도 주로 사용한다.  
{:.note}

```java
boolean play = true;
System.out.println(play);   //true

play = !play;
System.out.println(play);   //false

play = !play;
System.out.println(play);   //true
```

### 3.4 비트 반전 연산자(`~`)
비트 반전 연산자는 정수 타입(`byte`, `short`, `int`, `long`)의 피연산자에만 사용되며, 피연산자를 2진수로 표현했을 때 비트값인 `0`을 `1`로, `1`을 `0`으로 반전한다. 연산 후 부호 비트인 최상위 비트를 포함해서 모든 비트가 반전되기 때문에, 부호가 반대인 새로운 값이 산출된다.

|연산식||설명|
|---|---|---|
|~|피연산자|피연산자를 2진수로 표현했을 때 비트값인 0을 1로, 1을 0으로 반전|

```java
int x = 10;
x = ~x;     //-11
```
![10의 이진수](/assets/img/live-study/operator1.png){: width="70%" height="70%"}

> [이진수의 십진수변환 참고](/study/java-live-study/2022-02-13-whiteship-live-study2/#%EC%A0%95%EC%88%98-%ED%83%80%EC%9E%85byte-char-short-int-long)   

비트 반전 연산자의 산출 타입은 `int` 타입이다. 피연산자는 연산을 수행하기 전에 int타입으로 변환되고, 비트 반전이 일어난다. 

```java
byte v1 = 10;
//byte v2 = ~v1; //컴파일 에러
int v2 = ~v1;    //11
```

자바는 정수값을 총 32비트의 이진 문자열로 리턴하는 `Integer.toBinaryString()`메소드를 제공한다. `Integer.toBinaryString()`메소드는 앞의 비트가 모두 `0`이면 `0`은 생략되고 나머지 문자열만 리턴하기 때문에 총 32개의 문자열을 모두 얻기 위해서는 다음과 같은 메소드가 필요하다.   

```java
public class BitReverseOperatorExample{
    public static void main(String[] args){
        int v1 = 10;
        int v2 = ~v1;
        int v2 = ~v1 + 1;

        System.out.println(toBinaryString(v1)+ " ("+ v1 +")");    //00000000000000000000000000001010 (10)
        System.out.println(toBinaryString(v2)+ " ("+ v2 +")");    //11111111111111111111111111110101 (-11)
        System.out.println(toBinaryString(v3)+ " ("+ v3 +")");    //11111111111111111111111111110110 (-10)
    }

    public static String toBinaryString(int value){
        String str = Integer.toBinaryString(value);
        while(str.length() < 32){
            str = "0" + str;
        }
        return str;
    }
}
```

## 4. 이항 연산자 
### 4.1 산술 연산자 (`+`,`-`,`*`,`/`,`%`)   

|연산식|||설명|
|------|---|---|
|피연산자|`+`|피연산자|덧셈 연산|
|피연산자|`-`|피연산자|뺄셈 연산|
|피연산자|`*`|피연산자|곱셈 연산|
|피연산자|`/`|피연산자|좌측 피연산자를 우측 피연산자로 나눗셈 연산|
|피연산자|`%`|피연산자|좌측 피연산자를 우측 피연산자로 나눈 나머지를 구하는 연산|

- `%` 연산자    

```java
int result = num % 3;
```
`result`값은 `0`, `1`, `2`중 하나가 된다.

#### 산술 연산자의 특징    
피연산자들의 타입이 돌일하지 않을 경우 다음과 같은 규칙을 사용해서 피연산자들의 타입을 일치시킨 후 연산을 수행한다.   
1. 피연산자들이 모두 정수타입이고, `int`타입(4byte)보디 직은 타입의 경우 모두 `int`타입으로 변환후 연산을 수행한다. 따라서 산출 타입은 `int`이다.   
> `byte + byte => int + int = int`
2. 피연산자들이 모두 정수타입이고, `long`타입이 있을 경우 모두 `long`타입으로 변환후 연산을 수행한다. 따라서 연산의 산출타입은 `long`이다.   
> `int + long => long + long = long` 
3. 피연산자 중 실수 타입(float, double) 이 있을 경우, 크기가 큰 실수타입으로 변환 후, 연산을 수행한다. 따라서 산출 타입은 실수 타입이다.    
> `int + double => double + double = double`   

정수타입의 연산이 `int`타입으로 나오는 이유는 JVM이 기본적으로 32비트 단위로 계산하기 때문이다.    
{:.note}   

```java
byte byte1 = 1;
byte byte2 = 1;
//byte result = byte1 + byte2;   //컴파일 에러
int result = byte1 + byte2;   //2
```

```java
int int1 = 10;
int int2 = 4;

int result1 = int1 / int2;      //2
double result2 = int1 / int2;   //2.0, 연산결과가 나온후 실수화

double result3 = (int1*1.0) / int2;     //2.5
double result4 = (double)int1 / int2;   //2.5
double result5 = int1 / (double)int2;   //2.5
```

**`char`타입도 정수 타입이므로 산술연산이 가능하다.** 그러나 `int`타입으로 변환되므로 산출타입은 `int`타입니다.   

```java
char c1 = 'A' + 1;      //리터럴간의 연산은 해당타입으로 계산
char c2 = 'A';
//char c3 = c2 + 1;     //컴파일 에러
char c3 = (char)(c2 + 1);

System.out.pritnln("c1 : " + c1);   //c1 : B
System.out.pritnln("c2 : " + c2);   //c2 : A
System.out.pritnln("c3 : " + c3);   //c3 : B
```

#### 오버플로우 탐지
산술연산을 할 때 주의할 점은 연산 후의 산출값이 산출 타입으로 충분히 표현이 가능한지 살펴봐야한다. 산출 타입으로 표현할 수 없는 값이 산출되었을 경우, 오버플로우가 발생하고 쓰레기값을 얻을수 있기 때문이다. 

```java
int x = 1000000;
int y = 1000000;
int z = x * y;
System.out.println(z);      // -727379968
```

```java
long x = 1000000;
long y = 1000000;
long z = x * y;
System.out.println(z);      // 1000000000000
```
`x * y` 의 연산값이 $$10^{12}$$로 `int`타입에 저장될 수 있는 값의 범위를 넘어가기 때문에 쓰레기값이 나오게된다.    
`x`와 `y` 중 최소 하나라도 `long` 타입이어야 하고, 변수 `z`가 `long` 타입이어야 올바른 값이 저장된다.   

#### 정확한 계산은 정수 사용
정확하게 계산해야 할때는 부동소수점(실수) 타입을 사용하지 않는 것이 좋다. 

```java
int apple = 1;
double pieceUnit = 0.1;
int number = 7 ;

double result = apple - number*pieceUnit;

System.out.println(result);     //0.29999999999999993
```

`result`변수의 값은 정확히 0.3이 되지 않는다. 이것은 이진 포맷의 가수를 사용하는 부동소수점타입(`float`, `double`)은 0.1을 정확히 표현할수 없어 근사치로 처리하기 때문이다. 정확한 연산의 결과가 필요하다면 정수 연산으로 변경해서 계산해야 한다.   

```java
int apple = 1;
int totalPieces = apple *10;
int number = 7 ;
int temp = totalPieces - number;

double result = temp / 10.0;

System.out.println(result);     //0.3
```

#### NaN과 Infinity 연산
`/`, `%` 사용할 때, 좌측 연산자가 정수 타입인 경우 나누는 수인 우측 피연산자는 `0`을 사용할 수 없다. 만일 `0`으로 나누면 컴파일은 정상적으로 되지만, 실행시 `ArithmeticException`이 발생한다.

```java
5 / 0   //ArithmeticException 예외 발생
5 % 0   //ArithmeticException 예외 발생
```

그러나 실수 타입인 `0.0`, `0.0f`로 나누면 `ArithmeticException`이 발생하지 않고, `/`연산 결과는 `Infinity`, `%`연산 결과는 `NaN`(Not a Number) 을 가진다.   

```java
5 / 0.0     //Infinity
5 % 0.0     //NaN
```

`/`, `%`연산의 결과가 `Infinity`, `NaN`이 나오면 다음 연산을 수행해서는 안된다. 이값과 산술 연산을 하면 어떤 수와 연산을 하더라도 `Infinity`, `NaN`이 산출되어 데이터가 엉망이 될 수 있다.

```java
Infinity + 2    //Infinity
NaN + 2         //NaN
```

연산의 결과가 `Infinity`, `NaN`인지 확인하려면 `Double.isInfinite()`와 `Double.isNaN()`메소드를 이용하면 된다.   
```java
int x = 5;
double y = 0.0;

double z = x / y;
double w = x % y;

System.out.println(Double.isInfinite(z));   //true
System.out.println(Double.isInfinite(w));   //false

System.out.println(Double.isNaN(z));        //false
System.out.println(Double.isNaN(w));        //true

System.out.println(z);      //Infinity
System.out.println(w);      //NaN
```

#### 입력값의 NaN 검사
부동소수점(실수)을 입력받을 때는 반드시 `NaN`검사를 해야한다. `NaN`는 산술 연산이 가능하기때문에 어떠한 수가 `NaN`와 연산되면 데이터가 `NaN`이 되어 원래 데이터값을 잃을 수 있다. 그렇기 때문에 사용자로부터 문자열을 입력받을 때에는 반드시 `NaN`인지 검사해야 한다.

```java
String userInput = "NaN"                //사용자로부터 입력 받은 값
double val = Double.valueOf(userInput)  //입력값을 double타입으로 변환

double currentBalance = 10000.0;

if(Double.isNaN(val)){
    System.out.println("NaN이 입력되어 처리할 수 없음");
    val = 0.0;
}

currentBalance += val;
System.out.println(currentBalance);     //10000.0
```

### 4.2 문자 연결 연산자(`+`)
문자 연결 연산자인 `+`는 문자열을 서로 결합하는 연산자이다. 피연산자 중 한쪽이 문자열이면 `+`연산자는 문자열 연결 연산자로 사용되어 다른 피연산자를 문자열로 변환하고 서로 결합한다.    

```java
String str1 = "JDK" + 6.0;
String str2 = str1 + " 특징";

System.out.println(str1);   //JDK6.0
System.out.println(str2);   //JDK6.0 특징
```

간혹 `+`연산자가 산술 연산자인지 문자열 연결 연산자인지 판단하기 어려운 경우가 있다.   

```java
System.out.println("JDK" + 3 + 3.0); //JDK33.0
```
문자열과 숫자가 혼합된 `+`연산식은 왼쪽에서 오른쪽으로 연산이 진행된다. 따라서 `"JDK" + 3`이 먼저 연산되어 `JDK3`이라는 문자열이 되고, 이것을 다시 `3.0`과 연산하여 `JDK33.0`이라는 문자열 결과가 나온다.

다음과 같은 연산에서는 `3 + 3.0`이 먼저 연산되어 `6.0`실수값이 되고 이것을 `"JDK"`와 연산하여 `6.0JDK`라는 결과가 나온다.

```java
System.out.println(3 + 3.0 + "JDK"); //6.0JDK
```

### 4.3 비교 연산자(`<`,`<=`,`>`,`>=`,`==`,`!=`)
비교연산자는 대소(`<`,`<=`,`>`,`>=`) 또는 동등(`==`,`!=`)을 비교해서 `boolean`타입을 산출한다. 대소연산자는 `boolean` 타입을 제외한 기본 타입에 사용할 수 있고, 동등연산자는 모든 타입에 사용될 수 있다. 비교연산자는 흐름 제어문인 조건문(`if`), 반복문(`for`,`while`)에서 주로 이용되어 실행 흐름을 제어할 때 사용된다.   

|구분|연산식|||설명|
|---|---|---|---|---|---|
|동등비교|피연산자1|`==`|피연산자2|두 피연산자의 값이 같은지를 검사|
||피연산자1|`!=`|피연산자2|두 피연산자의 값이 다른지를 검사|
|크기비교|피연산자1|`>`|피연산자2|피연산자1이 큰지를 검사|
||피연산자1|`>=`|피연산자2|피연산자1이 크거나 같은지를 검사|
||피연산자1|`<`|피연산자2|피연산자1이 작은지를 검사|
||피연산자1|`<=`|피연산자2|피연산자1이 작거나 같은지를 검사|

만약 피연산자가 `char`타입이라면 유니코드 값으로 비교 연산을 수행한다.
{:.note}

```java
int num1 = 10;
int num2 = 10;
boolean result1 = (num1 == num2);   //true
boolean result2 = (num1 != num2);   //false
boolean result3 = (num1 <= num2);   //true

char char1 = 'A';
char char2 = 'B';
boolean result4 = (char1 < char2)   //true
```

비교연산자에서도 연산을 수행하기 전에 타입 변환을 통해 피연산자의 타입을 일치시킨다.    
한가지 예외가 있는데 `0.1==0.1f`의 경우 정상적이라면 `0.1f`가 `double` 타입으로 변환되어 `0.1==0.1`이 되어 `true`가 산출되어야 하지만 , 이진포맷의 가수를 사용하는 모든 부동소수점 타입은 `0.1`을 정확히 표현할 수 없어서 `0.1f`는 `0.1`의 근사값으로 표현되어 `0.10000000149011612`와 같은 값이 되기때문에 `0.1`보다 큰값이 되어버린다.    
해결방법은 피연산자를 모두 `float`으로 강제 타입 변환한 후 비교연산을 하든지, 정수로 변환해서 비교하면 된다.

```java
boolean b1 = ('A' == 65)    //true, 'A'를 int타입으로 변환 후 비교
boolean b2 = (3 == 3.0)     //true, 3을 double타입으로 변환 후 비교

boolean b3 = (0.1 == 0.1f)          //false
boolean b4 = ((float)0.1 == 0.1f)   //true
boolean b5 = ((int)(0.1*10) == (int)(0.1f*10)) //true
```

`String` 타입의 문자열을 비교할 때에는 대소연산자를 사용할 수 없고, 동등 비교 연산자는 사용할 수 있으나 문자열이 같은지, 다른지를 비교하는 용도로는 사용되지 않는다. `String`변수를 비교할 때 `==`연산자를 사용하면 두 피연산자에 저장된 주소값을 비교한다. `String`객체의 문자열만을 비교하고 싶으면 `==`연산자 대신에 `equals()` 메소드를 사용해야 한다.

```java
String str1 = "홍길동";
String str2 = "홍길동";
String str3 = new String("홍길동");

boolean b1 = (str1 == str2)     //true
boolean b2 = (str1 == str3)     //false

boolean b3 = str1.equals(str2)  //true
boolean b4 = str1.equals(str3)  //true
```

### 4.4 논리 연산자(`&&`,`||`,`&`,`|`,`^`,`!`)
논리 연산자는 논리곱(`&&`), 논리합(`||`), 배타적 논리합(`^`), 논리 부정(`!`) 연산을 수행한다. 논리연산자는 `boolean`타입만 사용할 수 있다.

- **AND(논리곱)**   

|연산식|||결과|설명|
|---|---|---|---|---|
|`true`|`&&`|`true`|`true`|피연산자 모두가 `true`일 경우에만 연산결과는 `true`|
|`true`|또는|`false`|`false`|
|`false`|`&`|`true`|`false`|
|`false`||`false`|`false`|

- **OR(논리합)**     

|연산식|||결과|설명|
|---|---|---|---|---|
|`true`|`||`|`true`|`true`|피연산자 중 하나만`true`이면 연산결과는 `true`|
|`true`|또는|`false`|`true`||
|`false`|`|`|`true`|`true`||
|`false`||`false`|`false`||


- **XOR(배타적논리합)**   

|연산식|||결과|설명|
|---|---|---|---|---|
|`true`|`^`|`true`|`false`|피연산자가 하나는 `true`이고 다른하나가 `false`일 경우에만 연산결과는 `true`|
|`true`||`false`|`true`||
|`false`||`true`|`true`||
|`false`||`false`|`false`||

- **NOT(논리부정)**  

|연산식||결과|설명|
|---|---|---|---|
|`!`|`true`|`false`|피연산자의 논리값을 바꿈|
||`false`|`true`||

> `&&`와 `&`의 산출 결과는 같지만 연산과정이 조금 다르다.    
    `&&` : 앞의 피연산자가 `false`라면 뒤의 피연산자를 평가하지 않고 바로 `false`라는 산출 결과를 낸다.    
    `&`: 두 연산자 모두를 평가해서 산출 결과를 낸다. 결과적으로 `&`보다 `&&`가 더 효율적으로 동작한다.   

> `||`와 `|`도 산출 결과는 같지만 연산과정이 조금 다르다.    
    `||` : 앞의 피연산자가 `true`라면 뒤의 피연산자를 평가하지 않고 바로 `true`라는 산출 결과를 낸다.    
    `|` : 두 연산자 모두를 평가해서 산출 결과를 낸다.   

### 4.5 비트 연산자(`&`,`|`,`^`,`~`,`<<`,`>>`,`>>>`)
비트 연산자는 데이터를 비트(bit) 단위로 연산한다. 즉 `0`, `1`이 피연산자가 된다. 그렇기 때문에 0과 1로 표현이 가능한 정수 타입만 비트 연산을 할 수 있다. 실수 타입인 `float`와 `double`은 비트연산을 할 수 없다.

##### 4.5.1 비트 논리 연산자(`&`,`|`,`^`,`~`)
`&`,`|`,`^`연산자는 피연산자가 `boolean`타입일 경우에는 [일반 논리 연산자](/study/java-live-study/2022-02-15-whiteship-live-study3/#44-%EB%85%BC%EB%A6%AC-%EC%97%B0%EC%82%B0%EC%9E%90)이고, 피연산자가 정수 타입일 경우에는 비트 논리 연산자로 사용된다.

- **AND(논리곱)**   

|연산식|||결과|설명|
|---|---|---|---|---|
|`1`|`&`|`1`|`1`|두 비트 모두 `1`일 경우에만 연산결과가 `1`|
|`1`|   |`0`|`0`|
|`0`|   |`1`|`0`|
|`0`|   |`0`|`0`|

- **OR(논리합)**     

|연산식|||결과|설명|
|---|---|---|---|---|
|`1`|`|`|`1`|`1`|두 비트중 하나만`1`이면 연산결과는 `1`|
|`1`|   |`0`|`1`||
|`0`|   |`1`|`1`||
|`0`|   |`0`|`0`||


- **XOR(배타적논리합)**   

|연산식|||결과|설명|
|---|---|---|---|---|
|`1`|`^`|`1`|`0`|두 비트 중 하나는 `1`이고 다른 하나가 `0`일 경우에만 연산결과는 `1`|
|`1`|   |`0`|`1`||
|`0`|   |`1`|`1`||
|`0`|   |`0`|`0`||

- **[NOT(논리부정)](/study/java-live-study/2022-02-15-whiteship-live-study3/#34-비트-반전-연산자)**  

|연산식||결과|설명|
|---|---|---|---|
|`~`|`1`|`0`|보수|
|   |`0`|`1`||

```java
int var1 = 45 & 25  //9
int var2 = 45 | 25  //61
int var3 = 45 ^ 25  //52
int var4 = ~45      //-46
```
![비트연산자](/assets/img/live-study/operator3.png){:width="90%" height="90%"}

비트 연산자는 피연산자를 `int`타입으로 자동 타입 변환 후 연산을 수행한다.

```java
byte num1 = 45;
byte num2 = 25;
//byte result = num1 & num2;    //컴파일 에러
int result = num1 & num2;    
```

![비트연산자](/assets/img/live-study/operator2.png)

##### 4.5.2 비트 이동 연산자(`<<`,`>>`,`>>>`)
비트 이동(shift) 연산자는 정수 데이터의 비트를 좌측 또는 우측으로 밀어서 이동시키는 연산을 수행한다.

|연산식|    |   |설명|
|------|---|---|----|
|`a`|`<<`|`b`|정수 `a`의 각 비트를 `b`만큼 왼쪽으로 이동(빈자리는 `0`으로 채워진다.)|
|`a`|`>>`|`b`|정수 `a`의 각 비트를 `b`만큼 오른쪽으로 이동(빈자리는 정수 `a`의 최상위 부호 비트(MSB)로 채워진다.)|
|`a`|`>>>`|`b`|정수 `a`의 각 비트를 `b`만큼 오른쪽으로 이동(빈자리는 `0`으로 채워진다.)|


```java
int result = 1 << 3;    //8
```
![쉬프트연산](/assets/img/live-study/operator4.png)

```java
int result = -8 >> 3;   //-1
```
![쉬프트연산](/assets/img/live-study/operator5.png)

```java
int result = -8 >>> 3;  //536870911
```
![쉬프트연산](/assets/img/live-study/operator6.png)

### 4.6 대입 연산자(`=`,`+=`,`-=`,`*=`,`/=`,`%=`,`&=`,`^=`,`!=`,`<<=`,`>>=`,`>>>=`)
대입연산자는 오른쪽 피연산자의 값을 좌측 피연산자인 변수에 저장한다. 오른쪽 피연산자는 리터럴 및 변수, 그리고 다른 연산식이 올 수 있다. 정해진 연산을 수행한 후 결과를 변수에 저장하는 복합 대입 연산자도 있다.

|구분|연산식|||설명|
|---|---|---|---|---|
|단순 대입 연산자|변수|`=`|피연산자|우측의 피연산자의 값을 변수에 저장|
|복합 대입 연산자|변수|`+=`|피연산자|`변수=변수+피연산자`|
||변수|`+=`|피연산자|`변수=변수+피연산자`|
||변수|`-=`|피연산자|`변수=변수-피연산자`|
||변수|`*=`|피연산자|`변수=변수*피연산자`|
||변수|`/=`|피연산자|`변수=변수/피연산자`|
||변수|`%=`|피연산자|`변수=변수%피연산자`|
||변수|`&=`|피연산자|`변수=변수&피연산자`|
||변수|`|=`|피연산자|`변수=변수|피연산자`|
||변수|`^=`|피연산자|`변수=변수^피연산자`|
||변수|`<<=`|피연산자|`변수=변수>>피연산자`|
||변수|`>>=`|피연산자|`변수=변수<<피연산자`|
||변수|`>>>=`|피연산자|`변수=변수>>>피연산자`|

대입연산자는 모든 연산자들 중에 가장 낮은 연산 우선 순위를 가지고 있기 때문에 제일 마지막에 수행된다. 

## 5. 삼항 연산자
삼항 연산자는(`?:`)는 세갸ㅐ의 피연산자를 필요로 하는 연산자를 말한다. 삼항 연산자는 `?`앞의 조건식에 따라서 콜론(`:`) 앞뒤의 피연산자가 선택 된다고 해서 조건 연산식이라고 부르기도 한다. 

```     
            조건식이        조건식이
            true일때        false일때
(조건식) ? 값 또는 연산식 : 값 또는 연산식
```


삼항연산자는 `if`문으로 변경해서 작성할 수 있지만, 한 줄에 간단하게 삽입해서 사용할 경우에는 삼항연산자를 사용하는 것이 더 효율적이다.
```java
int score = 85;
char grade = (score>90) ? 'A' : ((score>80) ? 'B' : 'C');   //B
```

```java
int score = 85;
char grade;

if(score>90){
    grade='A';
}else if(score>80){
    grade='B';
}else{
    grade='C';
}
```

## 6. 객체비교연산자(`instanceof`)
`instanceof`연산자는 객체 타입 비교 연산자로 참조변수가 참조하고 있는 인스턴스의 실제 타입을 알아보기 위해 사용한다.
연산 결과로 `boolean` 타입을 산출한다. 주로 <mark>상속 관계</mark>에서 부모객체인지 자식객체인지 확인하는데 사용한다.

참조변수의 타입과 비교하려는 타입이 상속 관계가 아니면 비교 자체가 불가능하다.(컴파일 에러)    
```java
String str = "string";
System.out.println(str instanceof String);      //true
//System.out.println(str instanceof Integer);   //컴파일 에러, 상속 관계가 아니다.
```

> **상속**   
어느 타입을 상속하는 다른 타입이 있다면 상속당하는 타입은 부모타입, 상속하는 타입은 자식타입이라한다.    
상속에 관해서는 나중에 자세히 알아보고 모든 참조 타입은 `Object`타입을 상속하며 `Object`타입은 모든 참조 타입의 부모 타입이란 점을 알아두자.

![상속관계](/assets/img/live-study/operator7.png){: width="80%" height="80%"}


**모든 참조타입은 `Object` 타입을 상속한다.**   

```java
String str = "string";
Integer i = 10;

System.out.println(str instanceof Object);      //true
System.out.println(i instanceof Object);        //true
```

**참조변수가 `null`이라면 `instanceOf`는 항상 `false`를 리턴한다.**   

```java
String str = null;

System.out.println(str instanceof Object);      //false
System.out.println(str instanceof String);      //false
```

어떤 타입의 대한 `instanceof` 연산의 결과가 true라는 것은 검사한 타입으로 형변환이 가능하다는 것을 뜻한다.


## 7. 화살표 연산자(`->`)
화살표 연산자는 Java 8 버전부터 추가된 것으로, 람다 표현식과 함께 사용된다.    
화살표 연산자는 Java 에서 람다 표현식의 syntax 일부이다.

```java
(타입 매개변수, ...) -> {실행문;...}
```
`->` 연산자는 매개 변수를 이용해서 중괄호`{}`를 실행한다는 뜻이다.

```java
(int a) -> {System.out.println(a);}
```

Refernce
- [이것이 자바다 - 신용권의 Java 프로그래밍 완전 정복](http://www.yes24.com/Product/Goods/15651484)   
- <https://velog.io/@geesuee/JAVA-%EA%B0%9D%EC%B2%B4-%ED%83%80%EC%9E%85-%ED%99%95%EC%9D%B8-instanceof>   
- <https://catch-me-java.tistory.com/31>