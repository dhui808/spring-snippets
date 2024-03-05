### In a multi-module project, child modules are shown as jar libraries instead of subprojects in STS/Eclipse
Most like there are configuration/code errors in either parent or child modules

### STS-4.3.2 issues
Project structure:  

![Project structure](images/project-folders-1.png)

![Project structure](images/project-folders-2.png)

STS workspace:  

![Project structure](images/sts-explorer.png)  


Maven Repo:  

![Maven repo](images/maven-repo.png)

In contrast, Eclipse jee-2022-06 does not create Maven repo for this project.  
Also the project structure is displayed differently in Eclipse jee-2022-06

![Project structure](images/eclipse-jee-2022-06.png)

### STS-Eclispe-JDK issue
    Fail to start Spring Boot MS
    https://bugs.eclipse.org/bugs/show_bug.cgi?id=562074
    https://github.com/spring-projects/sts4/issues/434
    
