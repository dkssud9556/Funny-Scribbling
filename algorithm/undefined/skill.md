# \[프로그래머스\] 스킬트리

문제 출처 : [https://programmers.co.kr/learn/courses/30/lessons/49993](https://programmers.co.kr/learn/courses/30/lessons/49993)

프로그래머스의 코딩테스트 연습에서 Level 1 문제를 다 풀고 Level 2 문제를 찾아보다가 풀게되었다. 앞으로 꾸준히 알고리즘 문제를 풀고 글로 기록할 생각이다. 

### 문제 

> 선행 스킬이란 어떤 스킬을 배우기 전에 먼저 배워야 하는 스킬을 뜻합니다.
>
> 예를 들어 선행 스킬 순서가 `스파크 -> 라이트닝 볼트 -> 썬더` 일때, 썬더를 배우려면 먼저 라이트닝 볼트를 배워야 하고, 라이트닝 볼트를 배우려면 먼저 스파크를 배워야 합니다.
>
> 위 순서에 없는 다른 스킬\(힐링 등\)은 순서에 상관없이 배울 수 있씁니다. 따라서 `스파크 -> 힐링 -> 라이트닝  볼트 -> 썬더`와 같은 스킬트리는 가능하지만, `썬더 -> 스파크`나 `라이트닝 볼트 -> 스파크 -> 힐링 -> 썬더`와 같은 스킬트리는 불가능합니다.
>
> 선행 스킬 순서 skill과 유저들이 만든 스킬트리를 담은 배열 skill\_trees가 매개변수로 주어질 때, 가능한 스킬트리 개수를 return 하는 solution 함수를 작성해주세요.
>
> **제한 조건**
>
> * 스킬은 알파벳 대문자로 표기하며, 모든 문자열은 알파벨 대문자로만 이루어져 있습니다.
> * 스킬 순서와 스킬트리는 문자열로 표기합니다.
>   * 예를 들어, `C -> B -> D`라면 "CBD"로 표기합니다. 
> * 선행 스킬 순서 skill의 길이는 1 이상 26 이하이며, 스킬은 중복해 주어지지 않습니다.
> * skill\_trees는 길이 1 이상 20 이하인 배열입니다. 
> * skill\_trees의 원소는 스킬을 나타내는 문자열입니다. 
>   * skill\_trees의 원소는 길이가 2 이상 26 이하인 문자열이며, 스킬이 중복해 주어지지 않습니다.

### 풀이 

```text
function isSkillTree(skill_tree) {
  let idx = skill_tree[0];
  for (let i = 1; i < skill_tree.length; i++) {
    if (idx > skill_tree[i]) {
      return false;
    }
    idx = skill_tree[i];
  }
  return true;
}

function solution(skill, skill_trees) {
  const arr = skill_trees.map((st) =>
    skill.split("").map((sk) => {
      const idx = st.split("").findIndex((v) => v === sk);
      return idx === -1 ? Number.MAX_SAFE_INTEGER : idx;
    })
  );
  return arr.filter((a) => isSkillTree(a)).length;
}
```

1. 우선 스킬트리마다 유효한 스킬트리인지 확인해야 하기 때문에 `skill_trees.map`으로 skill\_trees의 요소를 모두 돈다.
2. 정석적인 스킬트리의 스킬 하나하나가, 주어진 스킬트리에서 어떤 순서로 위치하는지 확인하기 위해서 스킬별로 펼친다. \(`skill.split('').map`\)
3. `findIndex` 메소드를 통해서 정석 스킬트리에 있는 스킬이 각각 어디에 위치하는지 구한다.
4. 만약 `findIndex` 메소드를 통해서 인덱스를 구했는데 -1이라면 그 정석 스킬은 스킬트리에 존재하지 않는다는 것이기 때문에 js에서 가장 큰 숫자를 return한다. \(이 이유는 후술할 것이다.\)
5. 1~4의 과정을 통해서 만들어진 배열의 모습을 예를 들어 표현해보겠다. 만약 정석 스킬트리가 `"CBD"`이고, `["CEFD", "BDF"]`가 skill\_trees에 매개변수로 넘어왔다면 `"CEFD"`는 C가 0번째, B는 없고, D는 3번째 인덱스에 있기 때문에 `[0, Number.MAX_SAFE_INTEGER, 3]`이 될 것이다. 그리고 `"BDF"`는 C가 없고, B는 0번째, D는 1번째에 있으므로 `[Number.MAX_SAFE_INTEGER, 0, 1]`이 될 것이다. \(최종 : `[[0, MAX, 3], [MAX, 0, 1]]`\)
6. arr에 있는 배열들을 돌면서 해당 스킬트리가 유효한지 검사한다. 그리고 걸러낸 배열들의 길이를 반환한다. \(`arr.filter((a) => isSkillTree(a)).length`\)

#### 4번 이유 설명 

내가 생각한 로직은 위치를 구해서 앞에서부터 차례대로 만약에 앞에 있는 스킬의 인덱스가 뒤에 있는 스킬의 인덱스보다 높다면 유효하지 않은 스킬트리로 판정하는 것이었다. 그래서 만약에 맨 처음 스킬이 존재하지 않는데 뒤에 있는 스킬이 2번째에 존재한다면 \[MAX, ... , 2\]가 될 것이고, 앞에 있는 스킬의 인덱스가 뒤에 있는 스킬의 인덱스보다 크기 때문에 유효하지 않은 것으로 판정한다.



