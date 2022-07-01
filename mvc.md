### The request processing workflow of the Spring MVC 
![Spring MVC](https://docs.spring.io/spring-framework/docs/3.0.0.M4/spring-framework-reference/html/images/mvc.png)

### DispatcherServlet
  The DispatcherServlet implements Front Controller design pattern and is responsible for directing incoming HttpRequests 
  to all of an application's other controllers and handlers.
  
  The core responsibility of a DispatcherServlet is to dispatch incoming HttpRequests to the correct handlers specified with the 
  @Controller or @RestController annotations.
