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
document.body.innerHTML = "<h1 id='clock'></h1>";
var clock = document.getElementById('clock');
setInterval(function () {
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

#### setTimeout(function, millisecond)

```javascript
setTimeout(function () {
    alert('3초가 지났습니다.');
}, 3000);
```
+ 3초 후에 함수를 1번 실행한다.

#### setInterval(function, millisecond)

```javascript
setTimeout(function () {
    alert('3초마다 실행합니다.');
}, 3000);
```

+ 3초마다 함수를 반복해서 실행한다.

#### clearTimeout(id), clearInterval(id)

```javascript
// 1초마다 경고창을 실행하는 함수를 intervalID로 할당한다.
var intervalId = setInterval(function () {
    alert('<h1>' + new Date() + '</h1>');
}, 1000);

// 10초 후 함수를 실행한다.
setTimeout(function () {
    // 타이머를 종료한다.
    clearInterval(intervalID);
}, 10000);
```

+ 10초 동안 경고창을 계속출력한다.


### 인코딩과 디코딩 함수

+ skip

### 숫자변환 함수

#### parseInt(), parseFloat()

```javascript
> Number('1000원')
NaN
> parseInt('1000원')
1000
> parseFloat('1.5$')
1.5
```

+ `Number()` 함수는 하나라도 숫자로 바꿀 수 없으면 NaN으로 반환한다.
+ `parseInt()` 함수는 숫자로 변환할 수 있는 부분까지 숫자로 반환한다.

**끝.**

---

## 6. 객체

### 객체 생성

```javascript
var product = {
    제품명: '7D 건조 망고',
    유형: '당절임',
    원산지: '필리핀',
}

> product.제품명
'7D 건조 망고'
> product.['제품명']
'7D 건조 망고'
```
+ 객체는 중괄호로 선언한다.
+ 객체는 키(key)와 속성(property)으로 구성된다.
+ 속성에 접근할 때는 대괄호(`[]`)보다 점(`.`)을 더 많이 사용한다.
+ 단, 키 값이 따옴표로 감싸져 있는 경우 대괄호를 사용해야 한다.

### 속성과 메서드

```javascript
var person = {
    name: '윤인성',
    eat: function(food) {
        alert(this.name + '이 ' + food + '을/를 먹습니다.');
    }
};

person.eat('밥');

// 윤인성이 밥을/를 먹습니다.
```

+ 객체의 속성 중 함수 자료형인 속성을 메서드(method)라고 부른다.
+ 위에서 `person` 객체는 두 가지 속성(property)를 가지고 있다.
    + `name`과 `eat`
+ 그 중 함수 자료형인 `eat`은 메서드라고 부른다.

### 객체와 반복문

```javascript
var product ={
    name: 'Microsoft Windows 10',
    price: '150,000원',
    language: '한국어',
    subscription: true
};

var output = '';
for (var key in product) {
    output += '●' + key + ': ' + product[key] + '\n';
}
alert(output);
```

### with 키워드

```javascript
var student = {
    이름: '연하진',
    국어: 92, 수학: 98
};

var output = '';
with (student) {
    output += '이름: ' + 이름 + '\n';
    output += '국어: ' + 국어 + '\n';
    output += '수학: ' + 수학 + '\n';
}
alert(output);

// 아래 코드처럼 속성 앞에 객체를 적을 필요가 없다.
// output += '이름: ' + student.이름 + '\n';
// output += '국어: ' + student.국어 + '\n';
// output += '수학: ' + student.수학 + '\n';
```
    + with 키워드에 객체를 넣어주면, 괄호 안에서 객체를 명시할 필요없이 속성을 쉽게 사용할 수 있다.

### 속성 추가, 속성 삭제

```javascript
var product = {제품명:'7D 건조 망고'};

product.원산지 = '필리핀'      // 속성 추가

delete(product.원산지);       // 속성 삭제
```

### 객체와 배열을 사용한 데이터 관리

+ skip

## 7. 생성자 함수

### 생성자와 객체

```javascript
var student = new Student()

// student : 객체 또는 인스턴스 (object or instance)
// Student : 생성자 함수 (constructor)
```

+ 파이썬의 `class`와 `instance` 개념과 비슷하다.

### 생성자 함수 생성

```javascript
function Student() {

}
```

+ 파이썬의 `class`와 비슷하다.
+ 생성자 함수의 이름은 일반적으로 대문자로 시작한다.
+ 대문자로 시작하지 않아도 문제 없지만 일종의 컨벤션이다.

### new

```javascript
function Student() {

}

var student = new Student();
```
+ 생성자 함수로 객체를 생성할 때 `new` 키워드를 사용한다.

### this

```javascript
function Student(name, highnote, lownote) {
    this.이름 = name;
    this.고음 = highnote;
    this.저음 = lownote;
}

var student = new Student('음악대장', 100, 100)
```

+ 파이썬의 `self`와 같다.

### 프로토타입

```javascript
function Student(name, english, math) {
    this.이름 = name;
    this.영어 = english;
    this.수학 = math;
}

Student.prototype.getSum = function () {
    return this.영어 + this.수학;
};
Student.prototype.getAverage = function () {
    return this.getSum() / 2;
};
```

+ 공통된 메서드가 필요할 때 프로토타입(`prototype`)으로 메서드를 만든다.
+ 생성자 함수로 생성된 객체가 공통으로 가지는 공간

### 캡슐화

```javascript
function Rectangle(w, h) {
    var width = w;
    var height = h;

    this.getWidth = function () {return w;};
    this.getHeight = function () {return h;};
    this.setWidth = function (w) {
        if (w < 0) {
            throw '길이는 음수일 수 없습니다.';
        } else {
            width = w;
        }
    };
    this.setHeight = function (h) {
        if (h < 0) {
            throw '길이는 음수일 수 없습니다.';
        } else {
            height = h;
        }
    };
}

// getWidth와 getHeight 형태의 메서드와 같이 값을 가져오는 메서드를 게터(Getter)라고 한다.
// setWidth와 setHeight 형태의 메서드와 같이 값을 입력하는 메서드를 세터(Setter)라고 한다.
// 게터와 세터를 만드는 것도 캡슐화의 일종이다.
```

+ 내가 만든 생성자 함수를 사용자가 아무렇게나 사용하지 못하도록 막는 기술을 `캡슐화`라고 한다.
+ 잘못 사용될 수 있는 객체의 특정 부분을 사용자가 사용할 수 없게 막는 기술을 `캡슐화`라고 한다.
+ 만일의 상황을 대비해서 특정 속성이나 메서드를 사용자가 사용할 수 없게 숨겨놓는 것을 `캡슐화`라고 한다.

### 상속

```javascript
function Square(length) {
    this.base = Rectnagle;
    this.base(length, length);
}

Square.prototype = Rectangle.prototype;
```

**끝.**

---

## 8. 기본 내장 객체

@@@ resume


---
