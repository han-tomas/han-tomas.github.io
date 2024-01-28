---
title: Web Server와 WAS
date: 2024-01-28 00:00:00 +0900
categories: [⚙️Back-End, 🕸️Web]
tags: [Web,
WAS,
Web Server,
Server,
]     
---    
  
![image-2](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/a715d453-5c5d-430d-b3b9-e4914dc19b42)
  
  
## 공부 배경
웹 개발자, 그 중에서도 백엔드 개발자로서 공부를 하고 있지만, 근본적으로 'Web Server가 뭐냐?' 했을 때, 확실하게 아니, 모호하게도 답을 못하는 것 같다.  
하고 싶은 일은데 적어도 기본은 알아야 하지 않겠냐 스스로 생각하며, 이에 대한 지식을 찾던 도중, *Web Server vs WAS*에 대한 자료를 찾았고 이를 정리해보면 좋을 것 같았다.  
  
---
## Web Server
### Web
**인터넷을 기반으로 한**, 정보를 공유하고 검색할 수 있게 하는 서비스  
> * URL (주소)  
> * HTTP(통신 규칙)  
> * HTML (내용)  
  

### Server
클라이언트에게 **네트워크를 통해 정보나 서비스를 제공하는 컴퓨터 시스템**  
  

### Web Server  
**인터넷을 기반으로 클라이언트에게 웹 서비스를 제공하는 컴퓨터**  
  
![Web Server](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/0a1f4660-8371-4632-b169-f36778e2f848)  
  
---
## WAS  
### Web Application Service  
* Web에서 실행되는 응용프로그램  
* 웹 애플리케이션과 서버 환경을 만들어 동작시키는 기능을 제공하는 소프트웨어 프레임워크  
* 웹 애플리케이션을 실행시켜 필요한 기능을 수행하고 그 결과를 웹 서버에 전달  
* php, jsp, asp와 같은 언어를 사용해 **동적인 페이지**를 생성할 수 있는 서버  
* 프로그램 실행 환경과 데이터 베이스 접속 기능 제공  
* 비즈니스 로직 수행 기능  
* Web Server + Web Container  

**<span style="font-size:10%"> Container : jsp/Servlet을 실행시킬 수 있는 소프트 웨어** 
  

![WAS](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/301dde0f-1d16-428e-b410-bac4e36316f2)
  
![apche_TomCat](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/c3464e5d-cb53-4d93-b4c8-fb1d27c5aeb4)
  
---
## 그럼 WAS가 있는데 Web Server를 왜 두어야 하는가?  
### 1. 책임 분할을 통한 서버 부하 방지  
정적 컨텐츠는 Web Server, 동적 컨텐츠는 WAS가 담당하게 하므로써 서버의 부하를 방지 할 수 있다.  
  
---
### 2. 여러대의 WAS 로드 밸런싱 
WAS가 처리해야하는 요청을 여러 WAS가 나누어 처리할 수 있도록 Web Server에서 설정한다.  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/095c5a2b-c6c5-4e41-b365-5dce32ff9bea)  
  
---
### 3. 여러대의 WAS Health Check  
Web Server가 WAS에 주기적으로 Http 요청을 보내 서버의 상태를 확인한다.  
> ex)  
> * Interval : health check를 통해 서버 상태를 확인하는 요청을 날리는 주기  
> * Fails : 3회 연속 실패하면 서버가 비정상이라고 인지  
> * Passes : 서버가 다시 복구되어 요청이 2번 연속 성공하면 서버를 정상으로 인지  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/6fb4ac64-6aa9-458d-8834-db28a89d91a2)
  
---
### 4. 보안
**리버스 프록시(Reverse Proxy)**를 통해 실제 서버를 외부에 노출시키지 않을 수 있다.  
![image](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/12742658-75e9-47c0-8766-a13d85e591ec)  
 