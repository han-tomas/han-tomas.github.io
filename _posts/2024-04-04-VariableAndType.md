---
title: C# 변수와 기본 타입
date: 2024-04-04 00:00:00 +0900
categories: [⚙️Back-End, 🕹️C#]
tags: [C#,
.NET,
OOP,
변수,
기본타입,
Variable,
Type,
]     
---  
## 목차  
  
> 1. 기본형 
> 2. 변수 정의    
> 3. 클래스에서 변수 선언  
> 4. 메서드에서 변수 선언  
  
---  
## 기본형 (Type)  
* **기본 자료형(Built-in Types)** : 개발자가 별도로 코드를 만들지 않아도 C# 언어에서 자체적으로 제공하는 데이터 형식을 의미  
    * 정수형, 실수형, 문자, 불린형  

### 정수형 기본 타입  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/1a4543d9-729e-4a86-a4d7-5dbc8f475641)  
  
### 기타 기본 타입  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/85be0730-844a-458a-8ea1-b7eac420846b)  
  
---  
## 변수 정의  
* 값(Literal)을 보관하는 장소  
* 변수는 반드시 (기본)타입과 함께 선언한 후 사용  
    * `int a;`  
    * `private string str;`
    * `public List<Student> students;`  
* 필요한 위치에서 선언 가능    
  
```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Example_3
{
    class Program
    {
        static void Main(string[] args)
        {
            int a;
            a = 1;
            char c = 'A';
            string str = "abcd";
            bool con = true;
            Console.WriteLine("a = " + a);
            Console.WriteLine("c = " + c);
            Console.WriteLine("str = " + str);
            Console.WriteLine("con = " + con);
        }
    }
}

```  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/f739f416-bd50-4695-be20-077254cad69a)  
  
### 변수 구분  
* **접근 제한에 따른 변수 구분**  
    * **멤버 변수** (전역 변수, Global 변수) - 클래스에서 선언
    * **지역 변수** - 메서드에서 선언 (파라미터 포함)  
* **타입에 따른 변수 구분**  
    * 값 형식 변수(Value Type)  
        * 기본 타입 중에 string만 제외하고 모두가 값 형식  
        * 구조체 (struct)  
    * 참조 형식 변수(Reference Type)  
        * 기본 타입 중에 string과 기타 모든 타입(클래스)  
  
```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Example_3
{
    class Program
    {
        static int a = 3;
        static void Main(string[] args)
        {
            int a = 1;
            Console.WriteLine("a = " + a);
            Function1();
        }

        static private void Function1()
        {
            Console.WriteLine("a = " + a);
        }
    }
}

```  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/5bfb0df4-a809-4dbd-aec3-b0a43c8a60c4)  
  
* `static int a = 3;` : <span style = "color : red">**클래스 블럭**</span>내에서 선언된 변수 👉 <span style = "color : red">**멤버 변수**</span>  
* `int a = 1;` : <span style = "color : blue">**메서드 블럭**</span>내에서 선언된 변수 👉 <span style = "color : blue">**지역 변수**</span>  
* 멤버 변수와 지역 변수의 이름이 동일할 경우에는 지역 변수를 우선으로 한다.  
  
---  
## 클래스에서 변수 선언(멤버 변수)  
* **인스턴스 변수(instance variable)**  
    * High Frequency Heap이라 불리는 힙의 특별한 부분에 저장  
    * 인스턴스변수.변수명으로 접근 가능  
* **스태틱 변수 (static variable)**  
    * High Frequency Heap이라 불리는 힙의 특별한 부분에 저장  
    * 클래스명.변수명으로 접근만 허용  
* **라이프 사이클**  
    * 프로그램 시작 시 할당, 프로그램 종료 시 해제  

---  
##  메서드에서 변수 선언(지역 변수)  
* **스택 메모리 사용**  
    * 함수 내부에서만 사용 가능  
    * 외부에서는 접근 불가능  
* **라이프 사이클**  
    * 함수 호출 시 할당, 함수 리턴 시 해제  
  
## 멤버 변수와 지역 변수  

### 멤버 변수 이용    
```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Example_3
{
    class Program
    {
        static int a = 0;
        static void Main(string[] args)
        {
            a = 1;
            Console.WriteLine("a = " + a);
            Function1();
            Console.WriteLine("a = " + a);
        }

        static private void Function1()
        {
            a = 2;
        }
    }
}

```   
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/b9dbf944-1bbf-4519-aecc-b4b96da96efc)  
  
### 지역 변수 이용  
```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Example_3
{
    class Program
    {
        static void Main(string[] args)
        {
            int a = 1;
            Console.WriteLine("a = " + a);
            Console.WriteLine("a = "+ Function1(a));
            Console.WriteLine("a = " + a);
        }

        static private int Function1(int a)
        {
            a = 2;
            return a;
        }
    }
}

```  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/a102996f-ec80-446e-b6f6-1e57e1a69c97)
  
* `Function(a);`에서는 지역 변수 `a`를 파라미터 값을 보낸 것이고, 이 메서드에 의해서 파라미터로써의 `a`값이 바뀌어 리턴되는 것일 뿐, `Main`메서드 내의 지역변수 값이 바뀌지 않는다.  

