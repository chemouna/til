
### Initialization and class not found exceptions

#### ExceptionInInitializerError:
 Signals that an unexpected exception has occurred in a static initializer. 
 An ExceptionInInitializerError is thrown to indicate that an exception occurred during 
 evaluation of a static initializer or the initializer for a static variable. 
 
 - Static initialization occurs when a class is loaded by a class loader. Its code can either come in 
   the form of a static block (i.e. static{ ..}), or as a call to  a static method for initializing a static data member 
 
 - checked exceptions are not allowed by the compiler. When an unchecked exception occurs, on the other hand, 
   it is wrapped by the ExceptionInInitializerError, which is then thrown in the context of the thread that triggered the class loading. 
   
   Example:
    ```java 
    class Useless {
        static {
            if (true) // Bypasses the compiler check for obvious exceptions in initializers
                throw new RuntimeException();
            }
        }
 
     public class TestUselessClass {
        public static void main(String[] args) {
            try {
                new Useless(); // Triggers class loading
            } catch (ExceptionInInitializerError e) {
                e.printStackTrace();
            }
            new Useless();
        }
    } 
    ```
  Since class loading is lazy, the class gets loaded and initialized only when we try to create an instance from it. 
  The class loading fails because initialization can’t complete, and then the ExceptionInInitializerError is thrown 
  and when we try to use the class anyway. The class loading will not be attempted again, and this time we get a NoClassDefFoundError. 
  This error is more severe than ClassNotFoundException, and it indicates in this case that we are trying to use a class that is in 
  an erroneous state due to a failed initialization.              

 
 
