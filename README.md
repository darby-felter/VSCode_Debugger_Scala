# CS385_VSCode_Debugger
Short tutorial and files used for utilizing the debugger in VS Code


Go to the homework's `build.sbt` file and add the following two lines following the existing `libraryDependencies`
```scala
libraryDependencies += "com.lihaoyi" %% "utest" % "0.7.9" % "test",
testFrameworks += new TestFramework("utest.runner.Framework"),
```
