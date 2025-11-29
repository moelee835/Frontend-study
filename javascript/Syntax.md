자바스크립트는 2개 타입의 values 를 다룬다.
1. Literals
2. Variables

리터럴은 고정값, 변수는 변동하는 값임. (당연히 아는거)
JS에서는 행동을 정의하기 위해 keyword를 사용함

`let` : 변수 선언용.
`const` : 상수 선언용. 반드시 초기화 해야함.

```javascript
let variable;
console.log(variable);
```

출력 결과는 undefined 임.

### 식별자
변수, 함수, 클래스 등에 붙이는 이름.

Naming rules
1. _나 $ 또는 알파벳 등 문자로 시작해야 함.
2. 숫자로 시작할 수 없음.
3. 예약어인 keyword를 지정할 수 없음.
4. case에 따라 구분됨. 대소문자 구분.

#### JS underscore(_)
'\_' 를 하나의 문자로 취급함.
또한, 변수명 처음에 달아서 사용 가능함.
`_x` 등으로 사용 가능

전문적인 개발자들은 private 변수들에 대해서 \_를 앞에 달아 사용함.

$ 달러 표시도 마찬가지로 사용됨.
보통 자바스크립트 라이브러리에서 main 함수의 별칭으로 사용함.

### 변수 선언
`let carName`;
위 표현에서 carName의 값은 undefined임.
어떤 값을 할당하기 전까진.

### 자동 변수 선언
```javascript
x = 5;
y = 6;
z = x + y;
```
위 코드에서 x, y, z 는 선언된 적이 없지만, 자동으로 선언이 이루어짐.

하지만, 항상 프로그램 초반에 선언하고 사용하는 것이 좋은 습관이다.

2015년 이전에는 var 키워드를 사용했다. 2015년 자바스크립트 이후에 let과 const 가 추가됨.

> *Never User var if you can use let or const*

### 데이터 타입
기본 8개 타입이 있음.
string은 인용부호 내부에 쓰여진다.

### 한 줄에 여러 변수 선언
```javascript
let person = 'john', carName ='Volvo', price = 200;
```

```javascript
//위와 같음
let person = 'john',
 carName ='Volvo',
 price = 200;
```

### 연산자
다른 언어와 같음.
다만, 다음에 주의할 것.

> 만약 인용부호 안에 숫자를 넣고, 나머지 숫자들과 `+`로 연결된다면, JS는 이 숫자들을 모두 문자열로 처리한다.

