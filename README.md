# VSCode Debugger for Scala
Short tutorial for utilizing the debugger in VS Code for Scala

## build.sbt
Go to the `build.sbt` file and add the following two lines after the existing `libraryDependencies` (the second line may or may not require a comma depending on where you place them)
```scala
libraryDependencies += "com.lihaoyi" %% "utest" % "0.7.9" % "test",
testFrameworks += new TestFramework("utest.runner.Framework"),
```
## launch.json
In the "Run and Debug" section within VS Code, click the dropdown menu and choose "Add Configuration..."
Choose any template you want, and that should open a `launch.json` file.
In that file, delete everything and replace it with 

```scala
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "scala",
            "name": "CS385 debugger",
            "request": "launch",
            "testClass": "tester.HelloTests"
        }
    ]
}
```
the `"testClass": "tester.HelloTests"` line will become relevant in a second

## Test Folder
Within the file explorer, create the following directory: `src/test/scala/HelloTests.scala`

Within `HelloTests.scala` copy/paste the following:

```scala
package tester
import utest._

object HelloTests extends TestSuite{
  val tests = Tests{
    test("test1"){
      val arg1 = 1
      val arg2 = 2
      fileName.functionName(arg1, arg2)
    }
  }
}
```
***Note that the package "tester" and the name of the file "HelloTests" matches the `testClass` field in the `launch.json` file*** <br />
<br />
`fileName.functionName` should be replaced by the name of the scala file you're working with and the name of some function in that file (and whatever parameters you want to test). Say I'm  working in a file called `example.scala` and I have a function called `sumOfInt(x: Int, y: Int)` that takes two integers as input. This would simply look like `example.sumOfInt(1,1)`

Next, at the top of your main scala file, in my example this was example.scala, type in another `package tester`

## Breakpoints
At this point you should be ready to set a break point within your main scala file and click the green triangle on the debugger panel. *I have found that you also need to set a break point in `HelloTests.scala` at the line where you call `fileName.functionName(arg1, arg2, etc...)`*
