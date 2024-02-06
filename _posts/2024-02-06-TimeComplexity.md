---
title: 시간 복잡도(Time Complexity)
date: 2024-02-02 00:00:00 +0900
categories: [💻Computer Science, 👨‍💻Algorithm]
tags: [네트워크,
Algorithm,
알고리즘,
시간 복잡도,
Time Comlexity,
Big-O,
빅오,
]     
---    
  
## 공부 배경  
본격적으로 알고리즘 정리하기에 앞서, 그동안 알고리즘을 공부하면서 늘 **시간 복잡도**에 대해 들었지만, 이게 정확히 뭔지 찾아보지는 않았다. 하지만 문제를 풀면서 **'시간초과'**라는 오류를 많이 접하게 되었고, 이를 해결하기 위해 시간 복잡도가 뭔지에 대한 정리가 필요했다.  
  
---  
## 시간 복잡도  
시간 복잡도는 알고리즘과 굉장히 밀접한 관계에 있다. **알고리즘**이란, **문제를 해결하기 위한 방법**이다.  
시간 복잡도의 의미는 *Wiki*에서 이렇게 나와있다.  
> **문제를 해결하는데 걸리는 시간과 입력의 함수 관계 - wiki**  
  
그렇다면, 문제를 해결하기 위한 알고리즘의 로직을 코드로 구현할 때, 시간 복잡도를 고려한다는 것은 무슨 의미일까? 그것은 **입력값의 변화의 따라 연산을 실행할 때, 연산 횟수에 비해 시간이 얼만큼 걸리는 가**를 고려한다는 것이다.  
**효율적인 알고리즘을 구현한다**는 것은 **입력값이 커짐에 따라 증가하는 시간의 비율을 최소화한 알고리즘을 구성했다**는 이야기이다. 그리고 이 시간 복잡도는 주로 **빅-오(Big-O) 표기법**을 사용해 나타낸다.  
  
---  
## Big-O 표기법  
빅-오(Big-O)는 **상한 접근법**으로 *'최악의 경우를 고려한다'*는 것이다. 바꾸어 말해, 프로그램이 실행되는 과정에서 소요되는 최악의 시간까지 고려한다는 의미이다.  
  
## Big-O 표기법의 종류  
1. **O(1)**  
2. **O(n)**  
3. **O(log n)**  
4. **O(n<sup>2</sup>)**  
5. **O(2<sup>n</sup>)**  
  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/6b313b94-8172-4acf-8f14-fc0917e67e3b)  

---  
### O(1)  
```java
public void print(int[] arr) {
    System.out.println(arr[0]);
}
```  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/a513a4c3-18b7-4235-a208-86ea4d0178b1)  
    
O(1)는 **일정한 복잡도(constant complexity)**라고 하며, 입력값이 증가하더라도 시간은 일정하다.  

---  
### O(n)  
```java  
public void print(int[] arr) {
    for (int i = 0; i < arr.length; i++) {
        System.out.println(arr[i]);
    }
}
```  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/813ce033-5237-4184-ba91-0f3b9bb5d976)  
  
O(n)은 **선형 복잡도(linear complexity)**라고 부르며, **입력값이 증가함에 따라 시간 또한 같은 비율로 증가**하는 것을 의미한다.  

---  
### O(log n)  
```java
public int binarySearch(int arr[], int l, int r, int x) { // 이분 검색
    if (r >= l) {
        int mid = l + (r - l) / 2;
        
        if (arr[mid] == x)
            return mid;
        
        if (arr[mid] > x)
            return binarySearch(arr, l, mid - 1, x);
        
        return binarySearch(arr, mid + 1, r, x);
    }
    
    return -1;
}
```   
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/a23f6b21-320c-4c0d-9c64-3b1b5c33abe9)  
  
O(log n)은 **로그 복잡도(logarithmic complexity)**라고 부르며, Big-O표기법중 **O(1) 다음으로 빠른 시간 복잡도**를 가지며, **가장 이상적**인 복잡도다. 입력값 n이 주어졌을 때, 특정한 요건에 따라 필요한 단계가 연산이 줄어 든다.  
  
---  
### O(n<sup>2</sup>)  
```java
public void print(int[][] arr) {
    for (int i = 0; i < arr.length; i++) {
        for(int j = 0; j < arr.length; j++>) {
            System.out.println(arr[i][j]);
        }
    }
}

```  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/de45ae18-3c81-470a-b2d9-bf970c11ea49)  
  
O(n<sup>2</sup>)은 **2차 복잡도(quadratic complexity)**라고 부르며, **입력값이 증가함에 따라 시간이 n의 제곱수의 비율로 증가하는 것**을 의미한다.  
  
---  
### O(2<sup>n</sup>)  
```java
public class Fibonacci {		
    public static void main(String[] args) {		
        int input = 8; 			
        for (int i = 1; i <= input; i++) {			
            System.out.println(fibo(i));		
        }	
    }	
            
    public int fibo(int n) {		
        if (n <= 1)	return n;		
        else return fibo(n-2) + fibo(n-1);	
    }
}
 
```  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/b02d1daa-57f5-4dec-aa33-37c57897c7e6)  

O(2<sup>n</sup>)은 **지수형 복잡도(Exponential Complexity)**라고 부르며, Big-O 표기법 중 **가장 느린 시간 복잡도**를 가진다.메모이제이션(Memoization)이 되어있지 않은 재귀 함수가 이 경우에 해당하며, 다차 형태와 모양은 비슷해도 엄청난 차이가 난다.  
  
---  
## 정리  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/4247ff4e-97fb-4bbf-8523-4cfc695c0937)  

|복잡도|1|10|100|
|:------:|:---:|:---:|:---:|
|O(1)|1|1|1|
|O(log n)|0|2|5|
|O(n)|1|10|100|
|O(log n)|0|20|461|
|O(n<sup>2</sup>)|1|100|10000|
|O(2<sup>n</sup>)|1|1024|1.2676506 x 10^30|
|O(n!)|1|3628800|9.332621544 x 10^157|    
