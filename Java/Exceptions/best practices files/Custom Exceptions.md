# Why Use Custom Exceptions?

Custom exceptions are specific to your application and provide more meaningful error messages. They make your code clearer, easier to debug, and better aligned with your business logic.

## Key Benefits:
- **Clarity:** Instead of generic exceptions, custom ones like `InvalidUserInputException` make it obvious what went wrong.
- **Grouping:** Allows specific handling of related errors (e.g., `PaymentFailedException` and `OutOfStockException`).
- **Context:** Add extra details like error codes or problem-specific data.
- **Domain Logic:** Encapsulate business-specific problems for better abstraction.

## Example: 

```java
public class InvalidUserInputException extends Exception {
    public InvalidUserInputException(String message) {
        super(message);
    }
}


if (input == null) throw new InvalidUserInputException("Input cannot be null.");
```




```java
public class InvalidUserInputException extends IllegalArgumentException {
    public InvalidUserInputException(String message) {
        super(message);
    }
}


if (input == null) throw new InvalidUserInputException("Input cannot be null.");
```
