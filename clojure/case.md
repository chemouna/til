

### Case in clojure

```clojure
(defn test-condp [x]
(condp = x
    0 "-> 0"
    1 "-> 1"
    (str "else " x)))
```
instead we can use case this way (unlike cond and condp, case doesn't do a sequential search for a match) :

```clojure
(defn test-case [x]
         (case x
           0 "-> 0"
           1 "-> 1"
           (str "else " x)))
```
