# Dynamic Programming

### Dynamic Programming이란? 

Dynamic Programming은 큰 문제를 작은 문제로 나누어서 문제를 해결하는 방식의 알고리즘이다.

### 분할 정복과의 차이점 

Dynamic Programming의 설명을 들으면 분할 정복과 차이점이 무엇인지 궁금해진다.

Dynamic Programming은 큰 문제를 작은 문제로 나누었을 때 작은 문제들이 중복적으로 나타날 때 사용되고, 분할 정복은 그렇지 않을 때 사용된다. 

따라서 Dynamic Programming은 이미 해결한 작은 문제의 답을 재사용할 수 있다.

### Dynamic Programming의 조건 

찾아보니까 Dynamic Programming의 조건이 나왔다. 내가 생각하기에 이 조건이라는건 Dynamic Programming을 적용할 수 있는 문제의 조건을 뜻하는 것 같다.

1. 큰 문제를 작은 문제로 분할할 수 있어야 한다.
2. 작은 문제들의 답은 항상 동일하다. -&gt; 메모이제이션 이

### Memoization

![&#xBCF4;&#xD1B5;&#xC758; &#xD53C;&#xBCF4;&#xB098;&#xCE58; &#xC218; &#xAD6C;&#xD604; &#xD568;&#xC218;](../../.gitbook/assets/image%20%282%29.png)

위 코드는 그냥 보통의 피보나치 수를 구현하는 재귀함수이다. 이 함수는 같은 함수를 몇번이나 계속 호출하기 때문에 n이 커지면 속도가 급격하게 떨어진다. 시간 복잡도는 O\(2^n\)이다. 

![&#xBA54;&#xBAA8;&#xC774;&#xC81C;&#xC774;&#xC158;&#xC744; &#xC801;&#xC6A9;&#xD55C; &#xD53C;&#xBCF4;&#xB098;&#xCE58; &#xC218; &#xAD6C;&#xD604; &#xD568;&#xC218;](../../.gitbook/assets/image%20%283%29.png)

위 코드는 피보나치 수를 구하는 재귀함수인건 변함이 없지만 답을 저장할 배열을 만들어놓고 작은 문제들의 답을 저장한다. 그리고 다음에 같은 문제가 오면 저장해놨던 답을 그대로 반환한다. 이러면 속도가 매우 빨라진다.  시간 복잡도는 O\(n\)이다.

### Dynamic Programming의 구현 방식 2가지 

1. Top-Down 방식 
2. Bottom-Up 방식 

