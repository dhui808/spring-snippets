### @SpringBootApplication
  @SpringBootApplication annotation can be used to enable three features:

    @EnableAutoConfiguration: enable Spring Boot’s auto-configuration mechanism
    @ComponentScan: enable @Component scan on the package where the application is located (see the best practices)
    @Configuration: allow to register extra beans in the context or import additional configuration classes
    
### @RefreshScope
  When there is a configuration change, a Spring @Bean that is marked as @RefreshScope gets special treatment.
  Refresh scope beans are lazy proxies that initialize when they are used
  
### @Configuration
  Indicates that a class declares one or more @Bean methods and may be processed by the Spring container to 
  generate bean definitions.
  
