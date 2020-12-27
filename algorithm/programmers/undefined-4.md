# 프린터

```text
function solution(priorities, location) {
  let answer = 0;
  while (true) {
    if (priorities[0] < Math.max(...priorities)) {
      priorities.push(priorities.shift());
      location = loc(location, priorities.length);
    } else {
      priorities.shift();
      answer++;
      if (location === 0) return answer;
      location = loc(location, priorities.length);
    }
  }
}
```

