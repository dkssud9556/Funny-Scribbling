# Merge의 종류

Merge도 다 같은 Merge가 아니고, 종류가 있다.

1. Fast-Forward Merge
2. 3-Way Merge

### Fast-Forward Merge

Fast-forward는 어떤 영상이나 소리를 빨리감기한다는 뜻이다. Fast-forward라는 이름에 걸맞게 Merge를 하는 모습이 빨리감기를 하는 것 같다.

![](../.gitbook/assets/image%20%284%29.png)

위 상태에서 dev 브랜치를 Merge하면 어떻게 될까? 새로운 Merge Commit이 생길까?

![](../.gitbook/assets/image%20%285%29.png)

위와 같이 새로운 커밋이 만들어지는 일 없이 그냥 master 브랜치가 dev 브랜치가 가리키는 커밋을 가리키게 된다.

이러한 Fast-Forward Merge는 커밋 히스토리가 같은 선상에 있는 브랜치를 Merge할 때 이루어진다.

### 3-Way Merge

![](../.gitbook/assets/image%20%287%29.png)

3-Way Merge는 위 그림의 1, 2, 3을 고려하여 Merge를 수행한다. 그리고 그림을 보면 알 수 있듯이 Fast-Forward Merge와 달리 새로운 Merge Commit이 생긴다.

#### 1, 2, 3의 의미 

1. 두 갈래로 갈라지기 전 공통 조상이 되는커밋 
2. 한 브랜치가 가리키는 커밋 
3. 다른 브랜치가 가리키는 커밋 

아래 표는 다양한 상황별 Merge 결과를 나타내는 표이다.

| 경우  | base | master | dev | Merge Result |
| :--- | :--- | :--- | :--- | :--- |
| case1 | A | A | B | B |
| case2 | 1 | 2 | 1 | 2 |
| case3 | "Hello" | \(공백\) | "Hello" | \(공백\) |
| case4 | "Bye" | "fighting" | "Please" | Merge Conflict |

#### 방식 

* base 내용과 비교해서 달라진 부분이 있는 것이 우선시 된다.
* 두 브랜치 모두 달라진 부분이 있으면 Conflict가 발생한다. 

