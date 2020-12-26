# 최대 수식화

```text
function solution(expression) {
	const priorities = [
		['*', '+', '-'],
		['*', '-', '+'],
		['+', '*', '-'],
		['+', '-', '*'],
		['-', '+', '*'],
		['-', '*', '+']
	];
	let results = [];
	for (let priority of priorities) {
		const result = calculate(priority, 0, expression);
		results.push(Math.abs(result));
	}
	return Math.max(...results);
}

function calculate(priority, n, expression) {
	let returnValue;
	if (n === 2) return eval(expression);
	if (priority[n] === '*') {
		returnValue = eval(expression.split('*').map(v => calculate(priority, n+1, v)).join('*'));
	}
	if (priority[n] === '+') {
		returnValue = eval(expression.split('+').map(v => calculate(priority, n+1, v)).join('+'));
	}
	if (priority[n] === '-') {
		returnValue = eval(expression.split('-').map(v => calculate(priority, n+1, v)).join('-'));
	}
	return returnValue;
}
```

