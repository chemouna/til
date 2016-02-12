
### Higher-order function Inject in groovy

Groovy has a nice Higher-order function inject Other languages call it a fold, reduce or accumulate.

- for example for sum of the values in a list
 With each :
 ```groovy
def total = 0
(1..4).each { total += it }
```
- However with inject it's a lot nicer :
```groovy
def sum = (1..4).inject(0) { result, i -> result + i }
```
