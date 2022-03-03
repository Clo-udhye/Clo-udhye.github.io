---
layout: post
title: "[Java] 제어문"
tags: java live-study operator
image: 
    path: /assets/img/live-study/live-study4-cover.png
accent_color: '#F4184C'
description: >
    [dev-ujin✨](https://github.com/dev-ujin)과 함께하는 [live study📝](https://github.com/whiteship/live-study) 4주차
categories:
    - study
    - java-live-study
related_posts:    
    - /study/java-live-study/2022-02-06-whiteship-live-study1/  
    - /study/java-live-study/2022-02-13-whiteship-live-study2/    
---

## [Java Live Study] 4. 제어문  
* 
{:toc}

## 코드 실행 흐름 제어
자바 프로그램을 시작하면 `main()` 메소드의 시작 중괄호`{`에서 시작해서 끝 중괄호 `}`까지 위에서 부터 아래로 실행하는 흐름을 가지고 있다. 이러한 흐름을 개발자가 원하는 방향으로 바꿀 수 있도록 해주는 것이 흐름 제어문이다. 제어문은 조건식과 중괄호`{}` 블록으로 구성되는데, 조건식의 연산 결과에 따라 블록 내부의 실행 여부가 결정된다. 흐름 제어문을 사용할 경우 다양한 실행 흐름이 생성된다. 
![흐름제어문](/assets/img/live-study/control.png){: width="80%" height="80%"}   

## 조건문
### if문
`if`문은 조건식의 결과에 따라 블록의 실행 여부가 결정된다.   
![if문](/assets/img/live-study/if.png){: width="70%" height="70%"}   

조건식에는 `true`또는 `false`값을 산출할 수 있는 연산식이나, `boolean` 변수가 올 수 있다, 조건식이 `true`이면 블록을 실행하고 `false`이면 블록을 실행하지 않는다.

중괄호`{}` 블록은 여러 개의 실행문을 하나로 묶기 위해 작성한다. 만약 조건식이 `true`일때 실행할 문장이 하나 밖에 없다면 생략할 수 있다. 하지만 중괄호 블록을 작성하지 않으면 코드의 가독성(코드해석)이 좋지않고, 버그 발생 원인이 될 수 있다.      
```java
if(조건식) {                
    실행문;                 
    실행문;                         
    ...             
}
```
```java
if(조건식)    
    실행문; 
```

```java
int score = 93;
if(score>=90){
    System.out.println("점수가 90보다 큽니다.");
    System.out.println("등급은 A 입니다.");
}

if(score<90)
    System.out.println("점수가 90보다 작습니다.");
    System.out.println("등급은 B 입니다.");     // 들여쓰기가 되어있지만 if문과는 상관없는 실행문
```
```
점수가 90보다 큽니다.
등급은 A 입니다.
등급은 B 입니다.
```
실행결과
{:.figcaption}

#### if-else문
`if`문은 `else`블록과 함께 사용되어 조건식의 결과에 따라 실행블록을 선택한다. `if`문의 조건식이 `true`이면 `if`문의 블록이 실행되고, 조건식이 `false`이면 `else`블록이 실행된다. 조건식의 결과에 따라 이 두개의 블록 중 어느 한 블록의 내용만 실행하고 전체 `if`문을 벗어나게 된다.
![if-else문](/assets/img/live-study/ifelse.png){: width="70%" height="70%"}  

```java
int score = 93;
if(score>=90){
    System.out.println("점수가 90보다 큽니다.");
    System.out.println("등급은 A 입니다.");
} else{
    System.out.println("점수가 90보다 작습니다.");
    System.out.println("등급은 B 입니다.");   
}    
```
```
점수가 90보다 큽니다.
등급은 A 입니다.
```
실행결과
{:.figcaption}

#### if-else if-else 문
조건문이 여러개인 `if`문도 있다. 처음 `if`문의 조건식이 `false`인 경우 다른 조건식의 결과에 따라 실행 블록을 선택 할  수 있는데, `if`블록의 끝에 `else if`문을 붙이면 된다. `else if`문의 수는 제한이 없으며 여러 개의 조건식 중 `true`가 되는 블록만 실행하고 전체 `if`문을 벗어나게 된다. `else if` 블록의 마지막에는 `else`블록을 추가할 수 있는데, 모든 조건식이 `false`일 경우 `else`블록을 실행하고, `if`문을 벗어나게 된다.    
![if-elseif-else문](/assets/img/live-study/ifelseifelse.png){: width="70%" height="70%"}  

```java
int score = 75;
if(score>=90){
    System.out.println("점수가 90~100 입니다.");
    System.out.println("등급은 A 입니다.");
} else if(score>=80){
    System.out.println("점수가 80~89 입니다.");
    System.out.println("등급은 B 입니다.");   
} else if(score>=70){
    System.out.println("점수가 70~79 입니다.");
    System.out.println("등급은 C 입니다.");   
} else{
    System.out.println("점수가 70 미만 입니다.");
    System.out.println("등급은 D 입니다.");
}
```
```
점수가 70~79 입니다.
등급은 C 입니다.
```
실행결과
{:.figcaption}

#### 중첩 if문
`if`문의 블록 내부에는 또 다른 `if`문으 사용할 수 있다. 이것을 중첩 `if`문이라 부르는데, 중첩의 단계는 제한이 없다. 모든 제어문은 서로 중첩이 가능하다.    
![중첩if문](/assets/img/live-study/ifif.png){: width="70%" height="70%"}  

```java
int score = (int)Math.random()*20 + 81; // 81~100
System.out.println("점수: " + score);

String grade;

if(score>=90){
    if(score>=95){
        grade = "A+";
    } else{
        grade = "A";
    }
} else{
    if(score>=85){
        grade = "B+";
    } else{
        grade = "B";
    }
}

System.out.println("학점: " + grade);
```
```
점수: 84
학점: B
```
실행결과
{:.figcaption}

### switch문
`switch`문은 `if`문과 마찬가지로 조건 제어문이다. 하지만 `switch`문은 `if`문 처럼 조건식이 `true`일 경우에 블록 내부의 실행문을 실행하는 것이 아니라, 변수가 어떤 값을 갖느냐에 따라 실행문이 선택된다. `if`문은 조건식의 결과가 `true`, `false` 두가지 밖에 없기 때문에 경우의 수가 많아질수록 `else-if`를 반복적으로 추가해야 하므로 코드가 복잡해진다. 그러나 `switch`문은 변수의 값에 따라서 실행문이 결정되기 때문에 같은 기능의 `if`문보다 코드가 간결하다. 

![switch문](/assets/img/live-study/switch.png){: width="70%" height="70%"}  
`switch`문은 괄호 안의 값과 동일한 값을 갖는 `case`로 가서 실행문을 실행시킨다. 만약 괄호 안의 값과 동일한 값을 갖는 `case`가 없으면 `defalut`로 가서 실행문을 실행시킨다. `defalut`는 생략 가능하다.

```java
int num = (int)(Math.random()*6) + 1;   //1~6

switch (num){
    case 1:
        System.out.println("1번이 나왔습니다.")
        break;
    case 2:
        System.out.println("2번이 나왔습니다.")
        break;
    case 3:
        System.out.println("3번이 나왔습니다.")
        break;
    case 4:
        System.out.println("4번이 나왔습니다.")
        break;                        
    case 5:
        System.out.println("5번이 나왔습니다.")
        break;
    default:
        System.out.println("6번이 나왔습니다.")
        break;                
}

```
```
5번이 나왔습니다.
```
실행결과
{:.figcaption}

`case` 끝에 `break`가 붙어 있는 이유는 다음 `case`를 실행하지 말고 `switch`문을 빠져나가기 위해서이다. `break`문이 없다면 다음 `case`가 연달아 실행되는데, 이때에는 `case` 값과는 상관없이 실행된다.   

```java
int time = (int)(Math.random()*4)+8;    //8~11
System.out.println("[현재시간]: " + time + "시");

switch(time){
    case 8:
        System.out.println("출근합니다.");
    case 9:
        System.out.println("회의를 합니다.");        
    case 10:
        System.out.println("업무를 봅니다.");    
    default:
        System.out.println("외근을 나갑니다.");    
}
```
```
[현재시간]: 9시
회의를 합니다.
업무를 봅니다.
외근을 나갑니다.
```
실행결과
{:.figcaption}

`char`타입 변수도 `switch`문에 사용될 수 있다.    

```java
char grade = 'B';

switch(grade){
    case 'A':
    case 'a':
        System.out.println("우수 회원입니다."); 
        break;
    case 'B':
    case 'b':
        System.out.println("일반 회원입니다."); 
        break;
    default:
        System.out.println("손님입니다."); 
}
```
```
일반 회원입니다.
```
실행결과
{:.figcaption}

`String`타입 변수도 `switch`문에 사용될 수 있다.    

```java
String position = "과장";

switch(position){
    case "부장":
        System.out.println("700만원"); 
        break;
    case "과장":
        System.out.println("500만원"); 
        break;
    default:
        System.out.println("300만원"); 
}
```
```
500만원
```
실행결과
{:.figcaption}

## 반복문
반복문은 어떤 작업(코드들)이 반복적으로 실행되도록 할 때 사용되며, 반복문의 종류로는 `for`문, `while`문, `do-while`문이 있다. `for`문과 `while`문은 서로 변환이 가능하기 때문에 반복문을 작성할 때 어느쪽을 선택해도 좋지만, `for`문은 반복 횟수를 알고 있을 때 주로 사용하고, `while`문은 조건에 따라 반복할 때 주로 사용한다. `while`문과 `do-while`문의 차이점은 조건을 먼저 검사하느냐 나중에 검사하느냐일 뿐 동작 방식은 동일하다.
### for문
프로그램을 작성하다 보면 똑같은 실행문을 반복적으로 실행해야 할 경우가 많이 발생한다. 

1~100까지 더하는 실행문을 `for`문을 통해 획기적으로 줄일수 있다.
```java
int sum = 0;
sum = sum + 1;
sum = sum + 2;
sum = sum + 3;
...
sum = sum + 99;
sum = sum + 100;

System.out.println("1~100까지의 합: "+sum);
```
```java
int sum = 0;
for(int i=1; i<=100; i++){
    sum = sum + i;
}
System.out.println("1~100까지의 합: "+sum);
```

반복문은 한 번 작성된 실행문을 여러번 반복 실행 해주기 때문에 코드를 절감하고 간결하게 만들어준다.     
![for문](/assets/img/live-study/for.png){: width="70%" height="70%"}  

`for`문이 처음 실행될 때 ①초기화식이 제일 먼저 실행된다. 다음 ②조건식을 평가해서 `true`이면 ③실행문을 실행시키고, `false`이면 `for`문 블록을 실행하지 않고 끝나게 된다. 블록 내부의 ③실행문들이 모두 실행되면 ④증감식을 실행시키고 ②조건식을 다시 평가하게 된다. 평가 결과가 `true`이면 ③→④→② 로 다시 진행하고, `false`이면 `for`문이 끝나게 된다. 

초기화식의 역할은 조건식과 실행문, 증감식에서 사용할 변수를 초기화 하는 역할을 한다. 초기화식이 필요없을 경우 초기화식을 생략할 수 있다. 

```java
int i=1;
for(; i<=100 i++){ ... }
```
어떤 경우에는 초기화식이 둘 이상이 있을 수도 있고, 증감식도 둘 이상 있을 수 있다. 
```java
for(int i=0, j=100; i<=50&&j>=50; i++, j--){ ... }
```

초기화식에 선언된 변수는 `for`문 블록 내부에서 사용되는 로컬 변수이다. 따라서 `for`문을 벗어나서는 사용할 수 없다. 변수 i가 초기화식에서 선언되지않고 `for`문 전에 선언되었다면 `for`문 내부뿐만 아니라 `for`문을 벗어나서도 사용할 수 있다.

```java
int sum = 0;

for(int i=1; i<=100; i++){
    sum += i;
}

System.out.println("1~100 합:" +sum);
//System.out.println("1~"+i+" 합:" +sum);   //컴파일 에러

sum = 0;
int j = 0;  //카운터 변수
for(j=1; j<=50; j++){
    sum += j;
}
System.out.println("1~"+(j-1)+" 합:" +sum);

```
```
1~100 합: 5050
1~50 합: 1275
```
실행결과
{:.figcaption}

`for` 문을 작성 할때 주의할 점은 초기화 식에서 루프 카운트 변수를 선언할 때 부동소수점 타입을 사용하지 말아야한다. 부동소수점으로는 0.1을 정확하게 표현할 수 없기 때문에 루프의 실행이 예상대로 안될수 있다.

`for`문은 또다른 `for`문을 내포할 수 있는데 이것을 중첩된 `for`문이라고 한다. 이경우 바깥쪽 `for`문이 한번 실행할 때마다 중첩된 `for`문은 지정된 횟수만큼 반복해서 돌다가 다시 바깥쪽 `for`문으로 돌아간다.

```java
for(int m=2; m<=9; m++){
    System.out.println("*** "+m+"단 ***");
    for(int n=1; n<=9; n++){
        System.out.println(m+"x"+n+"="+(m*n));
    }
}
```
```
*** 2단 ***
2x1=2
2x2=4
2x3=6
2x4=8
2x5=10
2x6=12
2x7=14
2x8=16
2x9=18

*** 3단 ***
...
```
실행결과
{:.figcaption}


#### for-each문 (향상된 for문)
`for`문은 카운터 변수를 이용해 실행문을 반복시키기 때문에 인덱스를 이용해 값을 저장하거나 조회하는 배열을 이용할 때 같이 사용되는 경우가 많다. 그러나 가독성이 좋지 않고 배열에 잘못된 인덱스로 접근하여 `ArrayIndexOutOfBoundsException` 예외가 발생하는 경우가 잦다. 이런 부분을 `for-each`문 이라고도 불리는 `향상된(Enhanced) for`문을 사용하면 좀 더 깔끔하게 코드를 작성할 수 있다.

```java
int[] nums = {1,2,3,4,5};

int sum = 0;
for(int i=0; i<=nums.length; i++){
	sum += nums[i];
}
System.out.println("nums의 합계: " + sum);

sum = 0;
for(int num: nums){
	sum += num;
}
System.out.println("nums의 합계: " + sum);
```
```
nums의 합계: 15
nums의 합계: 15
```
실행결과
{:.figcaption}

배열 `nums`안의 요소를 변수 `num`에 하나씩 넣어서 실행문을 실행한다. `for-each`문은 배열처럼 여러 원소로 이루어진 집합의 모든 원소에 대해 특정 작업을 반복하기 위해 사용하여 간편하고 가독성 좋은 코드를 만들수 있고 배열 인덱스 문제 `ArrayIndexOutOfBoundsException` 예외를 피할 수 있다. 
하지만 `for-each`문 내부에서 인덱스를 사용해 원하는 배열의 요소에 접근할 수 없고 **배열안의 값을 사용할 순 있지만 절대 수정할 수는 없다.**

```java
int[] nums = {1,2,3,4,5};

for(int num: nums){
    num = 0;        //배열 안의 값이 수정되지 않는다.
}

int i=0;
for(int num: nums){
    System.out.println("nums["+i+"]: " + num);
    i++;
}
```
```
nums[0]: 1
nums[1]: 2
nums[2]: 3
nums[3]: 4
nums[4]: 5
```
실행결과
{:.figcaption}


`for-each`문을 중첩으로 사용하여 2차배열의 요소에 접근할 수 있다.

```java
{% raw %}String[][] str_arr = {{"apple","banana","cherry"},{"2000","5000","8000"}};{% endraw %} 
		
for(String[] arrs : str_arr) {
	for(String s : arrs) {
		System.out.println(s);
	}
}
```
```
apple
banana
cherry
2000
5000
8000
```
실행결과
{:.figcaption}

### while문
`for`문이 정해진 횟수만큼 반복한다면, `while`문은 조건식이 `true`일 경우에 계속해서 반복한다. 조건식에는 비교 또는 논리 연산식이 주로 오는데, 조건식이 `false`가 되면 반복행위를 멈추고 `while`문을 종료한다. 
![while문](/assets/img/live-study/while.png){: width="70%" height="70%"}  

`while`문이 처음 실행 될 때 ①조건식을 평가한다. 평가결과가 `true`이면 ②실행문을 실행한다. ②실행문이 모두 실행되면 다시 조건식으로 되돌아가서 ①조건식을 다시 평가한다. 만약 조건식이 `true`이면 ②→①로 다시 진행하고, `false`이면 `while`문을 종료한다. 

```java
int sum = 0;
int i = 1;  //카운터 변수

while(i<=100){
    sum += i;
    i++;
}

System.out.println("1~"+(i-1)+" 합:" +sum);
```
```
1~100 합: 5050
```
실행결과
{:.figcaption}

조건식에는 `boolean`변수나 `true`/`false` 값을 산출하는 어떠한 연산식이든 올 수 있다. 만약 조건식에 `true`를 사용하면 `while(ture){...}`가 되어서 무한루프를 돌게된다. 무한 루프는 무한히 반복하여 실행하기 때문에 언젠가는 `while`문을 빠져 나가기 위한 코드가 필요하다. 

```java
boolean run = true;
int speed = 0;
int keyCode = 0;

while(run){
    if(keyCode!=13 && keyCode!=10){ //키보드 Enter의 키코드(13,10)
        System.out.println("-----------------------");
        System.out.println("1.증속 | 2.감속 | 3.중지");
        System.out.println("-----------------------");
        System.out.print("선택: ");
    }

    keyCode = System.in.read(); //키보드의 키코드를 읽음

    if(keyCode == 49){          //키보드 1
        speed++;
        System.out.println("현재속도: " + speed);
    } else if(keyCode == 50){   //키보드 2
        speed--;
        System.out.println("현재속도: " + speed);
    } else if(keyCode == 51){   //키보드 3
        run = false;
    } 
}
System.out.println("프로그램 종료");
```
```
-----------------------
1.증속 | 2.감속 | 3.중지
-----------------------
선택: 1
현재속도: 1
-----------------------
1.증속 | 2.감속 | 3.중지
-----------------------
선택: 2
현재속도: 0
-----------------------
1.증속 | 2.감속 | 3.중지
-----------------------
선택: 3
프로그램 종료
```
실행결과
{:.figcaption}

### do-while문
`do-while`문은 조건식에 의해 반복 실행한다는 점에서는 `while`문과 동일하다. `while`문은 시작할 때 부터 조건식을 검사하여 블록 내부를 실행할지 결정하지만, 경우에 따라서는 블록 내부의 실행문을 우선 실행시키고 실행결과에 따라서 반복 실행을 계속할지 결정하는 경우도 발생한다. 이때 `do-while`문을 사용 할 수 있다.
![do-while문](/assets/img/live-study/do-while.png){: width="70%" height="70%"}  

```java
//import java.util.Scanner;
System.out.println("메세지를 입력하세요");
System.out.println("프로그램을 종료하려면 q를 입력하세요.");

Scanner scanner = new Scanner(System.in);   
String inputString;

do{
    System.out.print("> ");
    inputString = scanner.nextLine();   //키보드로 입력한 문자열을 얻음
    System.out.println(inputString);
} while(!inputString.equals("q"));  //문자열 비교
System.out.println("프로그램 종료");
```
```
메세지를 입력하세요
프로그램을 종료하려면 q를 입력하세요.
> Hello~
Hello~
> nice to meet you!
nice to meet you!
> q
q
프로그램 종료
```
실행결과
{:.figcaption}

### break문
`break`문은 반복문인 `for`문, `while`문, `do-while`문을 실행 중지할 때 사용한다. 또한 `switch`문에서도 `break`문을 사용해서 종료한다.    
![break문](/assets/img/live-study/break.png){: width="70%" height="70%"}  

```java
while(true){
    int num = (int)(Math.random()*6) + 1;   //1~6의 랜덤숫자
    System.out.println(num);    

    if(num == 6){
        break;      //while문 종료
    }
}
System.out.println("프로그램 종료");
```
```
5
1
6
프로그램 종료
```
실행결과
{:.figcaption}

만약 반복문이 중첩되어 있을 경우 `break`문은 가장 가까운 반복문만 종료하고 바깥쪽 반복문은 종료시키지 않는다. 중첩된 반복문에서 바깥쪽 반복문까지 종료 시키려면 바깥쪽 반복문에 이름(라벨)을 붙이고 `break 이름;`을 사용하면 된다.   
![break Label](/assets/img/live-study/breakLabel.png){: width="70%" height="70%"}  

```java
Outer: for(char upper='A'; upper<='Z'; upper++){
    for(char lower='a'; lower<='z'; lower++){
        System.out.println(upper + "-" + lower);
        if(lower=='d'){
            break Outer;
        }
    }
}
System.out.println("프로그램 종료");
```
```
A-a
A-b
A-c
A-d
프로그램 종료
```
실행결과
{:.figcaption}

### continue문
`continue`문은 반복문인 `for`문, `while`문, `do-while`문에서만 사용되는데, 블록내부에서 `continue`문이 실행되면 `for`문의 증감식 또는 `while`문, `do-while`문의 조건식으로 이동한다. 
![continue](/assets/img/live-study/continue.png){: width="70%" height="70%"}  

```java
for(int i=1; i<=10; i++){
    if(i%2 != 0){   //홀수인 경우
        continue;
    }
    System.out.println(i);
}
```
```
2
4
6
8
10
```
실행결과
{:.figcaption}


<br>
- - -

## 학습목표 바로가기
- [선택문](/study/java-live-study/2022-02-25-whiteship-live-study4/#조건문)
- [반복문](/study/java-live-study/2022-02-25-whiteship-live-study4/#반복문)

- 과제 0 - [JUnit 5]()
  
- 과제 1
 `src`: [live-study dashboard](구현시 추가)
- 과제 2 - [LinkedList](https://dev-dahye.github.io/study/data-structure/2022-02-27-linked-list/)    
  `src`: [LinkedList](구현시 추가)   

- 과제 3 / 과제4 - [Stack](https://dev-dahye.github.io/study/data-structure/2022-02-24-stack/)   
  `src`: [Array Stack](구현시 추가)   
  `src`: [LinkedList Stack](구현시 추가)   

- 과제 5 - [Queue]   
  `src`: [Array Queue](구현시 추가)   
  `src`: [LinkedList Queue](구현시 추가)  


<br>
- - -

## Reference 
- [이것이 자바다 - 신용권의 Java 프로그래밍 완전 정복](http://www.yes24.com/Product/Goods/15651484)    
- <https://www.daleseo.com/how-to-traverse-list-in-java/>
- <https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=highkrs&logNo=220276708627>
- <https://java119.tistory.com/107>


