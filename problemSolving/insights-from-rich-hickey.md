
## Insights from Rich Hickey

1 - As always in a system with inheritance, it can be dangerous to rely on
    the concrete types of things:
    ```
    user=> (def a {"a" 2})
    user=> (. a (getClass))
    class clojure.lang.MapEntry

    user=> (def ab {"a" 2 "b" 3})
    user=> (. ab (getClass))
    class clojure.lang.PersistentHashMap
    ```
    Whereas testing whether something implements a specific interface is
    generally more useful:
    ```
    user=> (map? a)
    true
    user=> (map? ab)
    true
    ```
    So : Tying polymorphism to inheritance is bad
          in clojure protocols free us from that.
