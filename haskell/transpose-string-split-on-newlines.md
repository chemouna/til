
## Transpose a string split on newlines

For example, “Hello\nWorld” should return “HW\neo\nrl\nll\nod” :

```Haskell
transpose :: String -> String
transpose input = unlines (inner (lines input))
  where
        inner :: [String] -> [String]
        inner ls | not (any null ls) = map head ls : inner (map tail ls)
        inner _                      = []
```
