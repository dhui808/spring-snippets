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
  
### Spring Conditional Annotations
	Institiates a bean of a specific implementaion of an interface under certian conditions.
	For instance, If using Oracle database, then create DaoOracle. If using Informix database, the create DaoInformix.

	In pre-Spring era, one may pass the database flag as a commanline parameter, for instance,
	  if (args[0].equals("oracle") {
		dao = new DaoOracle();
	  } else if (args[0].equals("informix") {
		dao = new DaoInformix();
	  } else {
		throw new ApplicationException("Unsupported database:" + args[0]);
	  }

	Either way, one asks the question: "Is it the Oracle database?" only once, at the application startup time.
  
### Dependency for custom annotation
	Spring won't scan the classess annotated with custom annotations. One can add @Service, @Component, etc., to make
 	those classes the DI target.
  
### Circular dependency
	If Service1 and Service2 depends on each other, we can have constructor dependency injection for Service1 - 
	for example use Lombok @AllArgsConstructor. For Service2, use set dependency injection:
	@Service
	public class Service2 {
		private Service1 service1;

		@Autowired
		public setService1(Service1 service1) {
			this.service1 = service1;
		}
	}
	
