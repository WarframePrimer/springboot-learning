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
