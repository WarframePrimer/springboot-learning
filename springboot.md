Spring Boot是Spring官方的顶级项目之一，其他的还有Spring Cloud、Spring Framework、Spring Data等等。  
Spring Boot的官方原文中文翻译：  
Spring Boot可以轻松创建单独的，基于生产级的Spring应用程序，你需要做的只是“ run”。我们提供了Spring Platform对Spring框架和第三方库进行处理，  
尽可能的降低使用的复杂度。大多数情况下Spring Boot应用只需要非常少的配置。  
要开始一个Spring Boot项目    
1.配置项目的pom.xml

```
  <!--SpringBoot启动父依赖-->
  <parent>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-parent</artifactId>
      <version>1.5.8.RELEASE</version>
  </parent>
  
  <!--SpringBoot Web依赖-->
      <dependency>
          <groupId>org.springframework.boot</groupId>
          <artifactId>spring-boot-starter-web</artifactId>
      </dependency>
```
2.创建Application.java
```
@RestController
@EnableAutoConfiguration
public class Application{
  @RequestMapping("/")
  String index(){
    return "hello Spring Boot!";
  }
  
  public static void main(String[] args) throws Exception{
    SpringApplication.run(Application.class,args);
  } 
}
```
3.Run ,执行Application.main()或者mvn:spring-boot:run  
到此为止，就快速的构建、部署、启动了一个web应用。  

下面是Spring Boot官方关于构建web项目的项目结构建议：  
```
src
  com
  +- warframe
     +- myproject
        +- Application.java //建议位于项目的根目录，这可以简化@ComponentAScan
        |
        +- domain(pojo|bean)
        |  +- Customer.java（这里只是举个例子）
        |  +- Repository.java
        |
        +- service
        |  +-CustomerService.java
        |
        +- web
           +- CustomerController.java
   resources
   +- config //配置文件
      application.properties
   +- static //静态文件
      +- css
      +- js
      +- images
      index.html
   +- templates //模板文件
 pom.xml
```

SpringBoot提供了对应用进行自动化配置。相比之前XML配置方式，很多显式方式声明是不需要的。、  
SpringBoot不单单从application.properties中获取配置：  
-- 1.命令行参数  
-- 2.java:comp/env 里的JNDI属性 
-- 3.JVM系统属性  
-- 4.操作系统环境变量  
-- 5.RandomValuePropertySource 属性类生成的random.*属性  
-- 6.应用以外的application.properties文件  
-- 7.打包在应用内的application.properties文件  
-- 8.在应用@Configuration配置类中，用@PropertySource注解声明的属性文件  
-- 9.SpringApplication.setDefaultProperties声明的默认属性  

