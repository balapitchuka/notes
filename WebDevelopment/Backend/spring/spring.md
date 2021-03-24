# Spring Notes

What is Spring About
Dependency Injection
Different injection types
Xml vs Java based configurations

What is Spring MVC?
Dispatcher servlet
Working of multiple requests from clients at same time

What is Spring Boot?
JSP/Thymleaf
RestController
Spring Data
Spring Rest

Jackson
payload validation using annotation
parital updation


Spring Security
Spring SSL, deployment





### Rest API Development Using Spring Boot

`@RestController`
- The @RestController annotation was introduced in Spring 4.0 to simplify the creation of RESTful web services. 
- It’s a convenience annotation that combines @Controller and @ResponseBody – which eliminates the need to annotate every request handling method of the controller class with the @ResponseBody annotation
- As name suggest, it shall be used in case of REST style controllers i.e. handler methods shall return the JSON/XML response directly to client rather using view resolvers. 
- Every request handling method of the controller class automatically serializes return objects into HttpResponse if using @RestController

#### Difference between @Controller and @RestController in Spring MVC

**Spring MVC - @Controller**
```java

@Controller
@RequestMapping("/api/v1")
public class EmployeeController {
    @Autowired
    private EmployeeRepository employeeRepository;

    @GetMapping("/employees")
    public @ResponseBody List<Employee> getAllEmployees() {
        return employeeRepository.findAll();
    }

    @GetMapping("/employees/{id}")
    public @ResponseBody ResponseEntity<Employee> getEmployeeById(@PathVariable(value = "id") Long employeeId)
        throws ResourceNotFoundException {
        Employee employee = employeeRepository.findById(employeeId)
          .orElseThrow(() -> new ResourceNotFoundException("Employee not found for this id :: " + employeeId));
        return ResponseEntity.ok().body(employee);
    }
    
    @PostMapping("/employees")
    public @ResponseBody Employee createEmployee(@Valid @RequestBody Employee employee) {
        return employeeRepository.save(employee);
    }

    @PutMapping("/employees/{id}")
    public @ResponseBody ResponseEntity<Employee> updateEmployee(@PathVariable(value = "id") Long employeeId,
         @Valid @RequestBody Employee employeeDetails) throws ResourceNotFoundException {
        Employee employee = employeeRepository.findById(employeeId)
        .orElseThrow(() -> new ResourceNotFoundException("Employee not found for this id :: " + employeeId));

        employee.setEmailId(employeeDetails.getEmailId());
        employee.setLastName(employeeDetails.getLastName());
        employee.setFirstName(employeeDetails.getFirstName());
        final Employee updatedEmployee = employeeRepository.save(employee);
        return ResponseEntity.ok(updatedEmployee);
    }

    @DeleteMapping("/employees/{id}")
    public @ResponseBody Map<String, Boolean> deleteEmployee(@PathVariable(value = "id") Long employeeId)
         throws ResourceNotFoundException {
        Employee employee = employeeRepository.findById(employeeId)
       .orElseThrow(() -> new ResourceNotFoundException("Employee not found for this id :: " + employeeId));

        employeeRepository.delete(employee);
        Map<String, Boolean> response = new HashMap<>();
        response.put("deleted", Boolean.TRUE);
        return response;
    }
}
```

**Spring MVC - @RestController**
```java
@RestController
@RequestMapping("/api/v1")
public class EmployeeController {
    @Autowired
    private EmployeeRepository employeeRepository;

    @GetMapping("/employees")
    public List<Employee> getAllEmployees() {
        return employeeRepository.findAll();
    }

    @GetMapping("/employees/{id}")
    public ResponseEntity<Employee> getEmployeeById(@PathVariable(value = "id") Long employeeId)
        throws ResourceNotFoundException {
        Employee employee = employeeRepository.findById(employeeId)
          .orElseThrow(() -> new ResourceNotFoundException("Employee not found for this id :: " + employeeId));
        return ResponseEntity.ok().body(employee);
    }
    
    @PostMapping("/employees")
    public Employee createEmployee(@Valid @RequestBody Employee employee) {
        return employeeRepository.save(employee);
    }

    @PutMapping("/employees/{id}")
    public ResponseEntity<Employee> updateEmployee(@PathVariable(value = "id") Long employeeId,
         @Valid @RequestBody Employee employeeDetails) throws ResourceNotFoundException {
        Employee employee = employeeRepository.findById(employeeId)
        .orElseThrow(() -> new ResourceNotFoundException("Employee not found for this id :: " + employeeId));

        employee.setEmailId(employeeDetails.getEmailId());
        employee.setLastName(employeeDetails.getLastName());
        employee.setFirstName(employeeDetails.getFirstName());
        final Employee updatedEmployee = employeeRepository.save(employee);
        return ResponseEntity.ok(updatedEmployee);
    }

    @DeleteMapping("/employees/{id}")
    public Map<String, Boolean> deleteEmployee(@PathVariable(value = "id") Long employeeId)
         throws ResourceNotFoundException {
        Employee employee = employeeRepository.findById(employeeId)
       .orElseThrow(() -> new ResourceNotFoundException("Employee not found for this id :: " + employeeId));

        employeeRepository.delete(employee);
        Map<String, Boolean> response = new HashMap<>();
        response.put("deleted", Boolean.TRUE);
        return response;
    }
}
```


#### Lombok Library

**1. Avoid Repetitive Code**

- Java is a great language but it sometimes gets too verbose for things you have to do in your code for common tasks or compliancy with some framework practices. 
- These do very often bring no real value to the business side of your programs – and this is where Lombok is here to make your life happier and yourself more productive.
- The way it works is by plugging into your build process and autogenerating Java bytecode into your .class files as per a number of project annotations you introduce in your code.
- Including it in your builds, whichever system you are using, is very straight forward. Their project page has detailed instructions on the specifics. Most of my projects are maven based, so I just typically drop their dependency in the provided scope and I'm good to go
```xml
<dependencies>
    ...
    <dependency>
        <groupId>org.projectlombok</groupId>
        <artifactId>lombok</artifactId>
        <version>1.18.10</version>
        <scope>provided</scope>
    </dependency>
    ...
</dependencies>
```
2. @Getter @Setter @NoArgsConstructor




#### Implementing Validation for RESTful Services with Spring Boot

`What is Validation?`
- You expect a certain format of request for your RESTful Service. 
- You except the elements of your request to have certain data types, certain domain constraints.
- What if you get a request not meeting this constraints?

**You should return a proper error response**
- Clear message indicating what went wrong? Which field has an error and what are the accepted values? What the consumer can do to fix the error?
- Proper Response Status Bad Request.
- Do not include sensitive information in the response.

Response Statuses for Validation Errors
Recommended response status for validation error is -> 400 - BAD REQUEST