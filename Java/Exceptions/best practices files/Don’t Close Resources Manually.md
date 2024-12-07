# Explanation: Don’t Close Resources Manually

Manually closing resources like files, database connections, or sockets can lead to resource leaks if not done correctly, especially when exceptions occur. Using `try-with-resources` is a better, safer, and cleaner way to manage resources in Java.

---

## Why Avoid Manual Resource Management?

### Error-Prone:
- Forgetting to close resources manually is a common mistake, leading to resource leaks, which can degrade application performance or even crash the system.
- If an exception occurs before the resource is closed, the code may not reach the `close()` call.

### Messy Code:
- Manual closing requires extra boilerplate code, making your code less readable and harder to maintain.

### Difficult Debugging:
- Leaking resources (e.g., file handles, database connections) often results in subtle bugs that are hard to trace and debug.

### Automatic Management:
- With `try-with-resources`, the JVM ensures that the `close()` method of any `AutoCloseable` resource (e.g., files, streams, connections) is automatically called, even if an exception is thrown within the block.

---

## How Try-With-Resources Works

The `try-with-resources` statement automatically closes any resource that implements the `AutoCloseable` interface when the block completes execution, either normally or via an exception.

---

## Advantages of Try-With-Resources:

- **Automatic Resource Management:**  
  Ensures resources are closed properly without manual intervention.

- **Exception Safety:**  
  Resources are guaranteed to be closed even if an exception occurs within the `try` block.

- **Reduces Boilerplate Code:**  
  Eliminates the need for redundant `finally` blocks, keeping the code clean.

- **Fewer Bugs:**  
  Prevents resource leaks caused by forgetting to close resources.

---

## Applicability:

`Try-with-resources` works with any resource that implements the `AutoCloseable` interface, such as:
- Input/output streams (`FileReader`, `BufferedReader`)
- Database connections (`Connection`, `Statement`, `ResultSet`)
- Custom resources (like the `Door` example) that implement `AutoCloseable`.
