#Javon Alias declaration

Yes, typedef again! But it's just in a scope of single file, so there is no spread among multiple javon units so there is no hell of diffusion.

Alias for what? Generic type parameters, Generic types, types with annotations, and types.

The type defined in aliases can be backward referenced, just like normal java generic type parameter declaration.

The pure type alias is useful when a developer from other language, f.e. C family.

#Examples
```java
T: Runnable & Function<Integer>
V: List<Map<T, String>>
Tag: Element<String>
Strings: List<String>
NNString: @NonNull String
intfunction: int(string, int)
string: String
```
