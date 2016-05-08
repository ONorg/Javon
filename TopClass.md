# Javon top class file

## package
```java
package pack.age.name
```
## import
[see imports](imports.md)
```java
import package.ClassName alias, ClassName alias...
import package. //same as java import pakcage.*
import package.ClassName#StaticField  //same as java import static
import package.ClassName#staticMethod //same as java import static
import {
  package.ClassName alias, ClassName alias
  ...
}
```
#Examples
```java
import java.util.concurrent.CurrentHashMap CHMap, CurrentLinkedDeque deque

import {
  java.util. //find all in java.util package
  java.lang.String#valueOf //import static String.valueOf
  java.lang.Long# //import static Long.*
}
```
## alias
[see alias](alias.md)
```java
alias{
  TypeName: Type1 & Type2 & GenericType<TypeParameter> & @annotation Type
  ...
}
```
example
```java
alias{
	T: Runnable & Function<Integer>
	V: List<Map<T, String>>
	Tag: Element<String>
	Strings: List<String>
	NNString: @NonNull String
	intfunction: int(string, int)
	string: String
}
```
## Class
```java
@annotation... flags class/interface/enum/@interface Name<T1, T2...>: SuperClass, Interface1, Interface2 ;/{
}
```
Example.javon
```java
package com.xyz.example;

import {
	java.util.List
	java.util.concurrent.ConcurrentHashMap CHMap
	xyz.annotations.NonNull
	
}
alias{
  T: Function<Integer> & Charsequence
  V: Number
  string: @NonNull String
  cstring: Comparable<string>
}
class AbstractExample;
class Example<T, V>: AbstractExample, Charsequence, cstring{
}
```
