ⓒ JMC 2017

**주요 소스**  
모던 웹을 위한 JavaScript 및 jQuery 입문, 윤인성

**예제 코드**  
크롬 개발자도구를 켜고 console 창에 입력하면 된다.

**작성 규칙**  
파이썬과 다른 내용 위주로 적는다.

**resume**  
5.11 자바스크립트 내장 함수


---

# 예제 코드

## 현재 시간 표시 (코드 10-27)

### 코드

```javascript
> document.body.innerHTML = "<h1 id='clock'></h1>"
> var clock = document.getElementById('clock');
> setInterval(function () {
    clock.innerHTML = new Date().toString();
}, 1000);
```

+ 1초마다 시간이 바뀐다.

### 설명

+ `document.body.innerHTML` : HTML 내용을 문서의 body 태그 안에 넣는다.

# JavaScript 문법

## 1. 기본 문법

### 논리 연산자

+ `&&` : and
+ `||` : or

```javascript
alert(30 > 20 && 20 >10);
```

### 복합 대입 연산자

+ `*=` : 기존 변수의 값에 값을 곱한다.
+ `/=` : 기존 변수의 값에 값을 나눈다.
+ `%=` : 기존 변수의 값에 나머지를 구한다.


### 증감 연산자

```javascript
var number = 10;

alert(number++);    //코드 실행 후에 1을 더한다.
alert(++number);    //코드 실행 전에 1을 더한다.
alert(number--);    //코드 실행 후에 1을 뺀다.
alert(--number);    //코드 실행 전에 1을 뺀다.
```

+ 차례대로 10, 12, 12, 10을 출력한다.

### 자료형

#### typeof()

```javascript
alert(typeof('String'));
```

### 입력

#### prompt()

```javascript
> prompt('안내'[, '디폴트값'])
```

#### confirm()

```javascript
> confirm('안내')
```

+ `확인`를 누르면 true를 리턴한다.
+ `취소`를 누르면 false를 리턴한다.

### 자료형 변환

#### Number()

```javascript
var input = prompt('숫자를 입력해주세요.');
var numberInput = Number(input);
```
```javascript
var input = Number(prompt('숫자를 입력해주세요.'));
```

+ 두 코드는 동일한 기능을 수행한다.

#### String()

```javascript
var age = 28;
var stringAge = String(age);
```

#### Boolean()

```javascript
Boolean(0);
Boolean('');
Boolean(undefined);
```
+ 모두 `false`를 출력한다.

### 비교연산자와 일치연산자

+ `==` : 값이 같은지 비교한다.
+ `===` : 값도 같고, 타입도 일치하는지 연산한다.
+ `!==` : 값도 다르고, 타입도 다른지 연산한다.

```javascript
> alert('' === false);        // 값은 false로 같지만, ''는 type이 string이고, false는 type이 boolean이므로 false를 출력한다.
```

**끝.**

---

## 2. 조건문

### 형태

#### if else

```javascript
if (Boolean 표현식) {
    문장 A
} else {
    문장 B
}
```

+ `Python`과 달리 콜론(`:`)을 쓰지 않고 중괄호(`{}`)를 사용한다.
+ `Boolean 표현식`이 true이면 `문장 A`를 실행한다.
+ `Boolean 표현식`이 false이면 `문장 B`를 실행한다.

#### if else if

```javascript
if (Boolean 표현식1) {
    문장 A
} else if (Boolean 표현식2) {
    문장 B
} else {
    문장 C
}
```

## 3. 반복문

### for 반복문

#### 형태

```javascript
for (초기식; 조건식; 종결식) {
    문장
}
```
+ `초기식`을 실행한다.
+ `조건식`을 비교한다.
+ `조건식`이 거짓이라면 반복문을 빠져나간다.
+ `조건식`이 참이라면 `문장`을 실행한다.
+ `종결식`을 실행하고 다시 `조건식`을 비교한다.


```javascript
for (var value = 0; value < 5; value++) {
    alert(value + '번째 반복문')
}

// 출력 결과는 다음과 같다.
// 0번째 반복문
// 1번째 반복문
// 2번째 반복문
// 3번째 반복문
// 4번째 반복문
```

#### 배열 요소 출력하기

```javascript
var array = ['포도', '사과', '바나나', '망고'];

for (var i = 0; i < array.length; i++) {
    alert(array[i]);
}

// 포도
// 사과
// 바나나
// 망고
```

### for in 반복문

```javascript
var array = ['포도', '사과', '바나나', '망고'];

for (var i in array) {
    alert(array[i]);
}
```

### break

+ `Python`과 동일하다.
+ 반복문을 종료한다.

### continue

+ `Python`과 동일하다.
+ 현재 반복을 중단하고 다음 반복으로 넘어간다.

**끝.**

---

## 4. 함수

### 형태

#### 익명함수

```javascript
var 함수이름 = function (인자) {
    문장;
    return 리턴값;
}

// 인자 == 매개변수
```

#### 선언적 함수

```javascript
function 함수이름 (인자) {
    문장;
    return 리턴값;
}
```

+ 일반적으로 선언적 함수를 사용한다.

#### 선언적 함수 예시

```javascript
function myFunction(x) {
    return x * x;
}


alert(myFunction(3));


// 9
```

### 콜백 함수

+ 함수도 하나의 자료형이므로 인자로 전달할 수있다.
+ 이렇게 인자로 전달하는 함수를 콜백 함수라고 부른다.

```javascript
function callTenTiems(callback) {
    for (var i = 0; i < 10; i++) {
        callback();
    }
}

var callback = function () {
    alert('함수 호출');
};

callTenTimes(callback);

// '함수 호출'이 적힌 경고화면(alert)을 10번 출력한다.
```

**끝.**

---

## 5. JavaScript 내장 함수

### 타이머 함수


---
