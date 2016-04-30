
### Running a single Clojure test using leiningen

to run a single test when refactoring some code and needing to reflect the changes in the test suite via the build system and not just from inside the REPL ?

```bash 
lein test :only test-namespace/function
```
