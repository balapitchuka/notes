Protocol Buffers

1. Need for protocol buffers

An Evolution of data 
- csv (comma separated values)
	- Advantages
		- Easy to parse
		- Easy to read
		- Easy to make sense of
	- Disadvantages
		- The data types of elements has to be inferred and is not a guarantee.
		- Parsing becomes tricky when data contains commas
		- column names may or may not be there

- Relational Table definitions
	- Relational table definitions add types
		- CREATE TABLE distributors( name varchar(40) );
	- Advantages
		- Data is fully typed
		- Data fits in a table
	- Disadvantages
		- Data has to be flat(it has to fit in table)
		- Data is stored in a database and data definition will be differnt for each database.

- Json
	- Json format can be shared across network
	- Advantages:
		- Data can take any forms (arrays, nested elements)
		- Json is a widely accepted format on the web
		- json can be read by pretty much any language
		- json can be easily shared over a n/w
	- Disadvantages:
		- Data has no schema enforcing
		- Json objects can be quite big in size because of repeated keys
		- No commentss, no Metadeta, no Documentation
- Protocol Buffers
	- Protocol Buffers is defined by a .proto text file
	- You can easily read it and understand it as a human

```
Eg: example.proto
syntax = "proto3"

message MyMessage{
   int32 id = 1;
   string first_name = 2;
  bool is_validated = 3;
}
```
- Advantages
	- Data is fully typed
	- Data is compressed automatically (less cpu usage)
	- Schema(defined using .proto file) is needed to generat code and read the data
	- documentation can be embedded in the schema
	- Data can be read across any language(c#, java, go , python ,javascript etc)
	- Schema can evolve over time, in a safe manner(schema evolution)
	- 3-10x smaller, 20-100x faster than xml
	- code is generated for you automatically 
- Disadvantages
	- Protocol buffers support for some languages might be lacking(but the main ones is fine)
	- Can't open the serialized data with a text editor(b/z it is compressed and serialized)


* Today protcol buffers is used as google for almost all their internal applications
* google has over 48000 protobuf messages types in 12000 .proto files


