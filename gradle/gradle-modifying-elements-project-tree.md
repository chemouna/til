


# Modifying elements of the project tree

You can alter gradle project properties (all properties in [Project Descriptor](https://docs.gradle.org/current/javadoc/org/gradle/api/initialization/ProjectDescriptor.html) :

project(':projectA').projectDir = new File(settingsDir, '../my-project-a')
project(':projectA').buildFileName = 'projectA.gradle'

And to see descriptions of all project :

```bash
$ gradle -q projects
```
