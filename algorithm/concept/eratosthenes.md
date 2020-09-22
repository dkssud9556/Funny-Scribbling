# Eratosthenes Sieve

에라토스테네스의 체는 많은 수들 중에서 소수가 아닌 것을 걸러낼 때 사용하는 알고리즘이다. 즉, 소수를 구하는 문제에서 많이 사용된다. 

#### 알고리즘 

1. 1은 소수가 아니므로 없앤다. 
2. 2부터 시작해서 각 수의 배수들을 지운다. \(자기 자신과 이미 지워진 수 제외\) 

에라토스테네스의 체도 유클리드 호제법처럼 매우 간단한 알고리즘을 가지고 있다. 

다음은 자바스크립트로 1부터 100까지의 수에서 소수들을 리스트로 뽑아내는 알고리즘을 구현한 것이다. 

```text
function getPrimeNumberList(n) {
  let che = [];
  for (let i = 2; i <= n; i++) che[i] = i;
  for (let i = 2; i <= n; i++) {
    if (che[i] === 0) continue;
    for (let j = i * 2; j <= n; j += i) che[j] = 0;
  }
  return che.filter((v) => v);
}

getPrimeNumberList(100);
```

