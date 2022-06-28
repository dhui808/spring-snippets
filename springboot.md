### differences-between-jar-and-war-in-spring-boot
  Spring Boot can be told to produce a 'fat JAR' which includes all of your module/service's dependencies and can be 
  run with java -jar <your jar>.
    <packaging>jar</packaging>
  
  Spring Boot can also be told to produce a WAR file, in which case you'll likely choose to deploy it to a web container
  such as Tomcat or Jetty.
  Add these lines to your pom.xml file:
  
    <packaging>war</packaging>
  
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-tomcat</artifactId>
        <scope>provided</scope>
    </dependency>
  
### How will you deploy your spring boot application?
