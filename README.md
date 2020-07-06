# Gradle Shadow plugin example

This is just an example of how to use the [Gradle Shadow plugin](https://github.com/johnrengelman/shadow).

My use case: Build a Java library with a relocated Google Guice dependency (could be every other dep) to avoid
dependency problems in the downstream project but leaves the other dependencies like they are. This means the downstream
project still fetching these dependencies via a Maven repository.

## Branches

- [master](https://github.com/dacrome/gradle-shadow-plugin-example): Overview
- [wrong-config](https://github.com/dacrome/gradle-shadow-plugin-example/tree/wrong-config): This branch!
- [successful-config-option-1](https://github.com/dacrome/gradle-shadow-plugin-example/tree/successful-config-option-1)
- [successful-config-option-2](https://github.com/dacrome/gradle-shadow-plugin-example/tree/successful-config-option-2)

## Create jar

`./gradlew clean build`

=> Creates jar in build/libs folder. You can unpack the jar and check the content. Guice was successfully relocated.

## Publish jar

`./gradlew clean publishToMavenLocal`

Publishes jar in `~/.m2/repository/de/davidcrome/gradle/gradle-shadow-plugin-example/1.0-SNAPSHOT` folder. You can
unpack the jar and check the content. Guice was successfully relocated. Please check also the POM in this folder.

## Result

This is not working because the transitive dependencies of the relocated dependency `Guice` are not copied to the jar
by default. When this would be a real lib, it wouldn't be usable because of ClassNotFoundExceptions.
