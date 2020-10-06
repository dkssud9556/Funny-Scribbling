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

하지만 함수 표현식 형태로 정의한 함수는 함수 호이스팅이 일어나지 않는다. 그래서 함수 선언문보다는 함수 표현식 형태를 사용하는걸 권장한다.

```text
add(2, 4); // error

var add = function(x, y) {
    return x + y;
}

add(4, 3); // 7
```

### 함수도 객체다 

자바스크립트에서는 함수도 객체이다. 따라서 배열이 그랬던 것처럼 함수도 프로퍼티를 가질 수 있다.

```text
function add(x, y) {
    return x + y;
}

add.prop = 'dynamic';
add.prop2 = 13;

add.prop; // 'dynamic'
add.prop2; // 13
```

함수를 생성할 때 함수의 실행 코드는 함수의 \[\[Code\]\] 내부 프로퍼티에 저장된다.

### 함수는 일급 객체다 

자바스크립트에서 함수는 일급 객체이다. 다음의 특징들을 가지고 있을 때 일급 객체라고 부른다.

1. 리터럴에 의해 생성될 수 있다.
2. 변수나 배열의 요소, 객체의 프로퍼티 등에 할당 가능하다.
3. 함수의 인자로 전달 가능하다.
4. 함수의 리턴값으로 리턴 가능하다.

자바스크립트의 함수가 일급 객체이기 때문에 이를 통해 함수형 프로그래밍이 가능하다.

### 함수의 기본 프로퍼티 

함수를 생성하면 일반적인 객체와는 다른 함수 객체만의 표준 프로퍼티가 정의된다.

1. length

   * 함수의 length 프로퍼티는 함수의 선언에서 정의한 매개변수의 개수를 뜻한다.

   ```text
   function sayHello() {
       console.log('Hello');
   }

   function add(x, y) {
       return x + y;
   }

   sayHello.length; // 0
   add.length; // 2
   ```

2. prototype
   * prototype 프로퍼티는 \[\[Prototype\]\] 내부 프로퍼티와는 다르다. 둘다 프로토타입 객체를 의미하지만 관점이 다르다. 
   * \[\[Prototype\]\] 프로퍼티는 객체 자신의 부모 역할을 하는 프로토타입 객체를 가리키는 것이다.
   * prototype 프로퍼티는 함수 자신이 생성자 함수로 호출되었을 때 생성된 객체의 부모 역할을 하는 프로토타입 객체를 뜻한다.
   * prototype 프로퍼티는 함수가 생성될 때 만들어지며, prototype 프로퍼티가 가리키는 객체\(만들어진함수.prototype\)는 constructor 프로퍼티를 가지게 된다. 이 constructor 프로퍼티는 만들어진함수를 가리키게 된다.

### 함수의 여러 형태 

1. 콜백 함수 

   * 콜백 함수는 개발자는 등록만 해놓고 특정 이벤트가 발생했거나 특정 시점이 되었을 때 시스템이 호출하는 함수를 뜻한다.
   * 특정 함수의 인자로 넘겨서, 코드 내부에서 호출되는 함수도 콜백 함수다.
   * 보통 익명 함수를 사용하여 인자로 넘긴다.

   ```text
   function executeCallback(callback) {
       callback();
   }

   executeCallback(function() {
       console.log('callback function is executed');
   }); // 'callback function is executed'
   ```

2. 즉시 실행 함수 

   * 함수를 정의하는 동시에 실행되는 함수를 즉시 실행 함수라고 한다.
   * 즉시 실행 함수는 한 번 실행되고 다시 호출할 수 없는 함수다.
   * 보통 익명 함수로 정의한다. 이름을 명시할 수 있지만 그렇다고 해서 다시 호출할 수는 없다.

   ```text
   (function (msg) {
       console.log(msg);
   })('hello'); // 'hello'
   ```

   * 위 예가 즉시 실행 함수의 형식을 보여준다. 익명 함수 리터럴을 괄호로 감싸고, 뒤에 함수를 실행하는 괄호를 연다. 그리고 그 괄호 안에 매개변수를 넘긴다.
   * 한 번 실행되고 다시 호출할 수 없기 때문에 최초 초기화 코드에 많이 사용된다.

3. 내부 함수 

   * 내부 함수는 말 그대로 함수 내부에 정의된 함수를 뜻한다.
   * 내부 함수에서는 자신을 둘러싼 외부 함수의 변수에 접근할 수 있다.
   * 내부 함수는 일반적으로 자신이 정의된 부모 함수 내부에서만 호출 가능하다.
   * 내부 함수는 클로저를 생성하는 등의 용도로 사용된다.

   ```text
   function outer() {
       var x = 10;
       var y = 10;
    
       function inner() {
           var y = 30;
        
           console.log(x);
           console.log(y);
       }
       inner();
   }

   outer(); // 10, 30
   inner(); // inner is not defined
   ```

   * inner 내부 함수에서 부모 함수인 outer 함수의 변수 x에 접근할 수 있으며, outer 함수 외부에서는 inner 함수를 호출할 수 없다는 것을 알 수 있다.

4. 함수를 리턴하는 함수 

   * 자바스크립트에서 함수는 일급 객체이기 때문에 함수의 리턴값이 될 수 있다.

   ```text
   function outer() {
       var a = 10;
    
       return function() {
           console.log(a);
       }
   }

   var inner = outer();
   inner(); // 10
   ```

   * 그리고 위와 같이 실행이 끝난 부모 함수의 변수를 참조하는 함수\(inner\)를 클로저라고 한다.

### arguments 객체 

자바스크립트의 함수는 매우 유연하다.

```text
function say(x, y) {
    console.log(x, y);
}

say(); // undefined undefined
say(1); // 1 undefined
say(1, 2); // 1 2
say(1, 2, 3); // 1 2
```

위 예제를 보면 함수의 인수 개수를 맞추지 않아도 함수가 잘 호출되는 것을 볼 수 있다.

인수의 개수를 적게 호출하면 안 넘겨준 매개변수에는 undefined가 할당되고, 인수의 개수를 많이 호출하면 개수를 넘어간 인수는 무시된다.

그런데 코드를 작성하다 보면 함수의 인수 개수에 따라 동작을 다르게 해야줘야 할 때가 생긴다. 그럴 때 arguments 객체를 이용하면 유용하다. arguments 객체는 함수가 호출될 때 자동으로 함수 내부에 전달된다.

arguments 객체는 유사 배열 객체이며, 함수 호출할 때 넘긴 인자들이 배열 형태로 저장되어 있다.

arguments 객체에는 세 부분으로 구성된다.

1. 함수 호출로 인해 넘겨진 인자들 \(인덱스 0, 1, 2...\) 
2. length 프로퍼티 : 인자의 개수 
3. callee 프로퍼티 : 실행중인 함수의 참조값

다음은 인자로 넘겨진 모든 숫자들을 더해서 반환하는 함수의 예다.

```text
function sum() {
    var sum = 0;
    for (var i = 0; i < arguments.length; i++) {
        sum += arguments[i];
    }
    return sum;
}

sum(1, 2); // 3
sum(2, 5, 9, 10); // 26
```

그리고 유사 배열 객체이므로 this 바인딩을 통 배열의 표준 메소드를 사용할 수 있다.

### this 바인딩 

함수를 호출하면 방금 정리한 arguments 객체와 함께 this 인자가 함수 내부로 전달된다. 자바스크립트의 this는 함수의 호출 방식에 따라 다른 객체를 참조한다.

#### 객체의 메소드 호출 시 this 바인딩 

객체의 메소드 내부의 this는 메소드를 호출한 객체를 참조한다.

```text
var person = {
    name: 'Park',
    age: 19,
    introduce: function() {
        console.log("Hello, I'm " + this.name + ' and ' + this.age + ' years old.'
    }
}

person.introduce(); // "Hello, I'm Park and 19 years old."

var otherPerson = {
    name: 'Kim',
    age: 30
}

otherPerson.introduce = person.introduce;

otherPerson.introduce(); // "Hello, I'm Kim and 30 years old."
```

introduce 메소드는 간단하게 name, age 프로퍼티를 출력하는 기능을 한다. 앞에서 말했던 것처럼 this는 메소드를 호출한 객체로 바인딩된다는 것을 알 수 있다.

#### 함수 호출 시 this 바인딩 

일반적인 함수를 호출할 때 this는 전역 객체가 바인딩 된다. 전역 객체는 브라우저에서는 window, Node.js 환경에서는 global 객체가 된다.

모든 전역 변수는 전역 객체의 프로퍼티들이다. 그렇기 때문에 전역에 `var num = 13` 으로 변수를 선언하고, `window.num`으로 접근할 수 있다.

```text
var str = 'JavaScript';

function sayStr() {
    this.str;
}

sayStr(); // JavaScript
```

이러한 this 바인딩은 내부 함수에서도 똑같이 일어나기 때문에 주의해야 한다.

```text
var num = 13;

var obj = {
    num: 3,
    outer: function() {
        this.num++;
        console.log(this.num); // 4
        
        var inner1 = function() {
            this.num++;
            console.log(this.num); // 14
            
            var inner2 = function() {
                this.num++;
                console.log(this.num); // 15
            }
            inner2();
        }
        inner1();
    }
}

obj.outer();
```

위 예를 보면 outer 함수는 객체의 메소드이기 때문에 this가 메소드를 호출한 obj 객체로 바인딩된다. 하지만 inner1 함수와 inner2 함수는 내부 함수이기 때문에 일반 함수처럼 this가 바인딩되어 전역 객체가 바인딩된다.

이런 문제를 해결하기 위해서 outer 메소드에서 this의 참조값을 저장하는 변수를 만들어서 내부 함수에서 사용하는 방법을 사용한다. 또한 apply, call 메소드를 이용해서 해결하기도 한다.

#### 생성자 함수 호출 시 this 바인딩 

자바스크립트에서는 어떤 함수든 생성자 함수가 될 수 있는 잠재력을 가지고 있다. 일반 함수도 new 키워드와 함께 호출하면 생성자 함수로 취급된다. 그리고 반대로 생성자 함수를 new 없이 호출하면 일반 함수처럼 동작한다. 그래서 자바스크립트에서 생성자 함수는 다른 일반 함수들과 구분하기 위해 함수명의 첫 글자를 대문자로 쓰는 것을 권장하고 있다.

우선 생성자 함수 호출 시 this 바인딩을 설명하기 전에 생성자 함수가 동작하는 방식을 알아야 한다.

1. 생성자 함수 코드가 실행되기 전에 빈 객체가 생성된다. 그리고 새로 생성된 빈 객체가 this로 바인딩된다. 사실 빈 객체라고 하기엔 조금 애매하다. 왜냐하면 객체는 생성자 함수의 prototype 프로퍼티가 가리키는 객체를 자신의 프로토타입 객체로 설정하기 때문이다.
2. 빈 객체로 바인딩된 this를 통해서 빈 객체의 프로퍼티나 메소드를 동적으로 생성한다.
3. 생성된 객체를 리턴한다. 생성자 함수를 굳이 this를 리턴하지 않아도 알아서 생성된 객체를 리턴한다. 그런데 만약에 this가 아닌 다른 객체를 반환하면 새로 생성한 객체가 아니라 다른 객체를 반환한다.

