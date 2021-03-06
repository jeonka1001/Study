# 면접준비 - Spring
> 나만의 언어로 하는 면접준비

## 질문 목차

---

## Spring 을 사용하는 이유
- 엔터프라이즈 시스템 개발은 복잡하다. 스프링은 이러한 **복잡함 해결** 을 도와주며 개발자가 최대한 **개발 하는 것 에만 집중** 할 수 있도록 해주기 때문에 spring 을 사용한다.

##### 기업 시스템 개발이 복잡한 이유 ?
- 동시에 많은 요청과 예외를 처리해야 합니다.  
- 기업의 핵심 정보를 다루기 때문에 보안과 안정성, 확장 측면을 신경써야 합니다. 

##### Spring 복잡함을 어떻게 해결하나? ( 장점 )
> 개발자가 비즈니스 로직에만 신경쓸 수 있도록 도와줌  

- 기존 기술적인 제약 조건과 비즈니스 로직을 같이 갖고 있는 코드에서 기술적인 제약 조건을 스프링 내부적으로 처리 하며 코드를 간결하게 해준다.
    - 기술적인 제약 조건 : DB 연결, 쿼리 실행, 트랜잭션 처리
    - transaction 의 경우 ```@transactional``` 로 해결할 수 있다.
- 이 경우 기술 제약에 대해 변경 사항이 있을 경우 클래스 내부는 수정하지 않아도 된다.
    - DB 아이디 변경, 서버 주소 변경 등 ( XML 을 통해 함 )

---

## POJO 프로그래밍 ?
> POJO : plain old java object  
- 특정 기능을 사용하기 위해 특정 환경에 종속되지 않는 것
    - 서블릿 객체와 같이 특정 기능을 수행하기 위해 클래스나 인터페이스를 구현하지 않는 것

---

## IOC/DI 란? 
> IOC : 제어의 역전
> DI : 의존성 주입  

### IOC ( Inversion of Control)
- A 라는 클래스의 비즈니스 로직에서 B 라는 클래스를 사용할 때 직접 의존성을 주입하지 않는 것을 말한다. 이때 **의존성을 주입** 하는 것을 **DI** 라 하며, 이것이 간접적으로 헹해지기 때문에 느슨한 결합 이라 한다.

- B를 A 가 관리하지 않고 외부에서 건네받아 사용하기 떼문에 B 가 변경될 경우 A에 영향이 없기 때문에 코드 관리에 용이하다

##### DI의 종류
> setter, constructor, method injection 이 있다.  

##### Bean
- spring 에서 객체 의존성 주입을 위해 의존성을 관리하는 데 이때 관리하는 의존성 즉 객체를 bean 이라고 한다. 
- spring 을 통해 의존성을 주입하기 위해서는 bean 에 등록해 spring이 관리할 수 있도록 알려야 한다.

**_등록 방식_**  
1. 직접 클래스를 구성하고 어노테이션 태그  
2. Configuration 어노테이션이 붙은 클래스에 직접 등록

---

## Spring MVC 작동 방식
1. DispatcherServlet 이 클라이언트로부터 요청을 받는다  
2. 요청을 다룰 Handler 선택을 위해 HandlerMapping 에게 요청한다.
3. HandlerMapping 은 전/후처리 할 것을 interceptor 로 만든 후 Handler 를 실행한다.
4. Handler 는 service 객체를 실행 후 결과와 View 이름을 DispatcherServlet에 전송한다
5. DispatcherServlet 은 View 이름을 ViewResolver 에게 전달하여 View 객체를 얻은 후 View 를 보여준다

---

## AOP ( Aspect oriented Programming)
- 관점 지향 프로그래밍
- 메서드 중 공통으로 사용하는 기능적인 역할을 비즈니스 로직에서 분리하여 코드의 중복 없이 재활용하는 것 
    - 분리 대상 : 데이터베이스 연결, 로깅, 파일 입출력 등 ( 비즈니스 로직이 아닌 기능적인 역할 )

<!-- https://velog.io/@max9106/Spring-%ED%94%84%EB%A1%9D%EC%8B%9C-AOP-xwk5zy57ee -->

---

## PSA ( portable service abstraction )
- 개발자가 직접 관여하지 않는 기능을 추상화하여 제공하는 것 으로 개발자가 비즈니스 로직 외적으로 신경쓰지 않도록 도움을 주는 것 입니다.
- spring 에서는 AOP 개념에서 비즈니스 로직과 분리한 기능적인 역할을 추상화하여 제공하는것이머, 자바에서 제공하는 API 인 JPA 또한 이것에 의해 사용되는 기술?  입니다.

---

## MVC Model View Controller
- Model : 데이터를 담는 객체 , View 사용자에게 직접 출력되는 화면, 

---

## JPA
기존 MyBatis 는 SQL문을 미리 등록해 둔 후 Mapper Class 를 통해 DAO객체에서 SQL문을 실행했다.  
따라서 모든 SQL 에 해당하는 메서드를 만들고 

#### MyBatis 
- 자바에서 관계지향형 데이터 베이스 프로그래밍을 보다 쉽게 도와주는 라이브러리
- 기존 JDBC와 다르게 쿼리문을 비즈니스 로직과 분리해 따로 관리하게 해줌.
- Mapper 파일에 SQL 문을 작성하고 자바에 Mapper 클래스를 만들어 클래스의 메서드 하나와 쿼리문 하나를 매핑시켜 사용함
- DAO 코드가 훨씬 간결해 진다., 유지보수가 쉬워진다.

---

## Annotation 정리

#### @ComponentScan 
- @Controller @Service @Repository @Configuration @Component 어노테이션이 붙은 Bean 을 찾아서 컨텍스트에 등록을 해준다.
###### 모든 Component 를 @Component로 다 쓰지 않는 이유는 ? 
예를 들어 @Repository 는 DAO 에 붙이는 어노테이션 인데 DAO 메소드에서 런타임 시 발생할 수 있는 예외

#### @Transactional
- 데이터베이스 트랜잭션을 지원하는 어노테이션
- 해당 어노테이션이 있는 함수는 실행 전에 함수 앞에 Begin Transaction 구문과 함수 뒤에 Commit Transaction 혹은 Rollback Transaction 이 삽입된다.
    - Begin Transaction 은 AutoCommit 을 비활성화 해주며, Commit 혹은 Rollback이 될 경우 다시 활성화 된다.
---

## Filter vs Interceptor
- fileter 는 어플리케이션에 등록되어 스프링과 무관한 자원에 대해 실행
- interceptor 는 스프링 context 에 등록되어 controller 동작 전/후 에 실행된다.

