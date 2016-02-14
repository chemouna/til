
### Gradle Continue Running After Task Failure

When executed with ```--continue```, Gradle will execute every task to be executed
where all of the dependencies for that task completed without failure, instead
of stopping as soon as the first failure is encountered. Each of the encountered
 failures will be reported at the end of the build.

 just if a task fails tasks depending on it will not be executed,  
 For example, since the test task depends on the compilation task so
 tests will not run if there is a compilation error in the code under test.
