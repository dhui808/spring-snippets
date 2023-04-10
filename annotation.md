### @SpringBootApplication
    @SpringBootApplication annotation can be used to enable three features:

    @EnableAutoConfiguration: enable Spring Boot’s auto-configuration mechanism
    @ComponentScan: enable @Component scan on the package where the application is located (see the best practices)
    @Configuration: allow to register extra beans in the context or import additional configuration classes

### @ComponentScan
    @ComponentScan enables Spring to scan for things like configurations, controllers, services, and other components we define.
    In particular, the @ComponentScan annotation is used with @Configuration annotation to specify the package for Spring to scan 
    for components.
  
    @ComponentScan annotation can also scan, detect, and register beans for classes annotated with @Component, @Controller, 
    @Service, and @Repository.

### @EnableAutoConfiguration
    The @EnableAutoConfiguration annotation enables Spring Boot to auto-configure the application context. Therefore, it 
    automatically creates 

    The package of the class declaring the @EnableAutoConfiguration annotation is considered as the default. Therefore, we 
    should always apply the @EnableAutoConfiguration annotation in the root package so that every sub-packages and class can be 
    examined and registers beans based on both the included jar files in the classpath and the beans defined by us.

### @RefreshScope
    When there is a configuration change, a Spring @Bean that is marked as @RefreshScope gets special treatment.
    Refresh scope beans are lazy proxies that initialize when they are used
  
### @Configuration
    Indicates that a class declares one or more @Bean methods and may be processed by the Spring container to 
    generate bean definitions.
  
### @EnableConfigurationProperties registers as a Spring bean a POJO annotated with @ConfigurationProperties
    @ConfigurationProperties("customer")
    public class CustomerProperties {
      ...
    }

    @Configuration
    @EnableConfigurationProperties(CustomerProperties.class)
    public class MyConfiguration {

      @Autowired
      CustomerProperties customer;

      public CustomerProperties getCustomer() {
        return customer;
      }
    }

    Note:
    Add @EnableConfigurationProperties to the class annotated with @ConfigurationProperties may work (at least for
    non-springboot application). But in Springboot application, the above example is the right way.
    
