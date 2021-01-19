References:
> Learn Swagger and the Open API Specification from Udemy

### Swagger 
- Swagger is a set of tools that help you create  and use `API` definitions, including the ability to automatically generate documentation for APIs.
- Swagger and Open API Specification are the ways to define an API

### What are APIs?
- Application Programming Interface
- It defines how two pieces of software talk to each other
- In the current section, we are talking about `Web APIs`

### Web APIs
- Not a full webpage, just the data

### API Definition
- It describes
	- What requests are available
	- What the response looks like for each requests

### REST API
- Swagger and Open API Specification are designed for REST APIs
- REST is a type of `web API`
- Representation State Transfer

### API Definition File
- File describes all the things you can do with API
- Lists every request you can make
- Tells you how to make that request
- Tells you what the response will look like



Why create API Definition?
> 
Prerequistes
Swagger
The Open API Specification


### What’s an API Definition File?
**A file that describes everything you can do with an API**
Note: “API” means a collection of related requests
- Server location
- How security is handled (i.e., authorization) 
- All the available requests in that API
- All the different data you can send in a request
- What data is returned
- What HTTP status codes can be returned

### Getting the information to create an OAS file?
**If you are asked to create an OAS file, how do you find the information?**
- Developers can provide rough documentation
- Developers can provide sample requests and responses
	- Most common
- You can figure it out from the code
	- Requires strong coding skills


### Open API Specification
- The Open API Specification (OAS) uses structured data for its API definition files
- You can use one of two structured data formats: YAML or JSON

### YAML
- `Open API Specification Format`
- Stands for `YAML Ain’t Markup Language`
- It’s not a Markup Language like HTML
	- Used for data, not content
- Compared to JSON and XML, it minimizes characters
- It's most often used for configuration files, rather than files passed over the web, like JSON

### YAML Syntax
1. Key value pairs are indicated by a colon followed by a 
```
spacedate: 2017-08-06
firstName: Peter
```

2. YAML Levels
	- Levels are indicated by white space indenting
	- Cannot be a tab indent

3. YAML Types are determined from context
4. Quotes
	- In general, you don’t need quotes around strings
	- Exception:  something that will be interpreted as a number or boolean
	- **Quotes can be either single ' or double "**

5. List
	- Use dash to indicate a list item
	- You don’t need to declare the list
```yaml
cart:  
	- part_no: A4786     
		description: Photoresistor    
		price: 1.47     
		quantity: 4  
	- part_no: B3443    
		description: LED    
		color: blue    
		price: 0.29     
		quantity: 12
```