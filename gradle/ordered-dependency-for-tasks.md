
### Gradle ordered dependency for tasks

- writing that a task A depends on task B then C then D in order is not straight
  forward in gradle, here's a little helper method to help with it :
  ```groovy
    static void dependsOnOrdered(Task task, Task... others) {
        task.dependsOn(others)
        for (int i = 0; i < others.size() - 1; i++) {
            others[i + 1].mustRunAfter(task[i])
        }
    }
  ```
