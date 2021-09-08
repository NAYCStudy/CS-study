- https://blog.naver.com/jinwoo6612/222483423436   

## Spring   
 <img src="./images/Spring.png" width="50%" float="center">  
 
 ### 스프링 프레임워크   
 - Java 플랫폼을 위한 오픈소스 애플리케이션 프레임워크  
 - 웹 애플리케이션 개발에 필요한 기능을 종합적으로 제공하는 경량화 솔루션  
 - 경량 컨테이너로서 java 객체를 직접 관리   
 - 전자정부 표준 프레임워크   

 <br>
 
 #### 특징  
 1.  IoC : 제어의 역흐름  
 2.  DI / DL : 의존성 주입  
 3.  POJO : 단순 오브젝트   
 4.  AOP : 관점 지향 프로그래밍   
 5.  MVC 1, 2패턴   
 
 <br>
 
 __제어의 역전 [Inversion of Control]__   
 - 객체 생성, 호출에 대한 모든 권한을 Spring Framework에 위임하여 위임 받은 Spring 객체에 의해 제어되게 됩니다.  
 - 즉, 개발자가 객체를 제어하는 것이 아닌 Spring에게 해당 역할( __객체 생성 -> 의존성 주입 -> 초기화 -> 소멸__ )을 맡기는 것  
 - Ex. new 객체 생성, 의존성 주입, 초기화, 소멸 작업 등등  
 - 장점1 : 개발자는 객체 관리에 대한 일을 Spring에 위임하고 비즈니스 로직 개발에 더욱 집중할 수 있다.  
 - 장점2 : 객체 간 의존 관계를 쉽게 변경가능  
 - 장점3 : 결론적으로 코드 재사용성, 유지보수성 증가  


<br>

 __의존성 주입 [Dependency Injection]__   
 - 의존성 주입은 제어의 역전 특징 중 하나의 하위 개념이다.  
 - 스프링 컨테이너가 특정 객체(Bean)에 다른 객체(Bean)와의 의존성을 맺어주는 행위  
 - 즉, 하나의 객체가 다른 객체를 사용할 수 있도록 연결짓는 것  
 - 3가지 DI 방식 : 필드 주입 / Setter 주입 / 생성자 주입  
 <br> 
 
 - 필드주입 : 코드는 가장 간단하지만 외부에서 변경이 불가능하므로 지양되는 주입 방식  
 ```
 @Autowired
 private ExampleServcie exampleService;
 ```
 <br>
 
 - Setter 주입 : Field 변수를 변경할 수 있는 Setter를 통해 의존성을 주입하는 방식 (주입 객체가 수정될 가능성이 있는 경우 사용)  
 ```
 private ExampleService exampleService;

 @Autowired
 public void setExampleService(ExampleService exampleService){
     this.exampleService = exampleService;
 }
 ```
 <br>
 
 - 생성자 주입 : 생성자를 호출하는 시점에 1회 주입하는 것이 보장, 생성자 1개만 있을 경우 @Autowired 생략 가능   
 _장점_   
 &nbsp; 1. 생성자 주입을 통해 주입 객체의 불변성 보장   
 &nbsp; 2. 생성자 주입을 통해 객체 1회 주입 보장  
 &nbsp; 3. 의존 객체에 final 키워드 사용 가능, 컴파일 시점에 누락된 객체 확인 가능   
 &nbsp; 4. 순환 참조 에러 방지 __(추후 정리하기!)__   
 &nbsp; 5. 생성자 파라미터로 의존성 객체를 받기에 개발자로부터 무분별한 객체 주입 방지    
 ```
 @Service
 
 public class ExampleServiceImpl implements ExampleService {
     private ExampleDAO exampleDAO;
     private SampleService sampleService;

     @Autowired    // 생성자가 1개만 있을 경우 @Autowired를 생략해도 주입이 가능
     public ExampleServiceImpl(ExampleDAO exampleDAO, SampleService sampleService) {
         this.exampleDAO = exampleDAO;
         this.sampleService = sampleService;
     }
 }

 @Controller
 public class ExampleController {

  private final ExampleService exampleService = new ExampleService(new ExampleDAO(), new SampleService());
 }
 ```

 *생성자 주입을 쓰자!!
 
 
 <br>
  
 __POJO : Getter/Setter를 포함한 단순 오브젝트__    
 - 특정 규약에 종속되지 않는 단순한 오브젝트   
 - 객체 지향의 개념을 준수합니다.  
 - 특정 환경에 종속되지 않습니다.  
 - > 객체 지향 프로그래밍에 적절합니다.   
 ```
 public home {
    private String name;
    private float[] location;
    private int price;

    public void setName(String name){
        this.name = name;
    }
    public void setLocation(float[] location){
        this.location = location;
    }
    public void setPrice(int price){
        this.price = price;
    }

    public String getName(){
        return this.name;
    }
    public float[] getLocation(){
        return this.location;
    }
    public int getPrice(){
        return this.name;
    }
    
 ```
 
 <br>
 
 __AOP : 관점 지향 프로그래밍__   
 - 관심사가 같은 데이터를 한 곳에 모아 관리하고 낮은 결합도 높은 응집도를 갖도록 독립접인 모듈로 캡슐화하는 것을 의미  
 - 개발 과정 중복되는 코드가 발생하게 되고 이를 보완하기 위해 AOP가 등장했습니다.   
 - 핵심기능과 공통기능을 분리 -> 공통 기능에 대해서 재사용 될 수 있도록 분리해두고 핵심 로직에 영향을 끼치지 않도록 기능을 끼워넣는 형태로 사용    
 - 재사용성 극대화 -> 프로그래밍/개발 속도 증대  

 __Spring Framework 구조__   
 <img src="./images/springstructure.png" width="50%">   
 
 - Spring Core : Spring Framework 핵심 기능 제공, 주요 컴포넌트 BeanFactory   
 - Spring Context : 애플리케이션 생명주기 이벤트와 같은 다수 엔터프라이즈 서비스 제공    
 - Spring AOP : Aspect 지향 프로그래밍 기능을 Spring Framework와 통합하여 모든 객체에서 AOP 사용 가능    
 - Spring DAO : 서로 다른 DB 벤더들의 예외 핸들링, JDBC DB 접근, 트랜젝션 전반 관리   
 - Spring ORM : 다양한 ORM 프레임워크(JPA, Mybatis)에 플러그인 되어 Object Relational 툴 제공   
 - Spring Web Module : 웹 기반 애플리케이션 Context 제공, 다중 요청 핸들링   
 - Spring MVC Framework : 완전한 기능을 갖춘 MVC 패턴    


 <br>
 <br>
 
 ### MVC 패턴  
 - MVC : 웹 애플리케이션 개발에 있어 가장 많이 정형적으로 쓰이는 디자인 패턴   
 - Model, View, Controller    
 - Model : 데이터 처리를 담당, Service & DAO 영역으로 나누어집니다.  
 - View : 사용자에게 보여지는 부분, 사용자 인터페이스 담당, JSP & Vue & React    
 - Controller : Model, View 연결 담당, 전반적 서비스 제어 담당, Controller    

 <br> 
 
 - MVC1 패턴    
 ![image](https://user-images.githubusercontent.com/58026613/132129745-f9dd37e2-4ab9-4e7d-b69e-77f163dcc577.png) 

  
 - MVC2 패턴   
 ![image](https://user-images.githubusercontent.com/58026613/132129746-795e4679-0010-4e7e-8bd5-a50f665ca828.png) 

 [View - Controller - Model]   
  
 ### Spring VS Spring Boot  
 - Spring Framework와 Spring Boot Framework 차이점과 특징   
 가장 큰 차이점  
 &nbsp; - 스프링의 경우 AOP, DI, DL, POJO 특징을 가지고 웹 애플리케이션 개발을 위한 다양한 기능을 갖추고 있지만 기본 프로젝트 세팅에 있어 개발자에게 많은 시간 투자를 필요로 합니다.   
 &nbsp; - 스프링 부트의 경우 복잡한 프로젝트 설정을 자동화하고 @AutoConfiguration을 통해 애플리케이션 개발에 필요한 모든 내부 Dependency를 관리합니다.   
 
 <br>
 
 __Spring Boot__  
 - Spring MVC 사용시 Component Scan, Dispatcher Servlet, View Resolver 등 설정을 간단하게 설정할 수 있도록 합니다.   
 - Spring 프레임워크 설정의 많은 부분을 Boot가 자동화하여줍니다.   
 - Spirng과는 달리 Spring Boot 내장 WAS(Default: Tomcat)를 통해 서버를 실행할 수 있습니다.  
 - Spring-Boot-Starter는 의존성 및 설정, 버전 호환을 자동화하여주는 모듈입니다.   
 - > spring-boot-starter-jpa : spring-aop, spring-jdbc 의존성을 자동으로 설정  
 
 <br><br>
 
 ### Bean   
  #### Bean?  
  - Spring IoC 컨테이너가 관리하는 자바 객체를 Bean 이라고 합니다.   
  - Spring IoC는 객체(Bean)에 대한 제어권을 가지고 있습니다.   
  - new 를 통해 생성한 객체는 Bean이 아닙니다.  
  - ApplicationContext.getBean()으로 얻어질 수 있는 객체를 Bean 이라고 합니다.  


  즉, Spring에서 Bean는 Spring 컨테이너가 알고 있는 객체를 의미합니다.   
  
  <br>
  
  
  
