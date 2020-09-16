# Git HEAD와 reset

`git log` 명령어를 사용해서 git history를 살펴보면 **HEAD**라는 글자를 볼 수 있다. **HEAD**는 가장 최근에 한 커밋을 가리킨다. 

**HEAD**를 옮겨서 가장 최근것이 아니라 과거의 커밋으로 되돌리고 싶을 때는 `git reset` 이라는 명령어를 사용해야 한다. 정확히는 `git reset [옵션] [커밋 ID]` 형식으로 사용한다. 

커밋 ID는 `git log` 명령어를 통해서 얻을 수 있다. 

예를 들어서 `git reset --hard fad3` 을 입력하면 커밋 ID가 fad3...인 과거의 커밋으로 **HEAD**가 옮겨가고, 그 이후에 했던 커밋들은 사라진다. 즉, `git reset` 명령어는 아예 과거의 커밋으로 돌아가기 위해서 사용한다. 

### git reset의 옵션 3가지 

| git reset \[옵션\] \[커밋 ID\] | Working Directory | Staging Area | Repository |
| :--- | :--- | :--- | :--- |
| --soft | 안 바뀜  | 안 바뀜  | HEAD가 \[커밋 ID\] 커밋을 가리 |
| --mixed | 안 바뀜  | \[커밋 ID\] 커밋처럼 바뀜  | HEAD가 \[커밋 ID\] 커밋을 가리 |
| --hard | \[커밋 ID\] 커밋처럼 바뀜  | \[커밋 ID\] 커밋처럼 바뀜  | HEAD가 \[커밋 ID\] 커밋을 가리 |

### 커밋 후 Staging Area의 상태 

Working Directory에 있는 파일을 수정하고 `git add` 명령어를 사용해서 Staging Area에 등록하고, 커밋을 한다. 

커밋을 한 후에 Staging Area의 파일들은 사라질까, 아니면 그대로 남을까? 

정답은 **그대로 남는다**이다.

`git add`를 할 때마다 새로운 파일이 추가되거나 원래 있던 파일이 새로운 버전으로 교체가 될 뿐이다. 

