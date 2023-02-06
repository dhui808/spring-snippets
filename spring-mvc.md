### Spring MVC Annotations
    https://www.java67.com/2019/04/top-10-spring-mvc-and-rest-annotations-examples-java.html
    
    @Controller: make a class as a web controller
    @RequestMapping: mapping web requests onto methods (method, path/value, consumes, produces)
    @PathVariable	
    @RequestParam	
    @ModelAttribute: the argument should be retrieved from the model. If not present in the model, the argument should 
    be instantiated first and then added to the model.
    @SessionAttributes	
    
    @RequestMapping("/companies/{companyName}")
    public String getCompany(Map<String, Object> map, @PathVariable String companyName) {...}
    
    @GetMapping("/companyList")
    public String listCompanies(Map<String, Object> map, @RequestParam int pageNum) {...}
    
    @PostMapping("/add")
    public String saveNewCompany(@ModelAttribute Company company) {
      companyService.add(company);
      return "redirect:" + company.getName();
    }
    
    @Controller
    @RequestMapping("/company")
    @SessionAttributes("company")
    public class CompanyController {...}

    
    @RestController: a combination of @Controller and @ResponseBody. No need to annotate the method response with @ResponseBody
    
    @RequestBody: tell the Spring to find a suitable message converter to convert a resource representation 
    coming from a client (e.g. JSON) into the specified Java object.

    @ResponseBody: used to transform the Java object to a resource representation requested by the client, e.g. JSON.
    
    @RequestMapping(method=RequestMethod.POST,consumers= "application/json") 
    public @ResponseBody Course saveCourse(@RequestBody Course aCourse){ return courseRepository.save(aCourse); }

    @ResponseStatus: used to override the HTTP response code for a response. You can use this annotation for error handling method.
    
### Types of Method Arguments that that can be used in controllers as input arguments
    https://docs.spring.io/spring-framework/docs/current/reference/html/web.html#mvc-ann-arguments
    
