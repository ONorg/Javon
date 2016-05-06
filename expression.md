#Javon Expression and Statement

##Variable and Assignment
```java
type var = expression;
var = expression; //type inference
(a, b) = value1, value2; //tuple
t (int a, int b);
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
operators: (expression.md)
++ -- + - ! ~ * / % >> << >>> < <= > >= == != & ^ | && || 
```java
number+3-100 * 9 /20 
3a +3 b + Long.valueOf("1e10") //in constant multipitive case, the * char can be ignored, the equivelent is 
3 * a + 3*b + Long.valueOf("1e100")
number == 33 && string.charAt(0)==A || number>>3>=2
```
###Conditional and Loop Expression
```java
boolean expression? exp1: exp2
b1? exp1: b2? exp2: exp3 //the ternary expression can be nested
//enumerable switch
enumValue? {
	e1: exp1
	e2: exp2
	...
}
countable? {
	1: exp1
	2..10: exp2
	>400: exp3
	<=100: exp4
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
	...
}
countable? {
	1: stmt1
	2..10: stmt2
	>400: stmt3
	<=100: stmt4
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
 @1..10? print(i);
@array? d: print(d*d);
List<String> list = big, middle, small;
array2 = @list? s, i: print(s+i); //print: big1 middle2 small3
```
