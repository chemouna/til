

## Clojure sequences distinction

I read a message in clojure mailing list that realy made understand sequences 
and specialy their relationship to nil : 

"Empty collections are distinct from nil. Clojure does not equate nil 
and '(). 

So nil maps most closely to your notion of #f than anything else. You 
could write your string->numbers function in Clojure returning (1 2 
3), () (no numbers), or nil (not parseable). i.e. as a function that 
returns a list, rather than as a function that returns a seq. 

The big difference, and novelty in Clojure, is sequences. Sequences 
are not collections, esp. they are not lists. There is no such thing 
as an empty sequence. Either there is a sequence (with elements) or 
there isn't (nil). When you ask an empty collection for a sequence of 
its elements it returns nil, saying "I can't produce one". When you 
ask a sequence on its last element for the rest it returns nil, 
saying, "there is no more". 

Some of the sequence function map to functions from Scheme and CL that 
there manipulated only pairs/conses ("lists") and returned sentinel 
values ('() and nil) that represented 'empty' lists. The Clojure 
return values differ in not returning empty collections, but rather a 
sequence or not. Some of the sequence functions have no counterpart in 
Scheme/CL, and map to Haskell/ML-like functions. Some of those 
functions return infinite or calculated sequences, where the analogy 
to concrete data-structures like lists is tenuous at best. 

I think the leap is in distinguishing collections/data-structures and 
seqs/iteration. In both CL and Scheme they are conflated, in Clojure 
they are separate. "

[source](https://groups.google.com/forum/#!msg/clojure/OnagUrQZ1NE/Uwm8fvakuTQJ)
