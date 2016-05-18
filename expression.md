#Javon Expression and Statement

##Variable and Assignment
```java
type var = expression;
var = expression; //type inference
(a, b) = value1, value2; //tuple
(int a, string b) tuple; 
```
example
```java
int count = 3;
count = 3; //type inference
```
##Expression
###Simple Expression
```java
constant //constant value
var //variable reference
method(...) //invocatin with return value
object.method(...) //invocation
```
example
```java
int count; //var declaration
count //var reference
333 222 111 //number, the space allowed, Java form 333_222_111, it's not sciential for mankind :-)
this is a string //string, the space allowed, the quote chars is not necessay, 
//but quoted string is still allowed, but not recommended
//and there are 3 kinds of quoted string, ` ' ", 
"this is a string"
'In a quoted string
the newline chars is allowed'
String.valueOf(333) //method invocation
```
### Method invocation
```java
method(arg1, arg2...) //normal cases
method(args; e1, e2, e3...; ...) //direct array literal
method(arg1, arg2,  name: expression) //with named arguments which must be at the end of parameters
method(args; arg1, arg2: args...: expression); //lambdas
method(arg1; args...: ...args: lambda expression; name: expression);//with lambdas and named arguments
```
example
```java
m(1, string) //normal case
m(1, 2, 3; abc, def; 5) //array
m(string; x:y:z: x+y+z; true) //lambdas
m(hello, name: 3; times: 10) //named arguments
m(hello; x:y:z: x+y+z; name: 3; times: 10) //lambdas and named arguments
```
### String template
```java
int number=333; //var
The max value is $number //normal var reference, the result string is
The max value is 333
The winner is NO_$number //normal var refernece, the result string is 
The winner is NO_333
int first=22; //var
"mixed string is NO_${first}_$number" //compacted var reference, the result string is 
"mixed string is NO_22_333"
```
###Evaluation Expression
operators: [see operator prececence](Operators.md)
++ -- + - ! ~ * / % >> << >>> < <= > >= == != & ^ | && || 
```java
number+3-100 * 9 /20 
3a +3 b + Long.valueOf("1e10") //in constant multipitive case, the * char can be ignored, the equivelent is 
3 * a + 3*b + Long.valueOf("1e100")
number == 33 && string.charAt(0)==A || number>>3>=2
```
###Optional and Converting Expression
```java
expression#type //force type cast, higher priority
expression?#type  //only if type matched do cast
expression?.member //only if type NonNull do invocation
var $ Type? var.member //smart convertion
```
example
```java
long x = 100;
int y = x#int;
Object x = Person(who)
Object y = x;
Person p = y#Person;
Person q = y?#Person; //if y is not an instance of Person, the q has no value.
q = y?#Person; //ERROR, constant must have a value.
String name = y?#Person.name?#String;
Object s = "It's a string"
int length = s $ String? s.length(); //smart convertion, there is no need to call s#String
```
###Conditional and Loop Expression
Javon use @ ? ?! !? combinations as judgement operators instead of if, switch, for and while keyword for conditional and loop expression.
NOTE that the expression means that it can be the right value of assignment statement. Yes, even loop. A loop with multiple values can be used as a generator.
```java
boolean expression? exp1: exp2
b1? exp1: b2? exp2: exp3 //the ternary expression can be nested
//enumerable switch
enumValue? {
	e1: exp1
	e2: exp2
	e3, e4: exp3
	...
}
countable? {
	v1: exp1
	v2..v3: exp2
	boolean expression: exp3
	boolean expression: exp4
}
//LOOP
@boolean expression? expression
@range/enumerable/collectin? value-var, index-var, increment expression: expression;
```
example
```java
int number = 100;
number % 2 == 1? odd : even
number > 50? BIG: number>10? MIDDLE: SMALL
number? {
	>50: BIG
	>10: MIDDLE
	*: SMALL
}
number? {
	1: ONE
	2: TWO
	3..50: MIDDLE
	50..*: BIG
}
visibility? {
	PUBLIC: 0x0001
	INTERNAL: 0x0010
	PROTECTED: 0x0100
}
array = @1..10? i;
@array? d: d*d;
List<String> list = big, middle, small;
array2 = @list? s, i: s+i; //result is big1, middle2, small3
```
## Block
```java
{
	statement
	...
	statement or expression
}
```
##Statement
Block, Assignment, Method invocation, Conditional and Loop, and other control statements.
### Conditional and Loop statement
```java
boolean expression? stmt1: stmt2;
boolean expression? stmt1: b2? stmt2: stmt3 //the ternary statement can be nested
//enumerable switch
enumValue? {
	e1: stmt1
	e2: stmt2
	e3, e4: stmt3
	...
}
countable? {
	v1: stmt1
	v2..v3: stmt2
	boolean expression: stmt3
	boolean expression: stmt4
}
//LOOP
@boolean expression? statement
@range/enumerable/collectin? value-var, index-var, increment expression: statement;
```
example
```java
int number = 100;
Object var;
number % 2 == 1? var = odd :  var= even
number > 50? var = BIG: number>10? var = MIDDLE: var = SMALL
number? {
	>50: var = BIG
	>10: var = MIDDLE
	*: var = SMALL
}
number?{
	1, 3, 5, 7,8, 10,12: days = 31;
	4, 6, 9, 11: days=30;
	2: days= ((year % 4 == 0) && ! (year % 100 ==0) || (year % 400 ==0)? 29: 28;
	*: throw new IllegalArgument(Error month number $number)
}
number? {
	1: var = ONE
	2: var = TWO
	3..50: var = MIDDLE
	50..*: var = BIG
}
int flag;
visibility? {
	PUBLIC: flag = 0x0001
	INTERNAL: flag = 0x0010
	PROTECTED: flag = 0x0100
}
@1..10? i: print(i);
@array? d: print(d*d);
List<String> list = big, middle, small;
array2 = @list? s, i: print(s+i); //print: big1 middle2 small3
```

###Control statement
```java
fallthrough/follow? //currently, it's not certain, feedback needed
@LABEL: //label declaration, in conditional and loop expression and statement
goto LABEL;
//conditional 
enumerable? {
	@LABEL: value/values: statement/expression;
}
//Loop
@LABEL: boolean expression? {
}
return expression/statement; //void value is a valid case
break; //break loop
break LABEL; //break loop goto LABEL
continue; //continue loop
continue LABEL; //continue loop goto LABEL
throw Exception;
```
example
```java
Visibility?{
  PRIVATE: value = 1; fallthrough;
  PROTECTED: println(No public)
  PACKAGE: value = 2; goto DEFAULT;
  PUBLIC: checkPublic()
  @DEFAULT: *: println(Error case)
}
@LOOP: visibitity!=PUBLIC? {
  visibility++;
  visibility == INTERNAL? {visibility-=3; continue LOOP;}
  @1..100? i {
    i % 5 ==0? i % 10 == 0? continue LOOP: break LOOP;
  }
}
void method(): voidMethod();
void method(): return voidMethod();
void method(): field $ String? voidMethod(field): voidMethod2(field);
```
###Exception handler statement
```java
statement :? Any Exception e: statement;
statement :? {
	Exception1 e1: statement1; //handler
	Exception2 e2: statement2; //handler
}
//try block, just use block
{
	statement
	...
}:? {
  handler;
  ...
}
```
example
```java
Thread((): @?: System.in.read()).start() :? IOException e: println(e.getMessage());
x = System.in.read() :? IOException: -1;
x.getClass().getField("field"):? {
  ReflectionException: println("Error reflection")
  AccessException: println("Error Access")
}
{
  method1(); //maybe throw
  method2(); //maybe throw
}:? Exception{
  IllegalArgument: println("error arguments")
  RuntimeException: println("runtime error")
}
```
###Builder pattern statement
```java
instance.{
  method1(...)
  method2(...)
  ...
}
builder/Class{
  name: value
  name: value,
  name: value1, value2
  nest {
    name: value;
    name: value1, value2, ...
    ...
  }
  ...
}
```
example
```java
StringBuilder builder = StringBuile();
builder.{
  append("html{")
  append("body{")
  append("p: paragraph text as follows")
  append("}}")
}
htmlBuilder{
  html{
    body{
      p: paragraph text as follows
      a{href: target/linka; here text just is}
    }
  }
}
Person{
  name: zhangsan
  age: 33
  location: CQ
  favorite: what?
}
UIBuilder{
 width: 30
 height: 30
 color: r, g, b
 margin: 10
 border: 2
 padding: 1, 0, 0, 1
 flow: true
}
```
###lambda statement
same as it is in class member scope
```java
name=arg1, arg2, arg3: expression/statement/block;
```
