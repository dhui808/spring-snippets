### Types of Dependency Injection Configurations. 
  There are two different ways of Dependency Injection Configurations.

    XML based Configuration
    Java Annotation-based Configurations

### Different ways of Dependency Injection
  Constructor based Dependency Injection: @Autowired is used on top of the class constructor
    
  Setter based Dependency Injection: @Autowired is used on top of the class’s setter method
  Field or Property-based Dependency Injection: @Autowired is used on top of the field or property in the class
  
  @Primary annotation: Gives priority to the other beans of the same type.
  @Qualifier annotation: Differentiates between the other beans by providing a unique qualifier name.
  
