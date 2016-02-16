
### Attaching Debugger for a Task

To debug a gradle task :
Add :
```groovy
myTask {
  if (System.getProperty('DEBUG', 'false') == 'true') {
        jvmArgs '-Xdebug',
            '-Xrunjdwp:transport=dt_socket,server=y,suspend=y,address=9009'
  }
}
```
so that :
```bash
 $ gradle -DDEBUG=true myTask
```
will break in wherever you set your breakpoint.
and even better add a global init.gradle in $HOME/.gradle/ to do
for all task of a certain type for all your projects :
```groovy
allprojects {
    tasks.withType(JavaExec) {
        if (System.getProperty('DEBUG', 'false') == 'true') {
            jvmArgs '-Xdebug',
                '-Xrunjdwp:transport=dt_socket,server=y,suspend=y,address=9009'
        }
    }
}
````
