
## Item 17: Design and document for inheritance or else prohibit it

- the class must document precisely the effects of overriding any method.
     => the class must document its self-use of overridable methods. 

- By convention, a method that invokes overridable methods contains a description
of these invocations at the end of its documentation comment. The description
begins with the phrase “This implementation.” 

- The only way to test a class designed for inheritance is to write subclasses.

- a restriction that a class must obey to allow inheritance is that 
  constructors must not invoke overridable methods, directly or indirectly. 
  
Example
```java
public class Super {
    // Broken - constructor invokes an overridable method
    public Super() {
        overrideMe();
    }
    public void overrideMe() {
    }
}
```
and its subclass:
```java
public final class Sub extends Super {
    private final Date date; // Blank final, set by constructor
    Sub() {
        date = new Date();
    }
    // Overriding method invoked by superclass constructor
    @Override public void overrideMe() {
        System.out.println(date);
    }
    public static void main(String[] args) {
        Sub sub = new Sub();
        sub.overrideMe();
    }
}
```

prints out null the first time, because the overrideMe method is invoked by the Super constructor
before the Sub constructor has a chance to initialize the date field. 
this program observes a final field in two different states! if overrideMe
had invoked any method on date, the invocation would have thrown a
NullPointerException when the Super constructor invoked overrideMe.

- when designing for inheritance. It is generally not a good idea for a class designed
for inheritance to implement Cloneable and Serializable interfaces, as they place a substantial
burden on programmers who extend the class.

- prohibit subclassing in classes that are not designed and documented to be safely subclassed. 
  There are two ways to prohibit subclassing. The easier of the two is to declare the class final. The
  alternative is to make all the constructors private or package-private and to add
  public static factories in place of the constructors. 

- You might want to make a method final so that overriding classes can't change behavior that is counted 
  on in other methods. Methods called in constructors are often declared final so you don't get any 
  unpleasant surprises when creating objects.
