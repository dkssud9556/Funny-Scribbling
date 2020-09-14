# JDK, JRE, JVM

JDK, JRE, JVM의 차이에 대해서 원래 궁금증을 가지고 있었는데 미루고 있다가 오늘 한 번 공부해보았다. 

우선 결론부터 말하자면 JDK가 JRE를 포함하고, JRE가 JVM을 포함하는 포함관계를 가지고 있다. 

![https://javainterviewgoal.blogspot.com/2019/07/what-is-jdk-jre-and-jvm.html](../.gitbook/assets/image%20%281%29.png)

위와 같은 포함관계를 가지고 있다. 가장 아래에 짱박혀있는 JVM부터 JRE, JDK순으로 정리해보았다. 

### JVM \(Java Virtual Machine\)

* **JVM**을 해석하면 자바 가상 머신이다. **JVM**은 자바 컴파일러를 통해 컴파일된 자바 바이트코드\(.class\)를 해석해서 실행시켜준다. 
* **JVM**은 OS마다 따로 만들어져 있으며, 이를 통해 **JVM**이 있으면 한 번 컴파일한 자바 프로그램을 모든 OS에서 실행시킬 수 있다는 장점이 있다. 

### JRE \(Java Runtime Environment\)

* **JRE**는 `JVM + Java Library`로 구성된 자바 구동 환경이다. 
* 자바 언어를 사용해서 개발하는 개발자가 아니라 자바 코드로 된 프로그램을 실행할 사용자라면 **JRE**만 설치하면 된다.

### JDK \(Java Development Kit\)

* **JDK**는 JRE + Development Tool로 구성된 자바 개발자를 위한 Kit이다. 
* **JDK**에는 자바 컴파일러 \(javac.exe\), 자바 디버거 등이 포함되어 있다. 
* **JDK**는 버전이 올라감에 따라 새로 생기는 기능이 있고, 없어지는 기능이 있다. 
* **JDK**의 종류 
  * OpenJDK : OracleJDK와 거의 비슷한 성능. 언제나 무료.
  * OracleJDK : 개인적으로 사용할 때는 무료. 기업 등에서 상업적으로 이용할 때는 유료.

