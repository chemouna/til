
### Referencing Multiple dependencies Under the same name:
With gradle you can declare common dependencies in a parent script
and group multiple dependencies under the same name:

```gradle
libraries = [
    spring: [ // Groovy list literal
        "org.springframework:spring-core:3.1",
        "org.springframework:spring-jdbc:3.1"
    ]
]

dependencies { compile libraries.spring } // will then add both dependencies at once.
```

You can also share dependency declarations with advanced configuration options:
libraries = [
    spring_core: dependencies.create("org.springframework:spring-core:3.1") {
        exclude module: "commons-logging"
        force = true
    }
]
