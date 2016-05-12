#Javon Annotations

Javon Annotations syntax bases on Java Annotations', but there are some simplifications.

##syntax
Both COLON and EQUAL char are valid in Javon annotation, even mixed. 

Why? Just like you ask but I ask not! :-)  or What is the best food for people? it's the why.
```java
@Ann(name1: value1; name2: value2; ...)
@Ann(name1= value1; name2= value2; ...)
@Ann(name1: value1; name2= value2; ...)
```
###Array value
There is only a D1 array in Annotations, the brace pair surrounding is not necessary.
```java
@Ann(name: v1, v2, v3)
```
###Single implicit value
To use single value form, Java Annotation restrict developers to declare the "value" as name of a field. Javon does not.
Javon understand the single value to correspond to the unique required field.
Note that it cannot end with semicolon.
```java
@Ann(value)
@Ann(v1, v2, v3)
```
###Multiple Annotations
This form simplify declaration for custom array structure. Javon Ignore the duplicated names.
```java
@Ann(value1)(value2)(value3)
```
###Nested Annotations
Note that if @string form string occurs in value pair, it is allowed, but will not be processed as annotaton, it's just a normal string. Because @Annotation can only follow ( symbol.
```java
@A(@B)
@A(@Ann(value1)(value2)(value3))
@A(name: value; nest: @Ann(value1)(value2)(value3)))
```
##Other Examples
Of course, the quoted char is not necessary, and the .class suffix must be ignored.

###Java Version
```java
@Schedule(dayOfMonth="last") @Schedule(dayOfWeek="Fri", hour="23") 
@Alert(role="Manager") @Alert(role="Administrator", exception=RuntimeException.class) 
@Author(
   name = "Benjamin Franklin",
   date = "3/27/2003"
)
@SuppressWarnings(value = "unchecked")
@SuppressWarnings("unchecked")
@SuppressWarnings({"unchecked", "rawtypes"})

```

###Javon Version
```java
@Schedule(dayOfMonth=last)(dayOfWeek=Fri; hour=23) 
@Alert(role: Manager)(role: Administrator; exception: RuntimeException)
@Author(name: Benjamin Franklin; date: 3/27/2003)
@SuppressWarning(value: unchecked)
@SuppressWarning(unchecked)
@SuppressWarning(unchecked, rawtypes)
```
