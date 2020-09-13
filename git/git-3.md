# Git의 3가지 작업 영역

Git에는 아래 3가지의 작업 영역이 있다. 

1. Working Directory
2. Staging Area
3. Repository

### Working Directory

**Working Directory** 는 말그대로 작업하고 있는 디렉토리를 뜻한다. 

### Staging Area

**Staging Area**는 `git add` 명령어를 통해 추가한 파일들이 존재하는 영역이다. 커밋을 하면 이 **Staging Area**에 있는 파일들만 커밋에 반영된다. 

### Repository

**Repository**는 Working Directory가 변경된 이력들이 저장된 영역이다. `git init` 명령어를 실행했을 때 생성되는 `.git` 디렉토리가 **Repository**이다. 

