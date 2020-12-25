# 영어 끝말잇기

```text
function solution(n, words) {
	const checkList = { [words[0]]: true };
	let answer = [0, 0];
	for (let i = 1; i < words.length; i++) {
		const prev = words[i-1];
		if (words[i][0] !== prev[prev.length-1]) {
			answer = [i%n + 1, Math.ceil((i+1)/n)]; break;
		}
		if (checkList[words[i]]) {
			answer = [i%n + 1, Math.ceil((i+1)/n)]; break;
		}
		checkList[words[i]] = true;
	}
	return answer;
}
```

