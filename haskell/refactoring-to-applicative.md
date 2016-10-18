
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

