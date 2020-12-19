# 평균

```text
const fs = require('fs');
var [n, scores] = fs
	.readFileSync('/dev/stdin')
	.toString()
	.split('\n')
	.map((v, i) => {
		if (i == 0) {
			return Number(v);
		}
		return v.split(' ').map(c => Number(c));
	});

const max = Math.max(...scores);
const newScores = scores.map(score => score/max*100);
console.log(newScores.reduce((p, c) => p + c, 0) / n);
```

