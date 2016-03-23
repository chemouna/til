
## Gradle task that waits until some input before proceeding

One of the problems i ran into is to proceed with execution of a task when
a previous command has inputed something in console (for example when starting a
service only when ready is printed on console)

```gradle
class ExecWait extends DefaultTask {
    String command
    String ready
    String directory

    @TaskAction
    def spawnProcess() {

        ProcessBuilder builder = new ProcessBuilder(command.split(' '))
        builder.redirectErrorStream(true)
        builder.directory(new File(directory))
        Process process = builder.start()

        InputStream stdout = process.getInputStream()
        BufferedReader reader = new BufferedReader(new InputStreamReader(stdout))

        def line
        while ((line = reader.readLine()) != null) {
            println line
            if (line.contains(ready)) {
                println "$command is ready"
                break;
            }
        }
    }
}

task start(type: ExecWait, dependsOn: [copyToLib]) {
    directory './'
    command "java -jar lib/somejar.jar"
    ready 'Started...' //proceed after this is printed
}
```
