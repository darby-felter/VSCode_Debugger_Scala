# CS385_VSCode_Debugger
Short tutorial and files used for utilizing the debugger in VS Code


Go to the homeworks `build.sbt` file and add the following lines 
```scala
libraryDependencies += "com.lihaoyi" %% "utest" % "0.7.9" % "test",
testFrameworks += new TestFramework("utest.runner.Framework"),
```
