Auto-configuration classes can be bundled in external jars and still be picked-up by Spring Boot.
This is important if your applications use external or open source frameworks/libraries.

Spring Boot checks for the presence of a META-INF/spring.factories file within your published jar. 
The file should list your configuration classes under the EnableAutoConfiguration key:

	org.springframework.boot.autoconfigure.EnableAutoConfiguration=\
	com.mycorp.libx.autoconfigure.LibXWebAutoConfiguration
