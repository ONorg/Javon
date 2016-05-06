#Javon Expression and Statement

##Variable
```java
type var = expression;
var = expression; //type inference
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
###Arithm Expression
```java
int number=222; 
number++
number--
++number
--number
+ - * / % 
number+3-100 * 9 /20 
3a +3 b + Long.valueOf("1e10") //in constant multipitive case, the * char can be ignored, the equivelent is 
3 * a + 3*b + Long.valueOf("1e100")

```
###Logical Expression
```java
Operators: == != && || 
number == 33 && string.charAt(0)==A || 

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
### Assignment
```java
var = expression;
(a, b) = value1, value2; //tuple
t (int a, int b);
```
