

## Apply a list of functions to an argument

Apply a list of functions to an argument, generating a list of the results : 
```clojure 
    ((juxt inc dec (partial * 3)) 4)
```

