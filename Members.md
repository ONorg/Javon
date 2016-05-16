#Class Members

##Field
```java
type name = expression;
type name;
type name1 name2...; //If there are some additional annotations or flags for each field, just split this to multiple lines.
name = expression; //type inference
//TODO: consider syntax for multiple fields, name1=name2=...=expression;
//TODO: tuple field
```
example
```java
int count = 0;
int count;
int a b c; //if there are additional annotations, change to the following syntax
@Validate(10) int a;
@Validate(11) int b;
@Validate(12) int c;
count = 3; //type inference, int
name = default value string; //type inference, string
```

##Property
```java
type #name //will create private inner field, which name pattern is name_field
type #name1 #name2, ...; 
type #name: @field; //just wrap the given field, create no inner field
#name: @field; //same as above, type inference
type #name: @field1 @field2; //read field different from set field
#name: @field1: @field2; //same as above, type inference
type #name(): expression; //read only form
type #name(arg): statement; //write only form
type #name: { // add invariats, at least one form, readOnly or writeOnly or readAndWrite
  get: expression;
  before: statement; //full method is beforeSetXXX(value) can be ignore
  after: statement; //full method is afterSetXXX(value) can be ignore
  set: statement; //full method is setXXX(value)
}
#name {...} //same as above, type inference
//TODO: consider syntax for mixed field and property, type field, #property;
//@Property annotation, "declaration by exception" usage
@Property(Bean) //default, currently, JavaBean name convention pattern, setXXX(value) getXXX()
@Property(Att) //preferable pattern, name(value), name()
@Property(Bean, Att)//more code or delegate
```
example
```java
int count;
boolean overflow;
int #level; //create an inner field named as level
int #x #y;
@Property(Bean, Att) #amount: @count;
#amount {
  get: count;
  set: value>100? overflow=true; count =value % 100;
}
@Property(Att) #amount {
  get: overflow? count+100: count;
  set: value>100? overflow=true; count =value % 100;
}
```

##Method
NOTE: current both = and : allowed for named argument default value.
```java
type method(type arg, ...); //sanity abstract method, and there is no need to employ the keyworld "abstract".
type method(type arg, ...): expression or single statement; //fast way or shorthand
type method(type arg, ...) {
	statement;
	...
	expression/statement;
}
type method(type arg= default value, ...); //named argument
type method(int a b c, string name=Adele); //same type can be ignored, this time, it's int for both a, b and c parameter.
type method(int length, int ...args);  //varargs, Variable Argument, same as Java
type method(int length, int ...a b args); //enhanced varargs, by name reference
type method(type args, int...numbers, string... strings) //enhangced varargs, multiple varargs allowed, of course, the type must be not same
type method(String name, int[] numbers = 1, 2, 3; String priority = 3; int times = 50); //can define array value as default value
```
example
```java
int parse();
int sum(int a b c){
	checkRange(a, b);
	return a+b+c;
}
int getSetting(String key, int default=3){
	value = map.get(key);
	value==null? default: value#int; //the return can be ignored
}
```
NOTE: JLS varargs syntax is simple rough, indeed, the key point is that its source is the lack of the invocation syntax's diversity.
In Javon all is simple perfect:-) The solution is like the following
```java
method(int[] numbers, string[] strings);
method(1, 2, 3; abc, def)
```
##Lambda field
almost like method declaration, except the args declared without parentheses surrounded, and there is no named arguments and default argument value.
```java
name = type1 arg1, type2 arg2, type2 arg3: expression/statement/block; //type can be ignore
name = (): expression/statement/block; //special case for noargs
FunctionalInterfaceType name = arg1, arg2, arg3: expression/statement/block;
FunctionalInterfaceType name = (): expression/statement/block;
nest = args,...: args, ...: expression/statement/block;
//TODO: consider pure function syntax int(int) f = x: x+3;
```
example
```java
Runnable r = (): doSomething();
Function[Integer] f = x: x+3;
BiFunction[Integer,Integer] f = x,y: x+y^2;
Function[Integer] f = x {
	check(x);
	convert(x);
	return x+3;
}
l= x: y: z: x+y+z;
```
##Inner class
```java
class/interface/enum Name[T,...]: superClass, interface1, interface2... ;/{Members...}
```
example
```java
class Inner; //abstract class without the abstract flag
class B[T]: Inner{
  String name;
 }
```
##Initor(Instance Initialization method)
```java
class Name..{
  Type1 field1;
  Type2 field2;
  @init field1 field2; //there is no need to duplicate field assignment statement
  
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
  @init name count;
  
  init(String name, int a b c){
    @init: name, a+b/c;
  }
  init(String name1, String name2, int a b c){
    @init: name1+name2, a+b/c;
  }
  
}
```
## Property in interface
```java
@ReadOnly interface Super {
  type name; 
  @ReadWrite
  type other;
  type exceptProperty;
}

@Writable(except: exceptProperty)
interface Sub: Super{
  type name;
  type other;
}
```
