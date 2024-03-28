---
title: C# 프로그램 구조
date: 2024-03-28 00:00:00 +0900
categories: [⚙️Back-End, 🕹️C#]
tags: [C#,
.NET,
OOP,
클래스,
인스턴스,
메서드,
VisualStudio2019,
]     
---   
## 목차  
  
> 1. [프로젝트 만들기](#프로젝트-만들기)  
> 2. [클래스의 정의](#클래스의-정의)  
> 3. [메서드의 정의](#메서드의-정의)  
> 4. [Main() 메서드의 역할](#main-메서드의-역할)  
  
---  
## 프로젝트 만들기  
### VisualStudio2019  
1. 새 프로젝트 만들기  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/6b014fd0-967f-4255-af8a-f63a8a56d154)  
2. `콘솔 앱(.NET Framework)`을 선택하고 `다음`을 눌러준다.  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/082afb20-9bf1-40ae-9120-d7d31d828105)  
3. 프로젝트 이름을 입력한 후, 프로젝트를 만들어준다.  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/3142cf75-858c-46f6-a85a-1c0743d90960)  
4. 아래와 같이 프로젝트가 만들어진 것을 확인할 수 있다.  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/2c4ce112-7d20-450e-aa21-169715ab6504)  

---  
### 프로젝트 결과물  
프로젝트는 하나 이상의 **`.cs`**파일로 구성된다.  
프로젝트를 컴파일한 결과물은 두 가지 형태로 구분된다.  
* **`Main()`**함수를 가지고 있는 프로젝트는 **`.EXE`**파일 생성. 👉 이는 중간 언어인 **IL**이 된다.  
* **`Main()`**함수가 <span style="color : red">없는</span> **`.DDL`** 라이브러리 파일 생성. 👉 재사용이 가능한 클래스를 모아 놓은 것.  
* **`.EXE`**와 **`.DDL`**을 **어셈블리**라고 칭한다.  
 
---  
## 클래스의 정의  
### 클래스  
* 실세계에 존재하는 사물 또는 개념을 모델링(abstraction)한 것.  
* 클래스를 C#에서는 **타입(Type)**이라고 함.  
* 붕어빵틀, 건물 설계를 위한 설계도면으로 생각하면 이해가 쉽다.  
* **선언부**

### 인스턴스  
* 클래스가 타입으로 사용되어 프로그램에서 실행할 수 있도록 준비된 상태.  
* 붕어빵, 설계도면의 실체인 건물로 생각하면 이해가 쉽다.  
* **실행부**  
  
---  
### 객체 지향 프로그래밍 순서  
1. **`클래스(Class)`**라는 설계 도면을 우선 만든다. 👉 **`타입(Type)`**  
2. **`타입(Type)`**을 사용할 **`인스턴스`**를 선언한다.  
  
---  
### 클래스 선언  
```cs
접근제한자 예약어 클래스명
{
    속성 정의; // 프로퍼티(Property)
    행위 정의; // 메서드(Method) 
}
```  
클래스는 하나의 **`.cs`**파일에 하나 이상 선언 할 수 있다.  
- 하나의 **`.cs`**파일에 하나의 클래스를 정의하는 것이 유지/보수를 고려할 때 바람직하다.  
  
### 예제 3-1  
```cs
class HelloWorld
{
    static void Main()
    {
        System.Console.WriteLine("Hello World");
    }
}
```  
* **`System.Console`**이라는 **`클래스(Class)`**의 `WriteLine()`이라는 `메서드(Method)`를 사용한다는 뜻이다.  
* **`System.`**을 지우면 아래와 같은 빨간 밑줄과 함께 오류가 발생하는데, `Ctrl`+`.`을 눌러주어 `using System;`으로 **`System`** 클래스를 불러온다.  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/ebb34134-746b-4e73-98c1-b1adeef8ca3f)  

```cs
using System;

class HelloWorld
{
    static void Main()
    {
        Console.WriteLine("Hello World");
    }
}

```  
    
---
### 결과  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/08f845fa-44e6-447d-afa3-0cdd14549021)  
  
---  
### 예제 3-1 Decompile  
**`Decompiler`**를 사용하여 실행 파일을 Decompile하면, 실행 파일의 소스코드를 확인할 수 있다. `예제 3-1`을 Decompile하면 다음과 같다.  
```cs
using System;
internal class HelloWorld
{
 public HelloWorld()
 {
 }
 static void Main()
 {
    Console.WriteLine("Hello World");
 }
}
```  
* **`internal`**은 기본 접근 제한자이다. 이는 같은 어셈블리 내에서는 접근할 수 있지만, 다른 어셈블리에서는 접근할 수 없음을 의미한다.  
* `public HelloWorld(){}`는 컴파일러가 자동으로 추가하는 기본 생성자이다.  
  
---  
## 메서드의 정의  
### 메서드의 역할  
* 모든 실행문(명령문)은 메서드에서만 실행 가능  
* 객체의 로직을 명령 문으로 구현  
* 함수, 서브루틴, 프로시저라고도 불림  
* 메서드는 다른 메서드에서 호출되는 형식으로 사용됨  
* 메서드는 C 언어와 동일하게 재사용됨  
* <span style ="color:red">다른 클래스에 있는</span> 메서드 호출은 `클래스`or`인스턴스`or`변수``.메서드명(파라미터)` 방식으로 호출  
* <span style ="color:blue">같은 클래스에 있는</span> 메서드는 `메서드명(파라미터)`으로 호출  
  
---  
### 메서드 선언  
* 메서드가 값을 반환하지 않는 경우  
```cs
접근제한자 void 메서드명 (타입명 매개변수명, ...)
{
    (return;)
}

```  
* 메서드가 값을 반환 하는 경우  
```cs
접근제한자 반환타입 메서드명 (타입명 매개변수명, ...)
{
    return 반환타입;
}

```  
### 예제 3-1  
* 같은 클래스 내의 메서드(값 반환 X)를 호출하는 방법
```cs

using System;

class HelloWorld
{
    static void Main()
    {
        PrintHello();
    }
    
    static void PrintHello()
    {
        Console.WriteLine("Hello World");
    }
}
  
```  
  
* 메서드에 파라미터 값(string)을 보내는 경우    
```cs

using System;

class HelloWorld
{
    static void Main()
    {
        PrintHello("Hello World");
    }
    
    static void PrintHello(string str)
    {
        Console.WriteLine(str);
    }
}

```  

* 메서드를 다른 방법으로 재사용 하는 경우  
```cs

using System;

class HelloWorld
{
    static void Main()
    {
        PrintHello("Hello World");
        PrintHello("안녕 세상");
    }
    
    static void PrintHello(string str)
    {
        Console.WriteLine(str);
    }
}


```   
  
* 다른 클래스의 메서드를 사용하는 경우  
```cs

using System;

class HelloWorld
{
    static void Main()
    {
        AA aa = new AA();
        aa.PrintHelloAA("Hello World");
    }

}

class AA
{
    public void PrintHelloAA(String str)
    {
        Console.WriteLine(str);
    }
}

```  
  
---  
## Main() 메서드의 역할  
**Main() 메서드는 모든 프로그램이 실행되는 시작점**  
  
### Main() 메서드의 구성 요건  
* 이름은 반드시 **`Main()`**이어야 한다.  
* 정적 메서드 `static`.  
* Main()메서드가 정의된 클래스의 이름은 제한이 없다.  
* Main 메서드의 반환값은 `void` 또는 `int`만 허용된다.  
* Main 메서드의 **매개변수**는 **`없거나`** **`string 배열`**만 허용된다.  





