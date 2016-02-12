
### Groovy split a collection with a closure
Groovy has a nice concise method to split a collection base on some condition :

```groovy
  def (minors, adults) = people.split { it.age < 18 }
```
