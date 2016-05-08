

### Tips for learning Haskell

 - use ghci more to ask for the types.

  - trust the types. Always pay attention to type signatures. If they're generic, check the instances
     the typeclass has with Hoogle. If a variable has only one letter, understand what it is by looking at the type.

  - familiarize yourself with as many API functions in as many of the modules of the Haskell platform (especially the base) package as you possible can.

  - Von Neumann's "You don't understand mathematics, you just get used to it" as a pretty sane approach to Haskell follow it.

  - let go of the safety handles, start trying to use and trust the abstraction. Trusting the abstraction is certainly a skill you also need in Haskell.
      After a little while of fumbling about trying to understand Monads you will find you developed some intuition for them. 
      
  - When it gets hard just be sure that you are not stupid or going crazy. What you are experiencing is learning a whole new way of looking at programming
      which will take time and effort, and that it does get better. Much better.

  - learn how to vocalise  everything. For example, for instance Monoid v => Monoid (Map k v) where ... I vocalise it as 'Given v is an instance of Monoid,
      then Map of k and v is an instance of Monoid where ...'. For fmap :: (a -> b) -> f a -> f b, I'd say 'fmap has type, a to b, to f of a, to f of b'. And so on.

 
 
 
