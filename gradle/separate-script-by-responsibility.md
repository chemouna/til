

### Gradle Separate Script By Responsibility

For projects that have a very long build.gradle a good tip is to separate it by
responsibility into multiple script and apply each of them in the main script,
for example have a tests.gradle that contains tests dependencies, 
a repos.gradle that contains all repos needed in the project and
quality.gradle to declare all plugins and dependencies related to quality
(sonar, pmd,...)

A very good example of this is [Gradle Plugin for Amazon EC2 instances](https://github.com/aestasit/gramazon).
