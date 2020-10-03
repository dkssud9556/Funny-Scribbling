# Function

### 함수 리터럴 

자바스크립트에서 함수는 일반 객체처럼 값으로 취급된다.

객체 리터럴 방식처럼 함수 리터럴을 이용해 함수를 생성할 수 있다.

```text
// 함수 리터럴을 이용한 함수 선언의 예 
function sayHello() {
    console.log('Hello');
}
// function 키워드 
// 함수명 
// 매개변수 
// 함수 몸체 
```

### 함수 생성 방법 3가지 

1. 함수 선언문, 함수 표현식 

   * 함수 리터럴 방식으로 함수를 선언하는 방법이다.
   * 자바스크립트에서는 함수의 이름을 명시하지 않아도 된다. 이를 익명 함수라고 한다.
   * 함수 선언문 방식은 위에 있는 예와 형태가 같다. 함수 선언문은 반드시 함수 이름을 정의해야 한다.
   * 함수 표현식은 함수 리터럴로 함수를 만들고, 그 함수를 변수에 할당하는 방식이다.

   ```text
   var sayHello = function() {
       console.log('Hello');
   }
   ```

   * 여기서 sayHello는 Hello를 출력하는 익명 함수를 참조하는 참조 변수가 되는 것이다. 그래서 sayHello\(\)로 저 익명 함수를 호출할 수 있고, 다른 변수에 대입 연산자를 사용해서 같은 익명 함수를 참조하게 할 수 있다.
   * 익명 함수 표현식이 아니라 기명 함수 표현식도 사용할 수 있다. 그런데 많이 쓰이지 않는다.

   ```text
   var sayHello = function say() {
       console.log('Hello');
   }
   sayHello(); // 'Hello'
   say(); // say is not defined
   ```

   * 기명 함수 표현식을 사용할 때 주의할 점은 함수 표현식에서 사용된 함수 이름은 함수 외부에서 사용할 수 없다는 점이다.
   * 기명 함수 표현식의 함수명은 재귀 호출이나, 디버거 등에서 함수를 구분할 때 사용한다고 한다. 잘은 모르겠다.
   * 함수 선언문으로 선언한 함수는 자바스크립트 엔진에 의해 함수 표현식 형태로 변경된다.

   ```text
   function sayHello() {
       console.log('Hello');
   }
   ---- 자바스크립트 엔진에 의한 변경 ----
   var sayHello = function sayHello() {
       console.log('Hello');
   }
   ```

2. Function\(\) 생성자 함수 

   * 함수도 내장 Function\(\) 생성자 함수를 통해 생성된 객체이다. 함수 리터럴 방식으로 생성한 함수도 내부적으로는 Function\(\) 생성자 함수를 통해 생성된다.
   * 형식 : new Function\(arg1, arg2, ... argN, functionBody\)
   * 위 sayHello 함수를 Function\(\) 생성자 함수로 생성한 예 

   ```text
   var sayHello = new Function('console.log("Hello")');
   sayHello(); // 'Hello'
   ```

   * 자주 사용되지 않는 함수 생성 방식이다.

### 함수 호이스팅 

```text
add(4, 5); // 9

function add(x, y) {
    return x + y;
}

add(1, 3); // 4
```

위 예에서 첫 번째 add함수 호출은 add함수가 호출되기 전이지만 정상적으로 결과가 나온다. 

이는 함수 호이스팅 때문이다. 함수 호이스팅은 함수 선언문 형태로 정의한 함수의 유효 범위가 코드의 맨 처음부터 시작하는 것이다.

하지만 함수 표현식 형태로 정의한 함수는 함수 호이스팅이 일어나지 않는다.

```text
add(2, 4); // error

var add = function(x, y) {
    return x + y;
}

add(4, 3); // 7
```

