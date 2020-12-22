# 문자열 압축

```text
function solution(s) {
	if (s.length === 1) return 1;
	let compressed = [];
	for (let i = 1; i <= Math.floor(s.length/2); i++) {
		compressed.push(compress(s, i));
	}
	return Math.min(...compressed.map(v => v.length));
}

function compress(s, num) {
	let sliced = slice(s, num);
	let returnValue = '';
	let count = 1, prev = sliced[0];
	for (let i = 1; i < sliced.length; i++) {
		if (prev !== sliced[i]) {
			returnValue += count === 1 ? prev : count + prev;
			count = 1;
			prev = sliced[i];
			continue;
		}
		count++;
	}
	return count === 1 ? returnValue + prev : returnValue + count + prev;
}

function slice(s, num) {
	let sliced = [];
	for (let i = 0; i < s.length; i += num) {
		sliced.push(s.slice(i, i+num));
	}
	return sliced;
}
```

