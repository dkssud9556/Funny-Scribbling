# Object Type

자바스크립트에서 원시 타입\(number, string, boolean, null, undefined, symbol\)을 제외한 모든 값이 객체다. 따라서 객체에는 배열, 함수, 정규표현식 등이 객체라고 할 수 있다.

### 자바스크립트에서의 객체 

1. 키값 형태의 프로퍼티들을 저장한다. -&gt; 해시 자료구조와 매우 유사함.
2. 객체의 프로퍼티 키로는 string, symbol 타입이 올 수 있다.
3. 객체의 프로퍼티 값으로는 자바스크립트의 모든 타입의 값이 올 수 있다.
4. 프로퍼티 값의 타입이 함수이면, 이를 메소드라고 한다.
5. 객체에 존재하지 않는 프로퍼티에 접근할 경우, undefined를 뱉는다.
6. 이미 만들어진 객체에 동적으로 프로퍼티를 추가하거나 삭제할 수 있다.

### 객체 생성 방법 3가지 

1. Object\(\) 생성자 함수 사용 

   * 자바스크립트에서는 내장으로 Object\(\) 생성자 함수를 제공한다. 이를 이용하여 객체를 생성할 수 있다.

   ```text
   var person = new Object(); // 빈 객체 생성 

   person.name = 'Lee'; // 빈 객체에 name, age, from 프로퍼티 생성 
   person.age = 10;
   person.from = 'Republic of Korea';
   ```

2. 객체 리터럴 방식 

   * 객체 리터럴 방식은 중괄호\({}\)를 이용해서 객체를 생성하는 방식이다.
   * 중괄호\({}\)만 사용하면 빈 객체를 생성하고, 중괄호\({}\) 안에 \(키\):\(값\) 형태로 표기하면 프로퍼티가 추가된 객체를 생성할 수 있다.

   ```text
   var emptyLit = {}; // 빈 객체 생성 

   emptyLit.name = 'Lee'; // 프로퍼티 생성 

   var person = { // 프로퍼티 추가된 객체 생성 
       name: 'Lee',
       age: 10,
       from: 'Republic of Korea'
   };
   ```

3. 생성자 함수 방식 
   * 자바스크립트는 함수를 통해서 객체를 생성할 수 있다. 이러한 함수를 생성자 함수라고 한다.

### 객체 이용 

자바스크립트에서 객체의 프로퍼티에 접근하기 위해서 2가지 표기법을 사용한다.

1. 마침표\(.\) 표기법 

   * 자바나 C++과 같은 언어에서도 익숙한 표기법이다. \(예: 객체.프로퍼티키\)

   ```text
   var person = { name: 'Kim' };
   person.name; // 'Kim'
   ```

2. 대괄호\(\[\]\) 표기법 

   * 접근할 프로퍼티 키를 문자열 형태로 만들고 대괄호로 감싸서 접근한다.

   ```text
   var person = { name: 'Kim' };
   person['name']; // 'Kim'
   person[name]; // undefined
   ```

   * 자바스크립트에서는 대괄호 표기법에서 프로퍼티 이름을 문자열 형태로 만들지 않으면 toString\(\) 메소드를 자동으로 호출해서 이를 문자열로 바꾸려고 시도한다.

### 대괄호 표기법만을 사용해야 하는 경우 

자바스크립트에 대괄호 표기법이 있지만 일반적으로 마침표 표기법을 사용한다. 하지만 자바스크립트에서 대괄호 표기법을 꼭 사용해야만 하는 경우가 있다.

1. 프로퍼티가 표현식인 경우 

   ```text
   var person = { name: 'Lee' };
   person['detail-address'] = '1302dong 603ho';
   person.detail-address; // address is not defined
   ```

   * 위 예에서 객체를 생성한 후에 갱신한 프로퍼티는 -연산자가 있는 포현식이다. 그렇기 때문에 마침표 표기법을 사용하면 person.detail 프로퍼티와 address 변수의 -연산을 수행하는, 의도치 않은 동작을 하게 된다. detail 프로퍼티는 undefined라 치더라도 address는 아예 선언되지 않았기 때문에 오류가 난다.

2. 변수를 통해 프로퍼티에 접근할 경우 

   ```text
   var person = { name: 'Lee', age: 13 }
   for (var prop in person) {
       console.log(person[prop]); // 'Lee' 13
       console.log(person.prop); // undefined
   }
   ```

   * 위처럼 for in문을 사용하면 객체에 있는 모든 프로퍼티를 순회하며 프로퍼티 키를 변수\(prop\)에 저장한다. 이러한 변수를 통해 프로퍼티에 접근하기 위해서는 대괄호 표기법을 사용해야 한다.

