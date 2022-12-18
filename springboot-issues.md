## spring.main.allow-bean-definition-overriding
    What is the theory behind this property?
    
## Consider defining a bean of type 'com.fasterxml.classmate.TypeResolver' in your configuration.
    Re-build the application and the issue is gone. The root cause is, however, not clear
    
    pom.xml
    <dependency>
        <groupId>io.springfox</groupId>
        <artifactId>springfox-swagger2</artifactId>
        <version>3.0.0</version>
        <optional>true</optional>
    </dependency>
    <dependency>
        <groupId>io.springfox</groupId>
        <artifactId>springfox-swagger-ui</artifactId>
        <version>3.0.0</version>
        <optional>true</optional>
    </dependency>
    
    <build>
        <plugins>
            <plugin><artifactId>spring-boot-maven-plugin</artifactId></plugin>
            <plugin><artifactId>maven-war-plugin</artifactId></plugin>
            <plugin><artifactId>build-helper-maven-plugin</artifactId></plugin>
            <plugin><artifactId>maven-dependency-plugin</artifactId></plugin>
            <plugin><artifactId>swagger-codegen-maven-plugin</artifactId></plugin>
        </plugins>
    </build>

### Logback issue Dec. 18, 2022
    Springboot 2.7.6 with Logback 1.2.11 works fine
    Springboot 3.0.0 with Logback 1.4.5 does not work:
        ERROR in ch.qos.logback.classic.pattern.LoggerConverter@18cebaa5 - failed to parse integer string [1.] java.lang
		.NumberFormatException: For input string: "1."
		at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:251)
        
