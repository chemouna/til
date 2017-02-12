
## Array Store Exception

- If the type of the value being assigned is not assignment-compatible with the 
  component type, an ArrayStoreException is thrown.

- Thrown to indicate that an attempt has been made to store the wrong type of object 
  into an array of objects. 
     Object x[] = new String[3];
     x[0] = new Integer(0);

- Number[] numbers = new Integer[10];
  numbers[0] = Long.valueOf( 0 ); // throws ArrayStoreException

- Java arrays are covariant. This means that given a type S which is a subtype of a type T then S[] 
  is considered a subtype of T[]. This property is described in the Java Language Specification 
  (Subtyping among Array Types). This property is known to lead to ArrayStore exceptions

