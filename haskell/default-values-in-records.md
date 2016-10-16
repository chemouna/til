
# Default values in records : 

You cannot associate default values with a type, but you can define as many record values as you like and use them as basis for updating elements.

```haskell
data Foo = Foo { bar :: Int, baz :: Int, quux :: Int }
 
fooDefault = Foo { bar = 1, baz = 2, quux = 3 }
 
newRecord = fooDefault { quux = 42 }
````
