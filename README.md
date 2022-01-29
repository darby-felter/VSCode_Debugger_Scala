# CS385_VSCode_Debugger
Short tutorial for utilizing the debugger in VS Code for Scala

## `build.sbt`
Go to the homework's `build.sbt` file and add the following two lines after the existing `libraryDependencies`
```scala
libraryDependencies += "com.lihaoyi" %% "utest" % "0.7.9" % "test",
testFrameworks += new TestFramework("utest.runner.Framework"),
```
## `launch.json`
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
Within the hw file explorer, create the following directory: `src/test/scala/HelloTests.scala`

Within `HelloTests.scala` copy/paste the following:

```scala
package tester
import utest._

object HelloTests extends TestSuite{
  val tests = Tests{
    test("test1"){
      val arg1 = 1
      val arg2 = 2
      hw#.functionName(arg1, arg2)
    }
  }
}
```
***Note that the package "tester" and the name of the file "HelloTests" matches the `testClass` field in the `launch.json` file*** <br />
<br />
`hw#.functionName` should be replaced by the current homework and the name of your function (and its parameters). Say I'm working on the `unoccupiedDays` function in `hw4.scala`, then this would be `hw4.unoccupiedDays(k, arr)`

Next, at the top of your `hw#.scala` type in another `package tester`

## Breakpoints
At this point you should be ready to set a break point within your main `hw#.scala` and click the green triangle on the debugger panel. *I have found that you also need to set a break point in `HelloTests.scala` at the line where you call `hw#.functionName(arg1, arg2, etc...)`*
