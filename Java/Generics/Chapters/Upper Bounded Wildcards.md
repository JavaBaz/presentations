##Upper Bounded Wildcards

The purpose of upper bounded wildcards is to decrease the restrictions on a variable. It restricts the unknown type to be a specific type or a subtype of that type. It is used by declaring wildcard character ("?") followed by the extends (in case of, class) or implements (in case of, interface) keyword, followed by its upper bound.

Syntax :
```Java
List<? extends Number>  
```
Which 
? is a ***wildcard character***.
extends, is a ***keyword***.
Number, is a ***class*** present in java.lang package

Suppose, we want to write the method for the list of Number and its subtypes (like Integer, Double). Using List<? extends Number> is suitable for a list of type Number or any of its subclasses whereas List<Number> works with the list of type Number only. So, List<? extends Number> is less restrictive than List<Number>.

#### Example :

```Java
import java.util.ArrayList;

public class UpperBoundWildcard {


    private static Double add(ArrayList<? extends Number> num) {

        double sum=0.0;
        
        for(Number n:num){
            sum = sum+n.doubleValue();
        }

        return sum;
    }

    public static void main(String[] args) {

        ArrayList<Integer> l1=new ArrayList<>();
        l1.add(10);
        l1.add(20);
        System.out.println("displaying the sum= "+add(l1));

        ArrayList<Double> l2=new ArrayList<>();
        l2.add(30.0);
        l2.add(40.0);
        System.out.println("displaying the sum= "+add(l2));

    }
}  
```