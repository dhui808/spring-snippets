# spring-snippets
### Resources
[Dependency Versions](https://docs.spring.io/spring-boot/docs/current/reference/html/dependency-versions.html)

### Common Application Properties
[Common Application Properties](https://docs.spring.io/spring-boot/docs/current/reference/html/application-properties.html)  
[Spring Boot 2.7.x Server properties](https://docs.spring.io/spring-boot/docs/2.7.x/reference/htmlsingle/#appendix.application-properties.server)  
[Spring Boot 3.1.x Server properties](https://docs.spring.io/spring-boot/docs/3.1.x/reference/htmlsingle/#appendix.application-properties.server)  
[ServerProperties.java](https://github.com/spring-projects/spring-boot/blob/main/spring-boot-project/spring-boot-autoconfigure/src/main/java/org/springframework/boot/autoconfigure/web/ServerProperties.java)

### spring-boot-dependencies
    spring-boot-dependencies does not load some dependencies, e.g. httpclient. Maven or Springboot issue?
    
### How does Spring determine which packages should be scanned to resolve all dependencies?
    Spring uses a combination of default conventions and  @ComponentScan annotation.
    
    By default, Spring will scan all packages and sub-packages under the package where the @SpringBootApplication annotation is 
    defined.
    
    Alternatively, the @ComponentScan annotation can be used to specify the packages to be scanned.
    
### parameter-0-of-constructor-in-required-a-bean-type-of-spring-boot
	Could be caused the missing/incorrect configuration that causes a dependency not being instantiated.

### How does Spring Boot refresh when external properties change
	Use @RefreshScope on the Spring beans that depend on certain external configuration
 	Enable the /refresh endpoint: 
  	management.endpoints.web.exposure.include=*
	Use Spring Cloud Config Server:
	spring.config.import=optional:configserver:http://localhost:8888/

	In SCCS config, specify the git url of the perperties file repo:
 	spring.cloud.config.server.git.uri=https://github.com/mygithubid/mypropertiesrepo.git
	Or:
 	spring.cloud.config.server.git.uri=file:///Desktop/config
  
 	Invokes the Actuator’s refresh command:
	curl localhost:8080/actuator/refresh -d {} -H "Content-Type: application/json"
### Logging Headers/Body With Apache HttpClient
	<dependency>
	    <groupId>org.apache.httpcomponents</groupId>
	    <artifactId>httpclient</artifactId>
	</dependency>

	RestTemplate restTemplate = new RestTemplate();
	restTemplate.setRequestFactory(new HttpComponentsClientHttpRequestFactory());

