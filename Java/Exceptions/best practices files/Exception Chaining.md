# Why Use Exception Chaining?

Exception chaining is an essential technique in Java because it helps retain the full context of an error while adding more meaningful information. Here are the key reasons why you should use it:

## 1. Preserve the Original Cause

When an exception is thrown, the stack trace provides critical information about where and why the error occurred.  
If you replace the original exception without chaining it, this information is lost.

**Why it matters:**  
Losing the original exception makes debugging much harder. Exception chaining allows the original exception to be preserved as the "cause," so both the higher-level and lower-level issues are visible.

## 2. Add More Context

Often, the original exception doesn't provide enough information for someone reading the error to understand what went wrong in the specific context of your application.  
By wrapping the original exception, you can add custom messages or context that makes the error easier to diagnose.

**Why it matters:**  
The developer troubleshooting the issue gets a clearer picture of what happened at both the low level (original exception) and the higher level (your additional context).

## 3. Maintain Abstraction Layers

In well-designed software, exceptions should be translated when they cross abstraction boundaries. For example:
- A low-level data access layer might throw an `SQLException`.
- When this exception reaches the business logic layer, you might want to wrap it in a higher-level `DataAccessException` to reflect its meaning in that context.

**Why it matters:**  
This ensures that:
- The details of the lower layer remain encapsulated.
- The higher layer provides meaningful exceptions relevant to its domain.

## 4. Improve Debugging Efficiency

Exception chaining gives a full "trail" of what went wrong, from the low-level technical cause to the higher-level business impact.  
This trail reduces the time and effort needed to identify the root cause of an issue.

**Why it matters:**  
Without exception chaining, developers may spend unnecessary time tracing the origin of an error.

## 5. Avoid Information Loss

Wrapping an exception without chaining (or catching it and doing nothing) leads to information loss. This can obscure the real issue or make debugging significantly harder.  
Chaining ensures that no details are discarded.

**Why it matters:**  
Preserving the original exception ensures that even "impossible" errors are traceable and fixable.

## How Exception Chaining Works

When wrapping an exception, use the constructor of the new exception to include the original exception as its cause.

**Example:**

```java
try {
    // Low-level operation that throws SQLException
    throw new SQLException("Database connection error");
} catch (SQLException e) {
    // Wrap the original exception in a higher-level exception
    throw new DataAccessException("Failed to access data", e);
}
```

Here:
- The `SQLException` is the original, low-level exception.
- The `DataAccessException` is the higher-level exception that adds context but retains the original error as its cause.

When debugging, both exceptions and their stack traces will be available.

## How It Looks in Practice

When exception chaining is used, the stack trace will show the sequence of exceptions, like this:

```JAVA
DataAccessException: Failed to access data
    at com.example.DataAccessLayer.method(DataAccessLayer.java:25)
Caused by: SQLException: Database connection error
    at com.example.DatabaseConnection.connect(DatabaseConnection.java:12)
```

**Key Benefits:**
- Top-level message (`DataAccessException`): Explains the higher-level issue.
- Cause (`SQLException`): Explains the lower-level technical error.

## Summary

Exception chaining is valuable because it:
- Preserves the original exception and its details.
- Adds meaningful context for better debugging and understanding.
- Maintains clear separation and encapsulation of responsibilities across abstraction layers.
- Prevents information loss, ensuring that the root cause of an error is always traceable.

By chaining exceptions, you create more informative and maintainable error-handling systems, saving time and effort during troubleshooting.


## Always correctly wrap the exceptions in custom exceptions so that the stack trace is not lost

```java
catch (NoSuchMethodException e) {
   throw new MyServiceException("Some information: " + e.getMessage());  //Incorrect way
}
```

This destroys the stack trace of the original exception and is always wrong. The correct way of doing this is:

```java
catch (NoSuchMethodException e) {
   throw new MyServiceException("Some information: " , e);  //Correct way
}
```

## Always include all information about an exception in the single log message

```java
LOGGER.debug("Using cache sector A");
LOGGER.debug("Using retry sector B");
```
Don’t do this.

Using a multi-line log message with multiple calls to LOGGER.debug() may look fine in your test case, but when it shows up in the log file of an app server with 400 threads running in parallel, all dumping information to the same log file, your two log messages may end up spaced out 1000 lines apart in the log file, even though they occur on subsequent lines in your code.

Do it like this:

```java
LOGGER.debug("Using cache sector A, using retry sector B");
```

## Always terminate the thread which it is interrupted

```java
while (true) {
  try {
    Thread.sleep(100000);
  } catch (InterruptedException e) {} //Don't do this
  doSomethingCool();
}
```

InterruptedException is a clue to your code that it should stop whatever it’s doing. Some common use cases for a thread getting interrupted are the active transaction timing out, or a thread pool getting shut down.

Instead of ignoring the InterruptedException, your code should do its best to finish up what it’s doing and finish the current thread of execution.

So to correct the example above:

```java
while (true) {
  try {
    Thread.sleep(100000);
  } catch (InterruptedException e) {
    break;
  }
}
doSomethingCool();
```