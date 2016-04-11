
## Rx Java design insight: Provide orthogonal primitive operators

Example : no need to provide takeUntill(filer)
since it can be used by composing a set of other operators :

```scala
 object MainScala {
  def main(args: Array[String]): Unit = {

    val xs = Observable.items(0,1,2,3,4)

    val ys = xs.takeWhile(x => x < 3)
    ys.subscribe(y => println(y)) // 0,1,2

    val zs = xs.publish[Int]((xs: Observable[Int]) => xs.takeUntil(xs.dropWhile(x => x < 3)))
    zs.subscribe(z => println(z)) // 0,1,2,3
    readLine()
  }
 }
```

this analogy is very useful for library design in general: No need to provide
every possible use case just provide separate orthogonal constructs that can be
combined or composed together to provide whatever a user needs.

@see [Source](https://github.com/ReactiveX/RxJava/issues/1649)
