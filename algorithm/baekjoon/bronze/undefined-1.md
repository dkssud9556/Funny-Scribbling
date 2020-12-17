# 이항계수

```text
const fs = require('fs');
var [N, K] = fs.readFileSync('./dev/stdin').toString().trim().split(' ');

class CombinationResolver {
	constructor(n, k) {
		this.n = n;
		this.k = k;
	}

	getDivided() {
		let result = 1;
		for (let i = this.n; i > this.n-this.k; i--) {
			result *= i;
		}
		return result;
	}

	getDivisor() {
		let result = 1;
		for (let i = 2; i <= this.k; i++) {
			result *= i;
		}
		return result;
	}

	getCombination() {
		return this.getDivided() / this.getDivisor();
	}
}

console.log(new CombinationResolver(N, K).getCombination());
```

