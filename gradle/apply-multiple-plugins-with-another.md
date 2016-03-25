
## Gradle apply multiple plugins in another main plugin

to have a plugin orchestrate some tasks in other external plugins :
just add them as dependencies to the plugin and in the plugin definition :

```gradle
class MyMainPlugin implements Plugin<Project> {
    @Override
    void apply(Project project) {
        project.plugins.apply ExternalPlugin1
        project.plugins.apply ExternalPlugin2
        project.plugins.apply ExternalPlugin3
    }
}
```
