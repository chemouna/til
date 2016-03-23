
## Custom configuration if a task is in execution graph

taskGraph.hasTask() checks if a task is in an execution graph (if it it will get executed). Because the task execution graph is only created after the configuration phase, this method has to be called from a whenReady callback:

```gradle
gradle.taskGraph.whenReady { graph ->
    if (graph.hasTask(developerBuild)) {
        // do a custom conditional configuration
    }
}
```
Another, simpler way to solve this problem is to check whether a particular task name is contained in gradle.startParameter.taskNames. However, this has two limitations: First, it compares task names, which can make a difference in multi-project builds. Second, it will only find tasks that have been specified directly (e.g. on the command line), but not dependencies thereof.
