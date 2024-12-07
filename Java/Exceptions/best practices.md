# General tips :

## Explicitly define exceptions in the throws clause

Lazy developers use the generic Exception class in the throws clause of a method. Doing so is not a Java exception handling best practice.

Instead, always explicitly state the exact set of exception a given method might throw. This allows other developers to know the various error handling routines they can employ if a given method fails to execute properly.


## Catch the most specific exception first

This is more of a compiler requirement than a Java exception handling best practice, but a developer should always catch the most specific exception first, and the least specific one last.

If this rule is not followed, the JVM will generate a compile time error with a fairly cryptic error message that is difficult to understand.

Make your software development life easier, and always catch the most specific exception in your code first.


## Use modern exception handling techniques

Is Java verbose? It is if you stick with the 20-year-old exception handling techniques.

Java has added many features around error and exception handling that simplify development and greatly reduce the verbosity of Java code.

Take advantage of the ability to catch multiple exceptions in a single catch block, automatically close resource with the try-with-resources block, and use RuntimeExceptions so other developers aren’t forced to handle the exceptions you throw.


## Never catch Throwable

Well, it is one step more serious trouble. Because java errors are also subclasses of the Throwable.

Errors are irreversible conditions that can not be handled by JVM itself. And for some JVM implementations, JVM might not actually even invoke your catch clause on an Error.