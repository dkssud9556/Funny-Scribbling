# 셀프 넘버

```text
const numbers = new Array(10001).fill(true);
numbers[0] = false;

for (let i = 1; i <= 10000; i++) {
	numbers[i+String(i).split('').map(v => Number(v)).reduce((p, c) => p + c, 0)] = false;
}

numbers.forEach((v, i) => {
	if (v) console.log(i);
});
```

