
### Debugging error parameter declaration let should be a vector 

As a newbie to clojure i had this error and couldn't understand way 

```shell
CompilerException java.lang.IllegalArgumentException: Parameter declaration "let" should be a vector
```

```clojure
(defn my-function
  (let ...) 
  ...)
```

it appeared to be just that a  misses a parameter declaration vector.

```clojure
  [] ;; <- fix
  (let ...)
  ...)
```
(defn my-function
