## Unbounded Wildcards

The unbounded wildcard type represents the list of an unknown type such as List<?>. This approach can be useful in the following scenarios: -

1. When the given method is implemented by using the functionality provided in the Object class.
2. When the generic class contains the methods that don't depend on the type parameter.

#### Example :
```Java
import java.util.Arrays;
import java.util.List;

public class UnboundedWildcard {

    public static void display(List<?> list){
        for(Object o:list){
            System.out.println(o);
        }
    }


    public static void main(String[] args) {
        List<Integer> l1 = Arrays.asList(1,2,3);
        System.out.println("displaying the Integer values");
        display(l1);
        
        List<String> l2 = Arrays.asList("One","Two","Three");
        System.out.println("displaying the String values");
        display(l2);
    }
}
```
