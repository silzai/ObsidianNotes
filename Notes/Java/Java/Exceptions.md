```java
try {
	// code that might contain exception
} catch (Exception e){ // can also specify which type of exception there is
		// what to do if there is an exception
  } finally { 
			// what to always do finally
	}

```

- Note: we can also `throw` exceptions in the catch block using the `throw` keyword, if we don't know what to do with the exception.