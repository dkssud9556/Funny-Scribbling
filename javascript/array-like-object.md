# Array-like object

자바스크립트에는 **유사 배열 객체**라는 것이 있다. 유사 배열 객체는 length 프로퍼티를 가지고 있는 객체를 의미한다.

**유사 배열 객체의 가장 큰 특징 : 객체임에도, 자바스크립트 표준 배열 메소드를 사용할 수 있다.**

```text
var obj = {
    name: 'Lee',
    age: 17,
    length: 2
}; // 유사 배열 객체 생성 

obj.push(false); // 오류 발생 
```

위 예에서 유사 배열 객체를 생성했다. 그리고 push 메소드를 호출했더니 오류가 발생한다. 왜냐하면 당연히 obj는 Array.prototype을 상속받고 있지 않기 때문이다.

### apply\(\) 메소드 

위 예에서 유사 배열 객체에서 바로 push 메소드를 호출하면 오류가 난다는 것을 알게 됐다. 유사 배열 객체에 자바스크립트 표준 배열 메소드를 사용하기 위해서는 apply\(\) 메소드를 사용해야 한다.

```text
var obj = {
    name: 'Kim',
    age: 19,
    length: 2
};

Array.prototype.push.apply(obj, [false]);
obj; // { '2': false, name: 'Kim', age: 19, length: 3 }
```

