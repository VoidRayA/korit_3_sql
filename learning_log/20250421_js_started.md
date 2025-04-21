20250421 -> 20250421_js_started.md 파일로 변경

# JavaScript

## 실습 환경 구축하기
1. window + 기본 이라고 검색 -> 기본앱 -> 웹브라우저를 크롬으로
2. js_sql_study에서 새 폴더 -> js_study 생성
3. ch01 폴더 생성
4. 새 파일 -> index.html 생성
5. live server 실행
6. ctrl + shift + i -> 개발자도구를 켭니다.

### Hello, JavaScript
- console창에 출력하는 명령어
```js
console.log('Hello, JavaScript');
```

## Console과 주석 사용하기
### 콘솔
- 최종 사용자가 아닌 개발자를 위한 메시지 출력을 목적으로, 주로 개발 도중에 중간 결과를 확인하고, 디버깅을 위해 사용되는 영역.

```java
System.out.println(1  2  3);
System.out.print(1);
System.out.print(" ");
System.out.print(2);
System.out.print(" ");
System.out.print(3);
// 결과값이 1 2 3 -> 근데 자료형이 int여야해
```
Java에서는 %d을 사용하지 않으면 저렇게 작성해야하는 데 반해서,
```js
console.log(1, 2, 3); // 결과값 : 1 2 3 -> 자료형은 number
```
즉 콘솔 기능의 장점은 괄호 내에 쉼표(,)를 이용하여 여러 데이터를 한 번에 출력 가능하다는 점입니다.
### 주석(Comment)
- 모든 프로그래밍 언어에서 활용하는 개념으로, 컴퓨터가 무시하는 메시지.
- // : JavaScript에서의 주석 방법
- /**/ : 다중 주석
- ctrl + / : 일단 코드 써놓고 사후 주석처리 방법

## 변수와 상수에 데이터 담기
## 변수와 상수
1. 변수
  - 값을 저장하고 '변경이 가능한 것을' 변수
2. 상수
  - 값을 저장하지만 '변하지 않는 고정된 값'을 담는 것을 상수

```js
let darkModeOn = true;
const PI = 3.1415926535;
console.log(PI); //결과값 : 3.1415926535
console.log(darkModeOn); // 결과값 : true
darkModeOn = false;
console.log(darkModeOn); // 결과값 : false
PI = 5; // 상수에 값을 재대입했으므로 오류 발생
```

* 예전에는 변수를 선언할 때 var를 썼습니다.
  - ES6 이ㅏ전에는 JS에서 변수를 선언할 때 var를 사용했습니다. 근데 ES6버전 이후에는 let과 const가 var를 대체했습니다.

```js
//여기가 코드의 처음이라고 가정합니다.
console.log(b);     // 원래 오류 발생해야함. 변수 b는 없으니까// undefined
var b = 3;          // 근데 var로 선언됐기 때문에 오류가 발생하지 않고 ↑
                    // 67번 라인에 3이 아니라 undefined인 이유는
                    // b에 3이라는 데이터가 저장된 시점이 68번 라인이기 때문
                    // 근데 이상한 점은 변수 선언도 68번 라인이라는 점입니다.
                    // 그게 JS가 일관성 없는 프로그래밍언어인 이유였습니다.
                    // 이상을 해결하기 위해 let / const가 등장했습니다.
console.log(a);     // 얘도 67번 라인과 차이가 없어보입니다.
let a = 1;          // 여기가 차이가 생겨서 74번 라인은 바로 오류가 발생합니다.
                    // let을 쓰게 되면 Java에서처럼 '순서대로' 변수의 선언
                    // 및 초기화가 일어납니다.
```

1. let
  - let a = 1; 에서 우리가 알 수 있는 점
    - let은 자료형과 관계없이 '변수'임을 명시한다는 점
    - a는 변수명(camel case로 작성)
    - =는 대입연산자라는 점
    - = 뒤에 데이터가 온다는 점
    - 재 대입의 경우에는 Java에서처럼 let을 명시하지 않는다는 점
```js
let studentName = '안근수';     // 변수 선언 및 초기화
console.log(studentName);     // 결과값 : 안근수
studentName = '김일'          // 선언된 변수에 데이터 재대입 -> let 명시 x
console.log(studentName);     // 결과값이 : 김일
```

```js
let a = 1;
console.log(a);       // 결과값 : 1
let b = a;
console.log(a, b);    // 결과값 : 1 1
a = 2;                                // 프로그램은 '순서대로' 실행됩니다.
console.log(a, b);    // 결과값 : 2 1
```

* JS가 var에서 벗어났더니 또 골치아픈 점
- Java의 경우에는 처음 변수를 선언할 때 자료형을 명시하기 때문에 재 대입이 일어나는 과정에서 동일한 자료형이 아니면 오류가 발생했었습니다. 그런데 JS의 경우 let / const로 변수인지 상수인지만 명시하기 때문에 자료형이 다른 데이터를 변수에 대입하더라도 대입 상에서 오류가 발생하지 않습니다.
- 이상의 경우가 개발자 입장에서 변수 개수를 줄이면서 데이터를 바꿀 수 있으니 좋다고 생각하실 수도 있는데 예를 들어 input 태그에 type을 number로 잡아놔서 수학 연산을 하려고 했는데 거기에 string 자료형이 들어오게되면 페이지에 오류가 발생할 수 밖에 없습니다. 그런데 대입 자체까지는 오류가 발생하지 않기 때문에 개발자들이 어느 부분에서 오류가 발생했는지 정확하게 파악하기 힘들다는 점이 문제였습니다.


↓ JS 문제 예시
```js
let a = 1;
console.log(a);       // 결과값 : 1
let b = a;
console.log(a, b);    // 결과값 : 1 1
a = 2;                                // 프로그램은 '순서대로' 실행됩니다.
console.log(a, b);    // 결과값 : 2 1
a = '안녕하세요';     // 원래 정수에 string 자료형을 대입함 -> 오류 발생 x
b = true;             // 원래 정수에 boolean 자료형을 대입함 -> 오류 발생 x
console.log(a, b);    // 결과값 : 안녕하세요 true
```

## 기본 자료형 / 연산자
### 자료형
1. boolean
  - 참 / 거짓 여부 true / false
```js
let bool1 = true;
let bool2 = false;
console.log(bool1, bool2);
```