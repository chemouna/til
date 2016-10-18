
# Mixing Monad and Applicative Opertors 

take this piece of code for example:
```haskell
do a <- e1
   b <- e2 a
   c <- e3
   return (f b c)
```

can be refactored to use an applicative style:
```haskell
f <$> (e1 >>= e2) <*> e3
```
