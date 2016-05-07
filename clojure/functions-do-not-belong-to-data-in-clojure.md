

### Functions do not belong to data in clojure

In idiomatic clojure your functions do not belong to data, they operate on these data. Instead of structures maps or records are used, and you define functions which take these structures as parameters.

you can think of namespace as a unit of encapsulation, not data structure. You can create a namespace, define your data structure in it, write all the functionality you want with plain functions and mark internal functions as private (e.g. define them using defn- form, not defn). Then all non-private functions will represent an interface of your namespace.



