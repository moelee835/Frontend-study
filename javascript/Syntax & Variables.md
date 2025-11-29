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

---

## let keyword

* let 이라는 키워드는 ES6 부터 등장했음.
* let은 블록 스코프에 제한된다.
* let은 항상 사용전에 선언되어야 한다.
* let으로 선언한 이름은 같은 스코프에서 재선언될 수 없음.

ES6 이전에는 블록 스코프가 없었다.
오직 Global scope와 Function scope만 가지고 있었다.

이런 상황에서 블록 스코프`{}`에 한정되는 변수를 다루기 위해 let과 const가 등장했다.

```javascript
{
	let x = 2;
}

//여기선 위에서 사용한 x를 사용할 수 없다.
x = 10; // 이 x는 자동 선언된 완전 별개의 변수이다.
```

### Global scope

`var` 키워드로 선언되면 항상 전역 스코프 변수가 된다.
var로 선언되면, block 스코프를 갖지 않는다. 설령 블록 안에서 선언되어도.

또한 var로 선언하면 재선언이 가능하다.

```javascript
var x = 10;

let confunc = () => {
    var x = 302;
    console.log(x); // 302
}

console.log(x); // 10
confunc();
console.log(x); // 10
```

> 호이스팅에 의한 변수값 이상
> 함수 스코프에서 `var x` 형태로 global, function 스코프 모두에서 선언되어 있을 때, 함수 외부, 내부에서 별개로 취급된다.
> 그런데, 블록 스코프만으로 나뉘어 있다면 다르다.
```javascript
var x = 10;
console.log(x); // 302
{
    var x = 302;
    console.log(x); // 302
}
console.log(x); // 302
```
> 출력 결과는 모두 302로 동일하다. 변수 호이스팅에 의해
```javascript
var x = 10;
var x = 302;
console.log(x); // 302
{
    console.log(x); // 302
}
console.log(x); // 302
```
> 이렇게 변화하기 때문으로 보인다.


| Scope | Redeclare | Reassign | Hoisted | Binds this |
| ----- | --------- | -------- | ------- | ---------- |
| var   | No        | Yes      | Yes     | Yes        |
| let   | Yes       | No       | Yes     | No         |
| const | Yes       | No       | No      | No         |
#### This 바인딩
var로 선언하면 자동으로 window / global에 종속된다.
`var x`가 전역에서 window.x 또는 global.x가 된다. 즉, global object에서 this에 바인딩 된다.
반면 let과 const는 global의 프로퍼티가 되지 않는다.

### 호이스팅 여부
let, const, var 모두 호이스팅이 된다. 다만 TDZ에 의해 let, const는 선언된 스코프 외부에선 사용할 수 없다. (TDZ = Temporal Dead Zone)

### Browser Support

크롬 49, 엣지 12, 파이어폭스 36, 사파리 11, 오페라 36 부터 모두 let, const 완전 지원.
익스플로러 11 및 이전 버전은 사용 불가하다.

---

### Let Hoisting
`var` 로 선언되는 경우, 최상단에 호이스팅 된다. 그렇기에 모든 var로 선언된 변수들이 동시에 초기화 된다.
또한, 모든 var 변수는 실제 선언한 구간보다 위에서 호출이 가능하다.

```javascript
carName = "Volvo";
var carName;
```
carName은 모두 같은 변수이다.

let도 물론 호이스팅이 되긴 하지만, 초기화되지 않는다. 호출시 ReferenceError가 발생하게 된다.

```javascript
carName = "Saab";
let carName = "Volvo;;
```

---

## const 키워드

* ES6부터 유효하다.
* 재선언되지 않는다.
*  재할당되지 않는다. 
* block scope에 한정된다.

const 변수는 반드시 선언될 때 동시에 초기화 되어야 한다.
const 변수는 변수가 수정될 일이 없어야 하는 경우 사용할 수 있다. 일반적으로

Array, Object, Function, 정규식 을 선언할 때 사용한다.

### Constant Object and Arrays
const에 대한 잘못된 이해는 상수 값에 대한 수정 불가가 아닌 참조에 대한 수정 불가라는 점이다.
즉, const로 array를 선언했을 때, 해당 array의 원소 값을 변경하는 것은 가능하다. 또한 object에 대한 프로퍼티 값을 변경하는 것도 자유이다.

### Constant Arrays
```javascript
const ary = ['hi', 'hoist', 'value'];

ary[0] = 'hello';
ary[2] = 121;

ary.push("toyota");
console.log(ary);
```

### Redeclaring
다음을 살펴보면, const, let 상호 간 재선언에 대해 알 수 있다.
var를 포함해서 const, let 어떤 형식으로 변수를 선언하든 const로 재선언할 수는 없다.

```javascript
var x = 2;     // Allowed  
const x = 2;   // Not allowed  
  
{  
let x = 2;     // Allowed  
const x = 2;   // Not allowed  
}  
  
{  
const x = 2;   // Allowed  
const x = 2;   // Not allowed  
}
```

```javascript
const x = 2;     // Allowed  
x = 2;           // Not allowed  
var x = 2;       // Not allowed  
let x = 2;       // Not allowed  
const x = 2;     // Not allowed  
  
{  
  const x = 2;   // Allowed  
  x = 2;         // Not allowed  
  var x = 2;     // Not allowed  
  let x = 2;     // Not allowed  
  const x = 2;   // Not allowed  
}
```

### Let Hoisting
역시 let과 마찬가지로 호이스팅이 되긴 하지만 Temporal Dead Zone으로 인해 실제 선언부 이전에는 사용이 불가능하다. 물론 스코프 외부도 마찬가지이다.