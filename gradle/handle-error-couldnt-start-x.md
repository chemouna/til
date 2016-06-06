
### Handle error net.rubygrapefruit.platform.NativeException: Could not start x

When this error happen in gradle a simple : gradle --stop (or ./gradlew --stop inside
an android project) and rerunning the task is enough to solve the problem.
