---
title: JVM? JRE? JDK??
date: 2024-02-20 00:00:00 +0900
categories: [⚙️Back-End, ☕Java]
tags: [Java,
자바,
JVM,
JRE,
JDK,
컴파일,
인터프리트,
compiled,
interpreted,
]     
---   
## 공부 배경  
Java를 공부하면서 **`JVM`**,**`JRE`**,**`JDK`**에 관해서 들어봤을 것이다. 특히, **자바가 플랫폼에 독립적**이라고 설명하며, 위 세 단어가 자주 언급되었을 것이다. 이 개념들을 정리하면서 자바가 왜 플랫폼에 독립적이라고 하는지 알아보자.  
  
---
## Compile vs Interpret  
우리는 C언어와 Java 같은 우리가 읽고 작성할 수 있는 프로그래밍 언어로 코드를 짠다. 하지만 이 언어들을 컴퓨터는 바로 읽어들이지 못한다. 그렇기 때문에 컴퓨터가 알아들을 수 있는 기계어로 바꾸어 주는 작업이 필요하다.  
여기서 우리는 컴퓨터가 알아들을 수 있는 기계어로 **<span style = "color : cyan">번역</span>**할지 **<span style = "color : orange">통역</span>**할지에 따라, **<span style = "color : cyan">Compile</span>**되는 언어와 **<span style = "color : orange">Interpret</span>**되는 언어로 나눈다.  
  
### Compile 
컴파일은 프로그래밍 언어로 코드를 짜고 나서, 실행하기 전에 **미리** 컴퓨터가 읽을 수 있는 언어로 번역하는 작업을 말한다.  
  
**<span style = "color : blue">장점</span>**  
* 컴파일이 완료된 실행 파일은 컴퓨터에서 빠르게 실행할 수 있다.  
* 0과 1로 된 기계어로 번역되기 때문에 프로그램의 코드가 유출되지 않는다.   
* 컴파일 에러(문법적 에러)와 관련된 에러를 초기에 발견할 수 있다.  
  
**<span style = "color : red">단점</span>**  
* 코드를 수정하면 컴파일을 다시 해야한다.  
* 소스 파일 전체를 컴파일해야 하므로 용량이 크다.  
* 모든 소스파일을 한꺼번에 번역하기 때문에 비교적 시간이 걸린다.  
* 목적 파일을 생성하기 위해 메모리를 사용한다.  
* 특정 시스템에서 만들어진 실행 파일이 다른 시스템에서는 실행되지 않는 경우가 많다. 👉 플렛폼에 종속적이다.  
  
### Interpret  
인터프리트언어는 사람이 작성한 코드를 그대로 컴퓨터에게 건내주면 통역을 해주는 프로그램인 인터프리터가 **실시간**으로 컴퓨터에게 읽어준다.  
  
**<span style = "color : blue">장점</span>**  
* 메모리를 사용하지 않는다.  
* 시스템 간의 이식성이 뛰어나다.  
* 전체 코드를 다시 컴파일할 필요가 없기 때문에 코드 수정에 용이하다.  
  
**<span style = "color : red">단점</span>**   
* 매번 통역 과정을 거치면서 실행 속도가 비교적 느리다.  
* 중간 코드로 해석되기 때문에 프로그램의 코드가 유출 될 수 있다.  
  
### 정리  
개발자가 작성한 코드를  **<span style = "color : cyan">미리 번역</span>**해 두었다가, 프로그램을 실행할 때 컴퓨터가 번역된 코드를 한번에 읽는 언어는  **<span style = "color : cyan">컴파일되는 언어</span>**  
반대로, 개발자가 코딩을 하고 난 후, 그 코드를 그대로 갖고 있다가  프로그램을 실행하는 그때 그때에 **<span style = "color : orange">실시간으로 통역</span>**하는 언어는 **<span style = "color : orange">인터프리트 언어</span>**  
  
---  
## Java는 플랫폼에 독립적이다.  
**Java**는 **<span style = "color : cyan">미리 번역</span>**해 두는 **<span style = "color : cyan">컴파일</span>**되는 언어에 속한다. 하지만, Java는 C와 같은 기존의 컴파일 언어들과는 다른 부분이 있다.  
  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/354e5153-1182-4033-a028-f7ee9237dbcf)    
일반 컴파일 언어의 경우, 위 그림과 같이 운영체제(OS) 마다 쓰는 기계언어가 다르기 때문에, 각각의 기계언어로 컴파일 해야한다.<br>👉플랫폼에 종속적이다.  
  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/a70d9993-4d43-4b8d-8b9a-db4ff9f041f6)  
Java의 경우 위 그림과 같이 코드를 실행할 각 운영체제에 **JVM(Java Virtual Machine)**을 두고, 코드를 작성하여 하나의 **Java ByteCode**로 컴파일 하여 각각에게 보내면, JVM이 공통의 기계어 번역본을 가지고 실행한다. 자바 개발자들은 자바를 실행할 컴퓨터 및 기기에 이 JVM 프로그램만 설치해 둔다면 어떤 언어로 컴파일 할지 신경쓰지 않아도 된다. 👉 **플랫폼에 독립적이다.**  
  
---  
## JVM  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/7844c6b4-c22b-48d8-9aa6-8feb489511bf)  

**JVM**이란 **J**ava **V**irtual **M**achine의 약자로 *'자바를 실행하기 위한 가상 기계'*이다.  
**Java는 플랫폼에 독립적이다**는 특징을 가지고 있는데, 바로 이 **JVM**을 통해 OS에 종속 받지않고 Java언어로 프로그래밍 된 소프트웨어 실행할 수 있기 때문이다.  
  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/c62e4ad0-5307-4b4a-b10f-b488e8ce51cc)    
Java언어로 작성된 코드(.java)는 **javac**라는 컴파일러를 통해 Java ByteCode<sup>[1](#f1)</sup>로 컴파일 되고(.class), 이는 각 컴퓨터에 설치된 JVM에 의해 실행된다.  
위 그림과 같이 JVM의 구성요소에는 여러가지가 있지만, 이는 중요한 내용이 많아 따로 정리해보겠다.      
<span style="font-size: 10px"><b id="f1">1</b>: JVM이 이해할 수 있는 언어로 변환된 자바 소스코드</span>  

---  
## JRE  
JRE는 **J**ava **R**untime **E**nvironment의 약자로 *'자바 언어로 된 소프트웨어가 컴파일 및 빌드 후, 이가 실행 될때 필요한 환경요소'*이다.  
JRE는 JVM을 포함하고 있다. 즉, Java언어로 작성된 코드가 실행되기 위해서는 JRE가 설치되어 있어야 한다. JRE는 JVM 외에도 몇가지를 더 포함하는데, 그 중에서도 가장 핵심적인 것은 **표준 라이브러리(Library)**이다. Java Class Libraries 는 Java 를 실행시키는데 필수적인 라이브러리로, java.io , java.util , java.thread 등 작동에 필수적인 요소들을 가지고 있다.  
> **JRE = JVM + Library**  

---  
## JDK  
JDK는 **J**ava **D**evelopment **K**it의 약자로 *'최종 사용자가 아닌 프로그래머들을 위한 기능도 같이 탑재된 Java용 개발 키트'*이다.  
JRE는 개발에 사용되는 것이 아닌 실제 프로그램을 구동시키는 데 집중을 하고 있다. 따라서 Java 코드가 주어져도 이를 분석하거나 클래스 파일로 변환하는 일은 할 수 없다. Java Compiler를 비롯한 개발에 필요한 요소들은 없기 때문에 개발을 하기 위해서는 다른 요소들이 더 필요합니다. 이를 제공해주는 것이 JDK이다. JRE에 있는 모든 것 뿐만 아니라javac(자바 코드 컴파일)와 jdb(자바 디버깅), jar(서로 연관있는 클래스들을 하나의 jar파일로 묶어줌) 과 같은 도구도 있다.   
> **JDK = JRE + Development Tools**  

---  
## 정리  
JDK는 자바 프로그램을 실행, 컴파일, 개발하기 위한 도구 모음이다. JRE, JVM를 모두 포함한다.
JRE는 자바 프로그램을 실행할 수 있게 하는 도구이다. JVM을 포함하고 있다.  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/e4521c07-2c62-4a2a-bd88-a89d1357b726)      

