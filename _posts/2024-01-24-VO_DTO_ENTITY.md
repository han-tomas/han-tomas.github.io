---
title: VO vs DTO vs ENTITY
date: 2024-01-24 00:00:00 +0900
categories: [⚙️Back-End, 🍃Spring]
tags: [Spring,
문법,
vo,
dto,
entity,
]     # 태그 이름은 항상 소문자여야 한다.
---
![vodtoentity](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/393d3ba6-1af5-4a43-875e-0652639dc559)  

---
## 공부 배경

국비지원 학원을 다니면서 프로젝트를 진행했을 때, DB 테이블의 데이터를 사용할 때든, 그 데이터를 가공할 때든 객체를 VO로 선언하여 사용하였다.  
하지만, 수료 이후 개인적으로 공부를 진행하다 보니 데이터를 VO, DTO, ENTITY 이렇게 세가지 객체로 분류하여 관리하는 것을 알게 되었다.  
이에 대한 개념정리가 필요하였다.  

---

## VO? DTO? ENTITY?

---

### VO란 무엇인가?

`VO`란 Value Object 말 그대로 **값 그 자체를 표현하는 불변 객체**이다.  

* VO는 변경 불가능한(immutable) 객체
* VO는 특정 비즈니스 값을 담는 객체
  * getter 메소드는 가질 수 있지만, setter메소드는 가지지 않는다.
  * Read Only 특징을 가진다.
* VO는 객체들의 주소 값이 달라도 데이터 값이 같으면 동일한 것으로 여긴다.
  * 값 비교를 위해 equals()와 hashCode() 메서드를 오버라이딩 해야 함(객체의 불변성을 보장함.)  

```java
@Getter 
@Setter
class ArticleVO {
    private Long id;
    private String title;
    private String contents;

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Article article = (Article) o;
        return Objects.equals(id, article.id);
    }

    @Override
    public int hashCode() {
        return Objects.hash(id);
    }
}
```

---

### DTO란 무엇인가?  

`DTO` 는 **계층(Layer)간 데이터 교환이 이루어질 수 있도록 하는 객체**이다.

* DTO는 getter, setter 메서드를 포함하며, 이 외의 비지니스 로직은 포함하지 않는다.

* Controller 같은 클라이언트와 직접 마주하는 계층에서 사용하여, 데이터를 요청/응답하며, 주로 View와 Controller 사이에서 데이터를 주고받을 때 사용한다.

* 주로 비동기 처리를 할 때 사용한다.

```java
@Getter
@AllArgsConstructor
public class MemberDto {
private String name;
private int age;
}
```

---

### ENTITY란 무엇인가?  

`ENTITY`란 실제 **DB테이블과 매핑되는 핵심 클래스**로, DB테이블에 존재하는 컬럼들을 필드로 가지는 객체이다.

* ENTITY 클래스는 실제 DataBase의 테이블과 1:1로 매핑되는 클래스이다.

* DB의 테이블내에 존재하는 컬럼만을 속성(필드)으로 가져야 한다.

* 외부에서 ENTITY클래스의 데이터 필드에 접근하지 못하도록 제한해야 한다.

* ENTITY는 id로 구분되며, 비지니스 로직을 포함할 수 있다.

* ENTITY는 데이터베이스 영속성(persistent)의 목적으로 사용되는 객체이며, 요청(Request)이나 응답(Response)값을 전달하는 클래소로 사용하는 것은 좋지 않다.  

```java
@Entity
@Builder
@Getter
@NoArgsConstructor
@AllArgsConstructor
public class User {
@Id
@GeneratedValue(strategy = GenerationType.IDENTITY)
private Long id;

@Column(nullable = false)
private String name;

@Column(nullable = false)
private String email;

private String phoneNumber;
}
```

  
---
## 정리
---  

| |VO|DTO|ENTITY|
|:------:|:---:|:---:|:---:|
|생성 목적|객체안의 값을 통해서<br> 비교해야하는 중요 로직에서<br> 사용할 데이터를 담기위해<br> 사용|단순 데이터 전송,수신 용도|JPA 사용시 DB 테이블과<br> 직접적으로 매핑하여 DB에<br> 접근할 때 사용|
|getter 사용|O|O|O|
|setter 사용|X|O|X(setter 사용을 지양)|
|equals() & hashCode 구현|O|X|O|
|데이터 민감도|80|0|100|



