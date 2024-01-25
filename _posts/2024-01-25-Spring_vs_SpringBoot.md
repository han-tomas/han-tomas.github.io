---
title: Spring vs SpringBoot
date: 2023-01-25 00:00:00 +0900
categories: [🍃Spring, 이론 및 개념]
tags: [Spring,
SpringBoot,
]     
---  
![스프링-스프링-부트-프레임워크](https://github.com/han-tomas/han-tomas.github.io/assets/124488773/98f9c52f-2c7d-47bb-927d-b92325b1ad08) 

---  
## 공부 배경  
나는 그동안 Spring으로 프로젝트들을 진행해왔다. 그러나 개인적으로 공부를 하기위해 여러 인터넷 게시물들과 영상들을 찾아봤을때 예전의 자료들은 Spring, 최근의 것들은 대부분 Spring Boot를 이용하여 프로젝트를 진행하고 있었다.  
또 취업을 위해 기업들의 자격요건을 보면, 어떤곳은 Spring, 어떤곳은 Spring Boot 기반 웹 서비스 개발 가능자를 요구하는 것을 볼 수 있었다.  
Spring과 Spring Boot 이 둘의 차이점을 정리해 두는 것이 좋겠다고 생각했다.  

---  
## Spring Framework
>Whatever happened next, the framework needed a name. In the book it was referred to as <br>the “Interface21 framework” (at that point it used com.interface21 package names), but that<br>was not a name to inspire a community. Fortunately Yann stepped up with a suggestion:<br>“Spring”. His reasoning was association with nature (having noticed that I'd trekked to <br>Everest Base Camp in 2000); and **the fact that Spring represented a fresh start after the<br>“winter” of traditional J2EE.** We recognized the simplicity and elegance of this name, and quickly agreed on it.  
  
>**"개발자에게 겨울은 끝나고 봄이 왔다."**  
  
*Spring Framework의 주요 기능과 특징은 이 후 게시물에서 따로 다룰 생각이다.*  

---  
## Spring 과 SpringBoot의 차이  

|Spring|SpringBoot|
|:---:|:---:|
|dependency(의존성)를 버전까지 정확하게 작성 <br> &rarr; 작성 내용이 길다 |버전관리를 자동으로 해준다 <br> &rarr; 작성 내용이 짧아짐|  
|Configuration(환경설정)도 길다|application.properties/.yml로 짧게 적용 <br> (application.yml을 더 선호)|  
||embeded server(내장 서버)로 <br> 서버 구동 시간이 절반 가까이 단축됨. <br> 내장 서블릿 컨테이너 덕분에 <br> jar파일로 간단히 배포|  

---
### Dependency  
**Spring**의 의존성 작성법  
```
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-web</artifactId>
    <version>5.3.5</version>
</dependency>
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-webmvc</artifactId>
    <version>5.3.5</version>
</dependency>
```
  
**SpringBoot**의 의존성 작성법  
```
implementation 'org.springframework.boot:spring-boot-starter-web'
```  
---  

### Configuration  
`ex) Thymeleaf`  
**Spring**의 Configuration
```java
@Configuration
@EnableWebMvc
public class MvcWebConfig implements WebMvcConfigurer {

    @Autowired
    private ApplicationContext applicationContext;

    @Bean
    public SpringResourceTemplateResolver templateResolver() {
        SpringResourceTemplateResolver templateResolver = 
          new SpringResourceTemplateResolver();
        templateResolver.setApplicationContext(applicationContext);
        templateResolver.setPrefix("/WEB-INF/views/");
        templateResolver.setSuffix(".html");
        return templateResolver;
    }

    @Bean
    public SpringTemplateEngine templateEngine() {
        SpringTemplateEngine templateEngine = new SpringTemplateEngine();
        templateEngine.setTemplateResolver(templateResolver());
        templateEngine.setEnableSpringELCompiler(true);
        return templateEngine;
    }

    @Override
    public void configureViewResolvers(ViewResolverRegistry registry) {
        ThymeleafViewResolver resolver = new ThymeleafViewResolver();
        resolver.setTemplateEngine(templateEngine());
        registry.viewResolver(resolver);
    }
}
```  
**SpringBoot**의 Configuration  
```
implementation 'org.springframework.boot:spring-boot-starter-thymeleaf
```
---  
## 정리  

Spring보다 SpringBoot를 사용하는 이유는 다음과 같다.
1. 간단한 설정  
2. 편리한 의존성 관리 및 자동 권장 버전 관리  
3. 내장 서버로 인한 간단한 배포 서버 구축  
4. 스프링 Security, Data JPA 등의 다른 스프링 프레임 워크 요소를 쉽게 사용
