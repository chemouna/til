
### Gradle Dry Run

To see which tasks are executed in which order but don't them to actualy run
use -m option :
```bash
  gradle -m clean compile
```
will just print the execution order of the tasks but not run them.
this is useful specially when debugging complicated tasks dependencies.
