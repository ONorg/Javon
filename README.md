# Javon
Next generation language for JVM based ON

*Candidate names: alang? a lang, A-Lang or C(DEF[F#bG]GHI)J bG-lang Big-Lang?


#Sample

```java

@syntax{
	newline: SEMI;
	comment: SEMI;
	SingleLineComment: SEMI;
	MultiLinesComment: SEMI;
	//SLC, MLC, NL==>lines string
}

//additional file type
package pack.age.name;
module mod.ule.name;

//module example
module javon.hello;
version 2.2.0
vendor jx.com

require java.base, java.javafx //multiple module dependencies, without given version
require java.base@1.8
require java.javafx@2.1<=version<=8.6.0
require java.javafx@[2.1, 8.6.0]

exports javan.hello;

//example package
@annotation(version: 1.2.0; strings: abc, def)
package pack.age.name;


//.javon file
package pack.age.name;
import pack.age.Class alias, Class2 alias2;
import { 
	pack.age.Class alias;
	pack.age.Class alias, Class2 alias2;
}
alias{
	T: Runnable & Function<String>;
	V: List<Map<T, String>>;
	Person: Person<String>;
	Tag: Element<String>;
	StringList: List<String>;
	string: @Nonull String;
	intfunc: Function<int>;
	intf1: int (string, int);
}
@A @B @C(1)(2)(3)
@Property(Bean, Att)
class Name<T, V>: Class, Interface1, StringList{
	static max = 9999 9999 8765 4321;
	string field1;
	field2 = 0x1234 5678;
	field3 = method()+333 222 111;
	field4 = System.nanoTime() % 2 == 0? 3: 2;

	
	int #prop;
	@Property(Att)
	#prop1: @field2;
	#prop1: @field2: @field2;
	#prop2: @field2 {
		before: must(value>2);
		after: must(value>2);
		set: field3=value+222;
	}
	#prop2{
		get: field3+222;
		set: field3+value;
	}
	
	//lambda fields in class 
	Runnable r=() method();
	intfunc f1 = (x) x+3;
	intfunc f1 = x: x+3;
	intfunc f2 = x {
		method1();
		method2();
		x+3;
	}

	enum State{
		OPEN, RUNNING, CLOSE, TERMINATED, ABORTED;
	}
	class Person{
		Object name;
		String field1, field2;
		#prop1: @name {
			value.startsWith("BG")? field2=value: field2= value;
		}
	}
	class Student: Person{
		beforeSetProp1(String value){
			return value.startsWith("BG2")? value: "BG2_0";
		}
	}
	class Task{
		Person source;
		Object target;
	}
	//Method Task with same name as inner class Task. 
	//	It's ok in JLS, and allowed in Javon as well.
	Task Task(){ 
		println(field4)
	}
	
	field5 = Person(name){}
	field6 = Task.init(source, target);
	field7 = Task();
	
	static{
		max+=2222;
	}
	
	State state();
	
	type value1() : field3+222;
	
	int metdho1(String name=zhangsan, intfunc f){}
	
	int method2(string name, intf1 f): f(name.length>3? 1:2);
	
	(int a, int b) swap(int a, int b){
		return b, a;
	}
	
	type method(string name, int a, b, c){
		(x, y) = swap(2, 3);
		assert x==3;
		assert y==2;
		
		method1(name: lisi; f=x: x+3);
		method1(x: x+3);
		method1(wangwu; x: x+3);
		
		//lambdas in method
		f1(x): x+3;
		method1(f1);
		
		f2(x){
			field1=2;
			x+3;
		}
		method1(lisi, f2);
		method2("wangwu", f2);
		
		int a, b, c;
		long x = 10000L<<32;
		a = x#int + 32;
		ubyte b1, b2, b3, b4;
		c = b1#int<<24 | b2#int<<16;
		
		task = Task(zhangsan, great);
		Person p1 = task.source;
		Student s1 = task.source#Student;
		S1 = task.source?#Student;
		string = task.source#Person.name#String;
		string = task?.source?#Student.name?#String;
		
		string =value1();
		a = value1().length> 3? 222: 333;
		string.startsWith("a")? b = 3;
		string.startsWith("a")? b = 3: c = 3;
		
		len = value().length();
		len<3? b = 3:
		len<10: b= 10: b = 20;
		b = len? {
			<3: 3;
			<10: 10;
			>10 & <100: 100;
			10<len<100: 100;
			10..100: 100;
			default: 20;
		}
		c = state()? {
			OPEN: 0; goto DEFlabel;
			LABEL: ABORTED, TERMINATED: -1; fallthrough/follow;
			RUNNING: 1;
			DEFlabel: default: 2;
		}
		string = c?{
			0: "open";
			<0: "exception";
			1..10: "normal";
			default: "closed";
		}
		array = 1, 3, 5, 7, 9;
		@array? i, d: printf("%s %s\n", i, d);
		
		@State? s: println(s);
		@State? i, s: printf("%s: %s\n", i, s);
		@1..100? print(i);
		@1..100? @1..100? println(i*j);
		@len<3? {
			println(len++);
		}
		@LABEL: len<3? {
			method1("test", f(len));
			println(len);
			@len<100? {
				len % 11? break LABEL;
				len+=random(5);
			}
			method();
			len++;
		}
		@?{ 
			method1();
			field3 == 3333 ? break;
			method2();
		}
		@Order(width, height)
		builder.{
			width(30)
			height(30)
			color(red, green, blue)
			margin(10)
			border(2)
			flow(true)
		}
		builder{
			width: 30
			height: 30
			color: red, green, blue;
			margin: 10
			border: 2
			padding: 1, 0, 0, 1;
			flow: true
		}
		try( x=new FileInputStream("test.file")): c = x.read();

		Thread((): method2(zhangsan, f2)).start(): RuntimeException ex: throw StacklessException(ex);
		value = Class.getField("field").get(instance)? throw {
			InvocatinTargetException: e.printStack();
			ReflectionException: throw StacklessException(e);
		}
		
		int c;
		stream  x;
		c = stream.read(): RuntimeException: throw IllegalArgumentException(e);
		
		scope(failure) clear();
		scope(exit) finallyClear();
		@1..100? count+=stream.read();
		
		count = 3;
		string = string template contains $count references;
		s2 = string tempalte refers ${count}_s variable;
		
		t1 (int a, int b) = 2, 3;
		t2 = swap(t1);
		(a, b) = swap(t2);
		assert a==2 && b ==3;
		
		array = 1, 2, 3;
		Object[] objects= 111, name, "222", bbb, {2, 2, 3, 3};
	}
	(int a, String b) tupleMethod(){}
	
	//interoperation with Java
	@Tuple(int a, String b)
	Object[] tupleMethod(){};
}
```
