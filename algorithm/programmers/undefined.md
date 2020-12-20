# 소수 찾기

```text
function solution(n) {
  const che = [];
  for (let i = 2; i <= n; i++) che[i] = i;
  for (let i = 2; i <= n; i++) {
    if (che[i] === 0) continue;
    for (let j = i * 2; j <= n; j += i) che[j] = 0;
  }
  return che.filter((v) => v).length;
}
```

