# Array

자바스크립트에서 배열은 특별한 객체와 같다. 자바나 C같은 언어의 배열과 같은 역할을 하지만 세세한 부분이 다르다.

1. 배열 크기를 지정하지 않아도 된다.
2. 저장하는 데이터의 위치, 타입은 크게 상관이 없다.

### 배열 생성 방법 

1. 배열 리터럴 

   * 객체 리터럴과 비슷하게 대괄호\(\[\]\)를 이용해서 배열을 생성하는 방법이다.
   * 대괄호\(\[\]\)만 쓰면 빈 배열을 생성하고, 대괄호\(\[\]\) 안에 요소들을 나열하면 순서대로 배열의 요소가 된다.

   ```text
   var arr = []; // 빈 배열 생성 
   arr[0] = 'banana';
   arr[1] = true;
   arr[2] = 19;
   arr; // ['banana', true, 19]

   var arr2 = ['banana', true, 19];
   arr2; // ['banana', true, 19]
   ```

2. Array\(\) 생성자 함수 

   * Object\(\) 생성자 함수처럼 배열을 생성하기 위한 내장 Array\(\) 생성자 함수가 있다.
   * Array\(\) 생성자 함수의 인수로 숫자 하나를 넘기면 그 숫자의 길이에 해당하는 빈 배열이 생성된다. 인수로 여러 요소를 넘기면 그 요소들을 지닌 배열이 생성된다.

   ```text
   var arr = new Array(3);
   arr; // [empty x 3]

   var arr2 = new Array(12, 'b', true, 3);
   arr2; // [12, 'b', true, 3]
   ```

### 배열 요소 생성 

배열의 요소도 객체 프로퍼티를 동적으 추가할 수 있는 것처럼 동적으로 추가할 수 있다.

현재 배열의 크기를 넘어가는 인덱스에 요소를 추가하면 그만큼 배열의 길이가 늘어난다.

```text
var arr = [];
arr[0]; // undefined

arr[0] = true;
arr[12] = 'twelve';
arr[15] = 305;
arr; // [true, empty x 11, 'twelve', empty x 2, 305]
arr.length; // 16
```

빈 부분은 접근하면 undefined를 반환한다. 그리고 저런 빈 부분은 메모리가 할당되지 않는다고 한다.

### length 프로퍼티 

자바스크립트의 모든 배열은 length 프로퍼티를 가지고 있다. length 프로퍼티는 배열 요소의 개수를 말하긴 하지만 사실 배열의 가장 큰 인덱스에 1 더한 값이라고 하는게 더 정확하다.

length 프로퍼티는 배열의 가장 인덱스가 변함에 따라 변화한다.

그리고 놀랍게도 length 프로퍼티는 read-only가 아니기 때문에 개발자가 명시적으로 length 프로퍼티의 값을 변경할 수 있다.

```text
var arr = [false, 13];
arr.length; // 2

arr.length = 6;
arr; // [false, 13, empty x 4]

arr.length = 1;
arr; // [false]
```

위 예를 보면 알 수 있듯이 현재 배열의 length 값보다 큰 값을 할당하면 그만큼 빈 공간이 생긴다.

반대로 현재 length 값보다 작은 값을 할당하면 그만큼 배열의 요소가 삭제된다.

### 배열에 프로퍼티 생성 

아까 앞부분에서 배열은 특별한 **객체**라고 했다. 그렇기 때문에 배열에도 객체처럼 프로퍼티를 생성할 수 있다.

```text
var arr = ['money', 1300, true];
arr.length; // 3

arr.name = 'Lou';
arr.age = 48;

arr.length; // 3
```

위 예를 보면 배열에 프로퍼티를 생성해도 length 프로퍼티에는 영향을 주지 않는다는 것을 알 수 있다.

![&#xBC30;&#xC5F4;&#xB3C4; &#xD0A4;&#xAC12; &#xD615;&#xD0DC;&#xB77C;&#xB294; &#xAC83;&#xC744; &#xC54C; &#xC218; &#xC788;&#xB2E4;.](../.gitbook/assets/image%20%288%29.png)

### for in, for of

객체의 프로퍼티를 열거할 때 for in문을 사용한다. 

배열도 객체이기 때문에 for in문을 사용할 수 있다. 하지만 아래 예를 보면 문제점을 알 수 있다.

```text
var arr = ['money', 1300, true];
arr.name = 'Kim';
arr.age = 15;
for (var i in arr) {
    arr[i]; // 'money', 1300, true, 'Kim', 15
}
```

배열의 요소들 뿐만 아니라 프로퍼티들도 다 열거하는 것을 알 수 있다.

배열의 요소들만을 열거하기 위해서는 length 프로퍼티를 이용해서 for문을 돌리는 방법도 있지만, ES6에서 for of문이라는 것이 추가됐다. for of문은 프로퍼티는 제외한 요소들만을 열거한다.

```text
for (var i of arr) {
    arr[i]; // 'money', 1300, true
}
```

### 배열 요소 삭제 

1. delete 연산자 

   ```text
   delete arr[0];
   arr; // [empty, 1300, true]
   ```

   * delete 배열\[인덱스\]로 해당 인덱스의 요소를 빈 공간으로 만든다. 요소가 아예 삭제되지는 않는다.

2. splice\(\) 메소드 

   ```text
   arr.splice(1, 1);
   arr; // [empty, true]

   arr.splice(0, 1, 'banana', false, 13);
   arr; // ['banana', false, 13, true]
   ```

   * 배열.splice\(인덱스, 개수, 요소들\) : splice 메소드를 호출한 배열을 인덱스에서 개수만큼 요소를 삭제하고, 삭제한 공간에 요소들을 추가한다.

