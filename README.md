# CS385_VSCode_Debugger
Short tutorial and files used for utilizing the debugger in VS Code


Go to the homework's `build.sbt` file and add the following two lines after the existing `libraryDependencies`
```scala
libraryDependencies += "com.lihaoyi" %% "utest" % "0.7.9" % "test",
testFrameworks += new TestFramework("utest.runner.Framework"),
```
In the "Run and Debug" section, click the dropdown menu and choose "Add Configuration..."
Choose any template you want, and that should open a `launch.json` file.
In that file, delete everything and replace it with 

```scala
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "scala",
            "name": "hw4 debugger",
            "request": "launch",
            "testClass": "tester.HelloTests"
        }
    ]
}
```
the `tester.HelloTests` line will become relevant in a second

Within the hw file explorer, create the following directory: `src/test/scala/HelloTests.scala`

Within the `HelloTests.scala` copy/paste the following:

```scala
package tester

import utest._


object HelloTests extends TestSuite{
  val tests = Tests{
    test("test1"){
      val k = 2
      val arr = Array[(Int, Int)]((1,2), (5,6), (15,16))
      hw4.unoccupiedDays(k, arr)
    }
  }
}
```
***Note that the package "tester" and the name of the file "HelloTests" matches the `testClass` in the `launch.json` file***
