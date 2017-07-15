# Scala Hello World

A very quick introduction/experimento into Scala.

## Install (via Homebrew in Mac OS)

```sh
brew update
brew install scala
# you should be able to do: scala -version
```

## Usage

```sh
scalac HW.scala
scala HW

# or directly
scala HW.scala
```

## References

- http://www.scalatra.org/getting-started/project-structure.html


### Override methods simply by signature:
```scala
abstract class SemiGroup[A] {
  def add(x: A, y: A): A
}
abstract class Monoid[A] extends SemiGroup[A] {
  def unit: A
}
object ImplicitTest extends Application {
  implicit object StringMonoid extends Monoid[String] {
    def add(x: String, y: String): String = x concat y
    def unit: String = ""
  }
  implicit object IntMonoid extends Monoid[Int] {
    def add(x: Int, y: Int): Int = x + y
    def unit: Int = 0
  }
  def sum[A](xs: List[A])(implicit m: Monoid[A]): A =
    if (xs.isEmpty) m.unit
    else m.add(xs.head, sum(xs.tail))

  println(sum(List(1, 2, 3)))
  println(sum(List("a", "b", "c")))
}
```

### Servers for APIs

- http://www.scalatra.org/
- http://www.scalatra.org/getting-started/first-project.html
- https://github.com/scalatra/scalatra-website-examples/blob/master/2.4/http/scalatra-http-demo/src/main/scala/org/scalatra/example/HttpExample.scala
- http://xitrum-framework.github.io/
- http://doc.akka.io/docs/akka-http/current/scala/http/introduction.html

