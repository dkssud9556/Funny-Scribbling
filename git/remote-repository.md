# Remote Repository의 브랜치

깃허브 리모트 레포지토리를 만들고 나서 `git remote add origin [github 주소]` 와 `git push -u origin master` 명령어를 통해서 기본적인 설정을 한다. 

### git remote add origin \[remote repo 주\]

`git remote add origin [remote repo 주소]`의 의미는 해당 리모트 레포지토리를 origin이라는 이름으로 등록하겠다는 뜻이다. 

름을 origin이 아닌 다른 것으로 해도 되지만 리모트 레포지토리를 최초로 추가할 때 origin으로 추가하는 것이 관례이다. 

### git push -u origin master

`git push -u origin master` 명령어는 현재 로컬 레포지토리에 있는 master 브랜치의 내용을 origin이라는 리모트 레포지토리로 push한다는 뜻이다. 

#### -u 옵션 

-u는 --set-upstream의 약자다. 

-u 옵션을 주면 로컬 레포지토리에 있는 master 브랜치가 origin에 있는 master 브랜치를 tracking하도록 설정된다.

tracking connection이 설정되면 로컬 레포지토리가 master 브랜치에 있을 때 `git push`만 써도 origin의 master 브랜치를 대상으로 push가 수행된다. \(`git pull`도 마찬가지\)

만약 -u 옵션을 주지 않으면 `git push origin master:master`와 같은 형식으로 push를 해야 한다.

