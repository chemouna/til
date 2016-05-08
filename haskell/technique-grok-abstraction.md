

### A Technique to grok abstraction in Haskell

One technique that seems to always help me grok certain abstractions in Haskell is to
 define variations on the same expression, including one using the abstraction I'm having trouble with.

One example is for understanding the State Monad 

```haskell
-- push/pop, stack simulation without using State
pop :: [Int] -> (Int, [Int])
pop (x:xs) = (x, xs)

push :: Int -> [Int] -> ((), [Int])
push x xs = ((), x:xs)

simulateStack s = let
    (_, s1) = push 3 s
    (x, s2) = pop s1
    (_, s3) = push (x * x) s2
    in pop s3

res = simulateStack [1, 2, 3]


-- push/pop, stack simulation using State and bind
pop' :: State [Int] Int
pop' = state (\(x:xs) -> (x, xs))

push':: Int -> State [Int] ()
push' x = state (\xs -> ((), x:xs))

simulateStack' = (push' 3) >>= (\_ -> pop') >>= (\x -> push' (x * x)) >>= (\x -> pop')

res = runState simulateStack' [1, 2, 3]

-- stack simulation using State and do notation

simulateStack'' = do
    push' 3
    x <- pop'
    push' (x * x)
    pop'

res = runState simulateStack'' [1, 2, 3]
```

It's also nice in that it shows the progression in expressiveness.

