#Class Members

##Field
```java
type name = expression;
type name;
name = expression; //type inference
```
example
```java
int count = 0;
int count;
count = 3; //type inference, int
name = default value string; //type inference, string
```

##Property
```java
type #name //will create inner field
type #name: @field; //just wrap the given field, create no inner field
#name: @field; //same as above, type inference
type #name: @field1: @field2; //read field different from set field
#name: @field1: @field2; //same as above, type inference
type #name: @field {
  before: statement; //full method is beforeSetXXX(value)
  after: statement; //full method is afterSetXXX(value)
  set: statement; //full method is setXXX(value)
}
type #name {
  get: expression;
  set: statement;
}
```
example
```java
int count;
boolean overflow;
int #level; //create an inner field named as level
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
