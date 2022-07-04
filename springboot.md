### differences-between-jar-and-war-in-spring-boot
  Spring Boot can be told to produce a 'fat JAR' which includes all of your module/service's dependencies and can be 
  run with java -jar <your jar>.
  
    <packaging>jar</packaging>
  
  The main Spring boot application:
  
    @SpringBootApplication
    public class ControlleradviceApplication {

      public static void main(String[] args) {
        SpringApplication.run(ControlleradviceApplication.class, args);
      }

    }
  
  Spring Boot can also be told to produce a WAR file, in which case you'll likely choose to deploy it to a web container
  such as Tomcat or Jetty.
  Add these lines to your pom.xml file:
  
    <packaging>war</packaging>
  
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-tomcat</artifactId>
        <scope>provided</scope>
    </dependency>
  
  Inherit main spring-boot application class from SpringBootServletInitializer and override SpringApplicationBuilder 
  configure(SpringApplicationBuilder) method.
  
    @SpringBootApplication
    public class DemoApplication extends SpringBootServletInitializer {

        public static void main(String[] args) {
            SpringApplication.run(DemoApplication.class, args);
        }

        @Override
        protected SpringApplicationBuilder configure(SpringApplicationBuilder builder) {
            return builder.sources(DemoApplication.class);
        }
    }
  
### How will you deploy your spring boot application?
  
    Deploying in Java Archive (JAR) as a standalone application,
    Deploying as Web Application Archive (WAR) into a servlet container,
    Deploying in Docker Container
  
### Spring Boot Annotation 
  @SprinbBootApplication:
  This single annotation combines three annotations:
    @Configuration
    @EnableAutoConfiguration
    @ComponentScan.

  @ConfigurationProperties
  Spring Boot @ConfigurationProperties allows developer to map the entire .properties and yaml file into an object easily.  
  use the @Value to inject the .properties value one by one
  
  
