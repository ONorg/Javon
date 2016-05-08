#Class Members

##Field
```java
type name = expression;
type name;
type name1, name2...;
name = expression; //type inference
//TODO: consider syntax for multiple fields, name1=name2=...=expression;
```
example
```java
int count = 0;
int count;
int a, b, c;
count = 3; //type inference, int
name = default value string; //type inference, string
```

##Property
```java
type #name //will create inner field
type #name1, #name2, ...; 
type #name: @field; //just wrap the given field, create no inner field
#name: @field; //same as above, type inference
type #name: @field1: @field2; //read field different from set field
#name: @field1: @field2; //same as above, type inference
type #name: @field {
  before: statement; //full method is beforeSetXXX(value)
  after: statement; //full method is afterSetXXX(value)
  set: statement; //full method is setXXX(value)
}
#name: @field {...} //same as above, type inference
type #name {
  get: expression;
  set: statement;
}
#name {...} //same as above, type inference
//TODO: consider syntax for mixed field and property, type field, #property;
```
example
```java
int count;
boolean overflow;
int #level; //create an inner field named as level
int #x, #y;
#amount: @count;
#amount: @count{
	set: value>100? overflow=true; count =value % 100;
}
#amount {
	get: overflow? count+100: count;
	set: value>100? overflow=true; count =value % 100;
}
```

##Method
```java
type method(type arg, ...); //sanity abstract method, and there is no need to employ the keyworld "abstract".
type method(type arg, ...): expression or single statement; //fast way or shorthand
type method(type arg, ...) {
	statement;
	...
	expression/statement;
}
type method(type arg= default value, ...); //named argument
type method(int a, b, c, string name=Adele); //same type can be ignored, this time, it's int for both a, b and c parameter.
type method(int length, int ...args);  //varargs, Variable Argument, same as Java
```
example
```java
int parse();
int sum(int a, b, c){
	checkRange(a, b);
	return a+b+c;
}
int getSetting(String key, int default=3){
	value = map.get(key);
	value==null? default: value#int; //the return can be ignored
}
```
##Lambda field
```java
name = arg1, arg2, arg3: expression/statement/block;
name = (): expression/statement/block;
FunctionalInterfaceType name = arg1, arg2, arg3: expression/statement/block;
FunctionalInterfaceType name = (): expression/statement/block;
nest = args,...: args, ...: expression/statement/block;
//TODO: consider pure function syntax int(int) f = x: x+3;
```
example
```java
Runnable r = (): doSomething();
Function<Integer> f = x: x+3;
BiFunction<Integer,Integer> f = x,y: x+y^2;
Function<Integer> f = x {
	check(x);
	convert(x);
	return x+3;
}
l= x: y: z: x+y+z;
```
##Inner class
```java
class/interface/enum Name<T,...>: superClass, interface1, interface2... ;/{Members...}
```
example
```java
class Inner; //abstract class without the abstract flag
class B<T>: Inner{
  String name;
 }
```
##Initor(Instance Initialization method)
```java
class Name..{
  Type1 field1;
  Type2 field2;
  @init: field1, field2; //there is no need to duplicate field assignment statement
  
  init(args...){
    @init: value1, value2...;
  }
}
```
example
```java
class Example{
  String name;
  int count;
  @init: name, count;
  
  init(String name, int a, b, c){
    @init: name, a+b/c;
  }
  init(String name1, String name2, int a, b, c){
    @init: name1+name2, a+b/c;
  }
  
}
```
