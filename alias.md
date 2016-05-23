#Javon Alias declaration

Yes, typedef again! But it's just in a scope of single file, so there is no spread among multiple javon units so there is no hell of diffusion.

Alias for what? Generic type parameters, Generic types, types with annotations, and types.

The type defined in aliases can be backward referenced, just like normal java generic type parameter declaration.

The pure type alias is useful when a developer from other language, f.e. C family.

NOTE: Javon use bracket pairs [] as a replacement of chevron pairs <> which used in JLS.

there are a few reasons why, but it's a TODO thing:)

TODO: add generic types definition

#Examples
```java
T: Runnable & Function[Integer]
V: List[Map[T, String]]
Tag: Element[String]
Strings: List[String]
NNString: @NonNull String
intfunction: int(string, int)
string: String
E: INTF & Type[T & V, S, W & X[A, B] & Y]
```
Indeed, the & symbol is not so neccessary, consider the following syntax
```java
T: Runnable Function[Integer]
E: INTF Type[T V, S, W X[A, B] Y]
```
Note that annotations can precede any type, even a type parameter of a parameterized type and array symbol
```java
E: INTF @A Type[@B(1) T @B(2) V, S, W @C(1, 2) X[A, B] Y]
@A E: INTF & Others
class Name[@A T]{}
MyArray: @A int @B[] @C[] //but this form consider the follow form
MyArray: @A int [@B] [@C]
```
##About wildcards in Java
JLS provides a syntax for in and out generics because JVM generics defect, ? super T, ? extends T. This form just take onshot semantics, and then it is no any difference from normal Container<T>. So it should be viewed as an invalidity, someone knows which is very prevalent in C++ design philosophy.

Hence, in Javon, there is no wildcard, wildcard is invalidity, so there is no invalidity in Javon :---)

##Why use brackets instead of chevrons
TODO:
