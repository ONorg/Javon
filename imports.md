#Javon import statement

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
