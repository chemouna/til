
### Clojure's confusing contains

It does not check whether a collection contains a value
 instead it checks whether an item could be retrieved with get (=> whether a collection contains a key).
 Which makes sense for sets (they make no distinction between keys and values),
 maps so ```(contains? {:a 1} :a)``` returns true ,
 and for vectors ```(contains? [:foo :bar] 0) is true```, because the keys are indices and the vector in question does "contain" the index 0.

 But nicely in : In Clojure ≥ 1.5 contains? throws when handed an object with no support for "key membership" test.
  so instead to check for contains in a list use :
  ```clojure
    (some #{2} '(1 2 5))
  ```
  which will return 2.
  but there's a catch when searching for a falsy value :
  ```clojure
  (some #{false} [true false true]) ; = nil
  ```
   so instead we can fix that with
   ```clojure
   (some false? [true false true]) ; = true
   ```
   But even better create a function for it:
   ```clojure
   (defn seq-contains? [coll target] (some #(= target %) coll))
    (seq-contains? [true false true] false) ; = true
    ```
