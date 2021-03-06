***

Slides cannot be copy and pasted--ugh.  Go here: `/home/fred/coursera/big_data_analysis_w_scala_\&_spark`

***

### Week 1
* sbt tutorial
  * sbt console
    * You can start the Scala interpreter inside sbt using the console task. The interpreter (also called REPL, for "read-eval-print loop") is useful for trying out snippets of Scala code. Note that the interpreter can only be started if there are no compilation errors in your code.
    * Use `~console` (rather than `console`) to incrementally compile code changes in the Scala REPL when file changes are saved per [here](http://stackoverflow.com/questions/12703535/scala-sbt-console-code-changes-not-reflected-in-sbt-console)
  * sbt compile
  * sbt test
    * The directory src/test/scala contains unit tests for the project. In order to run these tests in sbt, you can use the test command.
  * sbt run
    * If your project has an object with a main method (or an object extending the `App` trait), then you can run the code in sbt easily by typing run. In case sbt finds multiple main methods, it will ask you which one you'd like to execute.
  * sbt submit <uname> <spass>
    * The sbt task submit allows you to submit your solution for the assignment. The submit tasks takes two arguments: your Coursera e-mail address and the submission password.
    * NOTE: the submission password <spass> is not your login password.  It is located on the Coursera programming assignment page in a frame in the top right.
    * FWC - I had to exit sbt (even though tests were passing correctly) and go back in to get submission to work correctly.
* Spark better than Hadoop (10x)
  * retains fault tolerance
  * but massively improves latency by keeping all data in memory (and immutable--i.e. ideas from FP)
  * more expressive APIs
* Spark (and Hadoop) require rewriting code to handle abstractions
  * premature optimization
  * need to think about where data is located, when it is cached, where code is running (driver/executor)
  * this is why the system I built at HBK was better (user didn't have to consider such abstractions)
  * "By default, RDDs are recomputed each time you run an action on them.  This can be expensive (in time) if you need to use a dataset more than once."
    * "Spark allows you to control what is cached in memory.  To tell Spark to cache an RDD in memory, simply call `persist()` [customizable storage level] or `cache()` [MEMORY_ONLY storage level] on it."
    * For example, if you compute an RDD then call `take(10)` on it followed by `count()` it will be recomputed twice, but if you call `persist()` on it first, it gets cached when `take(10)` is called so that `count()` is faster.
    * Hugely useful if iterating repeatedly across a large collection of points, for example (to compute a logistic regression, see spark-1-6.pdf, slide 23).
* **The solutions that Spark provides don't seem to be ones that I've encountered respective problems to in the past (e.g. reiterating over data).  Perhaps this is because of layered computations: once many layers of a computation have been computed and cached, there isn't any need to recompute all the underlying layers; merely reading the top (computed/derived) layer from disk is entirely efficient enough.**  This is why the solution I implemented at HBK worked well.