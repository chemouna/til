
# Simulate named argumentsw with newtypes

consider this : 

```haskell
renderBox :: Int -> Int -> Int -> Int -> IO ()
renderBox x y width height = undefined

main = renderBox 2 4 50 60
```
We can convert it to use newtypes like this:
```haskell
newtype XPos = XPos Int
newtype YPos = YPos Int
newtype Width = Width Int
newtype Height = Height Int

renderBox :: XPos -> YPos -> Width -> Height -> IO ()
renderBox (XPos x) (YPos y) (Width width) (Height height) = undefined

main = renderBox (XPos 2) (YPos 4) (Width 50) (Height 60)
```

