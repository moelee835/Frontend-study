# 호이스팅이란?
호이스팅은 JS에서 정의된 기본 동작으로 모든 선언부를 선언 스코프 상단으로 이동 시키는 것이다.

자바스크립트에서는 모든 변수는 사용 전 선언되어야 한다.

```javascript
x = 5; // Assign 5 to x  
  
elem = document.getElementById("demo"); // Find an element  
elem.innerHTML = x;                     // Display x in the element  
  
var x; // Declare x
```

위와 같은 프로그램은 아래와 동일하다.
```javascript
var x; // Declare x  
x = 5; // Assign 5 to x  
  
elem = document.getElementById("demo"); // Find an element  
elem.innerHTML = x;                     // Display x in the element
```

이런 현상을 이해하기 위해선 "호이스팅"이란 단어에 대해 이해해야한다.

JS에서 호이스팅이란 선언문을 현재 스코프 최상단으로 이동시키는 것을 의미한다.

> 여기서 스코프의 최상단 이라는 것은 현재 스크립트의 최상단 또는 현재 함수의 최상단을 의미한다. 함수 스코프, 전역 스코프에서 var는 서로 다른데, 블록 스코프, 전역 스코프 var는 같은 현상이 여기서 기인한다.

## let and const keyword
let과 const 키워드로 선언한 변수 또한 호이스팅 된다.
그러나 초기화되지는 않는다.
즉, 코드 블럭은 해당 변수에 대해서 이미 알고 있지만, 실제 선언될 때 까지는 사용할 수 없다는 것이다. 그럴 경우 ReferenceError 가 발생하게 된다.

이런 구간을 Temporal Dead Zone이라고 한다.

```javascript
carName = "Volvo";  
let carName;
```

## 초기화 구문은 호이스팅 되지 않는다.

자바스크립트는 오직 선언만 호이스팅 할 뿐 초기화는 하지 않는다.
```javascript
var x = 5; // Initialize x  
var y = 7; // Initialize y  
  
elem = document.getElementById("demo"); // Find an element  
elem.innerHTML = x + " " + y;           // Display x and y
```

```javascript
var x = 5; // Initialize x  
  
elem = document.getElementById("demo"); // Find an element  
elem.innerHTML = x + " " + y;           // Display x and y  
  
var y = 7; // Initialize y
```

실행 결과 elem의 내용은 `NaN`이 된다.
즉, 실제 y를 사용하는 문장에서 y는 undefined가 되는 것이다.


```javascript
var x = 5; // Initialize x  
var y;     // Declare y  
  
elem = document.getElementById("demo"); // Find an element  
elem.innerHTML = x + " " + y;           // Display x and y  
  
y = 7;    // Assign 7 to y
```

2번째 소스와 위 소스는 동일하다.

호이스팅은 알 수 없거나 예측하기 어려운 동작을 할 수도 있다. 개발자가 호이스팅에 대해 이해하지 못한다면 버그가 발생할 수 있다. 버그를 회피하기 위해 모든 변수는 반시 스크립트나 스코프가 시작할 때 선언하도록 한다. 자바스크립트가 이런식으로 코드를 해석하기 때문에, 이런 습관은 항상 권장된다.