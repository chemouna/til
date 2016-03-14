
### Observable use of .publish and takeUntil on itself

Using .publish and takeUntil on yourself is a very common pattern that more
people should use.
```scala
import rx.lang.scala._

object MainScala {
  def main(args: Array[String]): Unit = {
  val xs = Observable.items(0, 1, 2, 3, 4)
  val zs = xs.publish[Int]((xs: Observable[Int]) => xs.takeUntil(xs.dropWhile(x => x < 3).tail))
  zs.subscribe(z => println(z)) // 0,1,2,3
  readLine()
}
```
Other examples uses :
https://github.com/avexa/connect4robot/blob/master/src/bot/playerInteraction.js
[Fizzbuzz solution here]( https://github.com/owyke/rx-java-stepup/blob/master/src/test/java/se/mejsla/stepup/rxjava/lab2/ObservableUtilsTest.java)  
