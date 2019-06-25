# Spring Framework Review

## 1. IoC (Inversion of Control)

일반적인 코드를 가지고 생각해보자.

```
class OwnerController {
```

​	`private OwnerRepository repository = new OwnerRepository();`

```
}
```

=> `OwnerRepository`는 `OwnerController`의 의존성이다.

(`OwnerRepository`라는 객체가 있어야 `OwnerController`가 실행될 수 있기 때문이다.)

### **여기서 제어 역전(IoC)이란?**

객체에 대한 제어권을 역전시켜(** 컨트롤러), 컨트롤러에게 제어권을 위임함으로써

1. 어플리케이션 간 결합도를 낮추어 코드의 변경에 유연하게 대처할 수 있으며

   (개발자가 제어 시 클래스 내부에서 진행함으로 강결합 상태가 됨)

2. 개발자의 효율적인 코딩(객체를 제어 할 필요가 없어지므로) 만들어냄

## 2. IoC Controller

IoC container는 컨테이너가 클래스 내부에 만든 객체들(bean)의 의존성을 관리.

### **Spring Framework의 장점?**

IoC를 가능케 하는 `ApplicationContext(Bean Factory)`를 자체적으로 지원.

- IoC Container는 자기 자신(ApplicationContext)를 Bean으로 등록
- 직접 컨트롤러의 역할을 확인하고 싶으면 @Autowired로 값 주입하면 확인 가능하나... 쓸일은 거의 없다.

<br>

## 3. Bean

**Bean**은 스프링 IoC가 관리하는 객체

Annotation은 자체 기능이 없고, 주석과도 같음. 

이 주석을 어디에 붙이느냐, 언제까지 유지할 것이냐는 속성을 가지고 있을 뿐, 기능은 없음. (Annotation을 마커로 사용하여 처리하는 프로세서들이 있는 것임)

@ComponentScan 어노테이션의 경우

=> 모든 클래스에 Component라는 어노테이션이 붙어있는 클래스를 찾아서 bean으로 등록해줌 (@Controller 역시 @Component 어노테이션을 가지고 있기 때문에 bean으로 등록이 가능하다)

#### **직접 Bean을 등록하는 방법은?**

#### @Bean 어노테이션으로 메소드를 정의한다. <u>단, Bean 메소드를 정의하기 위해서는 Configuration이라는 메소드 안에 정의해야한다.</u>

<br>

#### **Bean을 꺼내서 쓰는 방법**

@Autowired라는 어노테이션으로 ApplicationContext안의 Bean을 꺼내서 쓸 수 있다.



**중요한 점은 Bean만 의존성을 관리해준다는 것!** 

Bean이 아닌 객체의 경우 의존성을 관리해 주지 않음. 많이 사용하게 되는 클래스의 경우 클래스 전체가 Bean등록이 되야하는 이유가 바로 이것!

<br>

## 4. 의존성 주입(Dependency Injection)

어떠한 Bean에 생성자가 오직 1개만 있고 파라미터로 받는 객체가 Bean이 존재한다면 Annotation이 없더라도 주입이 된다. (Spring 4~5버전에서 추가된 기능)



ApplicationContext안에는 수 많은 lifeCycle Interface들이 있고,  이 인터페이스를 구현할 경우 수 많은 lifeCycle 단계에 껴서 작업할 수 있음.  

스프링데이터 JPA는 인터페이스를 구현한 인터페이스 타입의 객체를 만들어줌.

(** Bean을 만들어서 ApplicationContext에 등록해주는 Call Back)



@Autowired/ @Inject 위치

- 생성자 (1)
- 필드 (3)
- 클래스 Setter (Setter가 있다면, Setter를 통해서 의존성을 변경하겠는 의미, 따라서 의존성 주입 역시 Setter를 통해서 진행하는게 자연스럽다고 볼 수 있음) (2)
- 그렇다면 Setter가 없는 경우 굳이 Setter를 만들어서 붙여야 한다는 건 바람직하지 않음 (필요없이 Setter가 들어가 의존성이 바뀜)

- ### Reference

  - 백기선님의 스프링 프레임워크 입문강좌

    (https://www.inflearn.com/course/spring/dashboard)

  - 스프링 샘플 프로젝트 petclinic

    (https://github.com/spring-projects/spring-petclinic)

  - Tutorial Teacher

    (https://www.tutorialsteacher.com/ioc/inversion-of-control)
