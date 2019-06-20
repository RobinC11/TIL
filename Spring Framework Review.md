Spring Framework Review
================================

## 1. IoC (Inversion of Control) 

일반적인 코드를 가지고 생각해보자.

`class OwnerController {` 

​	`private OwnerRepository repository = new OwnerRepository();`

`}`

=> `OwnerRepository`는 `OwnerController`의 의존성이다.

(`OwnerRepository`라는 객체가 있어야 `OwnerController`가 실행될 수 있기 때문이다.)



**여기서 제어 역전(IoC)이란?** <u>

객체에 대한 제어권을 역전시켜(** 컨트롤러), 컨트롤러에게 제어권을 위임함으로써 

1. 어플리케이션 간 결합도를 낮추어 코드의 변경에 유연하게 대처할 수 있으며 

   (개발자가 제어 시 클래스 내부에서 진행함으로 강결합 상태가 됨)

2. 개발자의 효율적인 코딩(객체를 제어 할 필요가 없어지므로) 만들어냄



**그렇다면 제어 역전을 어떻게 진행할까?**



## 2. IoC Controller

IoC container는 컨테이너가 클래스 내부에 만든 객체들(bean)의 의존성을 관리.

**Spring Framework의 장점?** 

IoC를 가능케 하는 `ApplicationContext(Bean Factory)`를 자체적으로 지원. 



IoC Container는 자기 자신(ApplicationContext)를 Bean으로 등록시켜 놓았기 때문에 직접 컨트롤러의 역할을 확인하고 싶으면 @Autowired로 값 주입하면 확인 가능하나... 쓸일은 거의 없다.

 <!--(예전에는 ServletApplication 생성 시 web.xml에 ApplicationType을 ServletListner에 argument로 전달해야 했었으나 버전이 올라오면서 Servlet이 java를 지원하고, xml를 사용하지 않게 되고 Spring Boot 등장으로 해당 설정들이 기본설정으로 감춰짐.)-->





- ### Reference

  - 백기선님의 스프링 프레임워크 입문강좌

    (<https://www.inflearn.com/course/spring/dashboard>)

  - 스프링 샘플 프로젝트 petclinic

    (<https://github.com/spring-projects/spring-petclinic>)

  - Tutorial Teacher

  ​       (<https://www.tutorialsteacher.com/ioc/inversion-of-control>)

  