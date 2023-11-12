### Advantage of Java Generics

1. Type safety
2. Avoid type csting
   (It offen happens in the Lists.)
3. Compile-Time checking

### Advanced details

1. Java Generics using Map

Short note :
```java
Map<Integer,String> map=new HashMap<Integer,String>();
```
Long note :

```java
import java.util.*;
        class TestGenerics{
            public static void main(String args[]){
                Map<Integer,String> map=new HashMap<Integer,String>();
                map.put(1,"vijay");
                map.put(4,"umesh");
                map.put(2,"ankit");

                //Now use Map.Entry for Set and Iterator
                Set<Map.Entry<Integer,String>> set=map.entrySet();

                Iterator<Map.Entry<Integer,String>> itr=set.iterator();
                while(itr.hasNext()){
                    Map.Entry e=itr.next();//no need to typecast
                    System.out.println(e.getKey()+" "+e.getValue());
                }
            }
        }

```

---
2. Generic class
we can use generic types in our classes.
The T type indicates that it can refer to any type (like String, Integer, and Employee). The type you specify for the class will be used to store and retrieve the data.
```java
class MyGenContainer<T>{
    T obj;

    void add(T obj){
        this.obj=obj;
        }
    
    T get(){
        return obj;
        }
}  
``` 

Note :
The type parameters naming conventions are important to learn generics thoroughly. The common type parameters are as follows:

T - Type
E - Element
K - Key
N - Number
V - Value

---

3. Generic Method
Like the generic class, we can create a generic method that can accept any type of arguments. Here, the scope of arguments is limited to the method where it is declared. It allows static as well as non-static methods.

```Java
public class GenericsMethods {

	//Java Generic Method
	public static <T> boolean isEqual(GenericsType<T> g1, GenericsType<T> g2){
		return g1.get().equals(g2.get());
	}
	
	public static void main(String args[]){
		GenericsType<String> g1 = new GenericsType<>();
		g1.set("Pankaj");
		
		GenericsType<String> g2 = new GenericsType<>();
		g2.set("Pankaj");
		
		boolean isEqual = GenericsMethods.<String>isEqual(g1, g2);
		//above statement can be written simply as
		isEqual = GenericsMethods.isEqual(g1, g2);
		//This feature, known as type inference, allows you to invoke a generic method as an ordinary method, without specifying a type between angle brackets.
		//Compiler will infer the type that is needed
	}
}
```

---

### Wildcard in Java Generics
The ? (question mark) symbol represents the wildcard element. It means any type. If we write <? extends Number>, it means any child class of Number, e.g., Integer, Float, and double. Now we can call the method of Number class through any child class object.

We can use a wildcard as a type of a parameter, field, return type, or local variable. However, ***it is not allowed to use a wildcard as a type argument for a generic method invocation, a generic class instance creation, or a supertype.***

we have 3 types of wildcard usage in Java Generics :
1. [Unbounded Wildcards](/Java/Generics/Chapters/Unbounded%20Wildcards.md) (no inheritance)
2. [Upper Bounded Wildcards](/Java/Generics/Chapters/Upper%20Bounded%20Wildcards.md) (using child classes by using **extends**)
3. [Lower Bounded Wildcards](/Java/Generics/Chapters/Lower%20Bounded%20Wildcards.md) ((using parent classes by using ***super***))