
# Refactoring to application

with this parser code with do-notation:

```haskell
p_hex :: CharParser () Char
p_hex = do
  char '%'
  a <- hexDigit
  b <- hexDigit
  let ((d, _):_) = readHex [a,b]
  return . toEnum $ d
```
we can refactor with applicative to make it much shorter and more clear:

```haskell
a_hex = hexify <$> (char '%' *> hexDigit) <*> hexDigit
    where hexify a b = toEnum . fst . head . readHex $ [a,b]
```

onother example : 
```haskell
do a <- e1
   b <- e2
   c <- e3
   return (f a b c)
```
can be refactored to: 
```haskell
f <$> e1 <*> e2 <*> e3
```
or 
```haskell
liftA3 e1 e2 e3
```

generaly here's a method to switch from Monads to applicative style:
Start using liftM, liftM2, etc or ap where you can, in place of do/(>>=). 
```haskell
do x <- fx
   y <- fy
   return (g x y)
```
It can be rewritten to liftM2 g fx fy. In general, whenever the choice or construction of monadic 
actions does not depend on the outcomes of previous monadic actions, then it should be possible to rewrite everything with liftM.
When you notice you're only using those monad methods, then import Control.Applicative and replace return with pure, liftM with (<$>)
(or fmap or liftA), liftM2 with liftA2, etc, and ap with (<*>). 
If your function signature was Monad m => ..., change to Applicative m => ... (and maybe rename m to f or whatever).
