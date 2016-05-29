
## Restart ghc when a new dependency can't be loaded

I was stuck wondering why the new dependency that i added to my .cabal file 
and installed both with stack and cabal wasn't found when i import it and 
load the file in ghc, it turned i just had to restart ghc repl to have it loaded.

(Note to self: Remember this next time).
