# Git 명령어 정리

* `git init` : 현재 디렉토리를 working directory로 지정하고 레포지토리를 생성한다. 
* `git add [파일이름]` : 수정 사항이 있는 파일을 Staging Area에 등록한다.
* `git reset [파일이름]` : Staging Area에 등록한 파일을 다시 내린다.
* `git status` : 현재 레포지토리의 상황을 보여준다.
* `git commit -m [커밋메시지]` : Staging Area에 등록된 파일들을 커밋으로 남긴다.
* `git push` : 로컬 레포지토리의 커밋 내용들을 리모트 레포지토리로 보낸다.
* `git pull` : 리코트 레포지토리의 커밋 내용들을 로컬 레포지토리로 가져와서 Merge 한다.
* `git clone [주소]` : 리모트 레포지토리에 있는 프로젝트를 컴퓨터에 가져온다.
* `git blame [파일이름]` : 해당 파일이 언제, 누구에 의해서 어떤 변경사항이 있었는지 출력한다.
* `git revert [커밋아이디]` : 해당 커밋으로 상태를 되돌리는 커밋을 만든다.

