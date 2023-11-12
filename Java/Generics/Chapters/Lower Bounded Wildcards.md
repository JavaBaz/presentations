## Lower Bounded Wildcards

The purpose of lower bounded wildcards is to restrict the unknown type to be a specific type or a supertype of that type. It is used by declaring wildcard character ("?") followed by the super keyword, followed by its lower bound.

Syntax : 
```Java
List<? super Integer>  
```

which
? is a ***wildcard character***.
super, is a ***keyword***.
Integer, is a wrapper ***class***.

Suppose, we want to write the method for the list of Integer and its supertype (like Number, Object). Using List<? super Integer> is suitable for a list of type Integer or any of its superclasses whereas List<Integer> works with the list of type Integer only. So, List<? super Integer> is less restrictive than List<Integer>.

#### Example :

```Java
import java.util.Arrays;
import java.util.List;

public class LowerBoundWildcard {

    public static void addNumbers(List<? super Integer> list) {
        for(Object n:list){
            System.out.println(n);
        }
    }
    
    public static void main(String[] args) {

        List<Integer> l1=Arrays.asList(1,2,3);
        System.out.println("displaying the Integer values");
        addNumbers(l1);

        List<Number> l2=Arrays.asList(1.0,2.0,3.0);
        System.out.println("displaying the Number values");
        addNumbers(l2);
    }
}
```