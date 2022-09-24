### spring-boot-maven-plugin issue
  This plugin causes problems for multi-module projects, since it treats child modules as regular dependencies,
  which are pulled from the local Maven repo instead of the child modules inside STS, which results in debugging
  problem since no source code is attached to the dependencies in Maven repo. The breaking points won't work.
  
  Solution: Remove spring-boot-maven-plugin from pom.xml
  
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
