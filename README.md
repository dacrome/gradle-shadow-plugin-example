# Gradle Shadow plugin example

This is just an example of how to use the [Gradle Shadow plugin](https://github.com/johnrengelman/shadow).

My use case: Build a Java library with a relocated Google Guice dependency (could be every other dep) to avoid
dependency problems in the downstream project but leaves the other dependencies like they are. This means the downstream
project still fetching these dependencies via a Maven repository.

## Branches

- [master](https://github.com/dacrome/gradle-shadow-plugin-example): Overview: This branch!
- [wrong-config](https://github.com/dacrome/gradle-shadow-plugin-example/tree/wrong-config)
- [successful-config-option-1](https://github.com/dacrome/gradle-shadow-plugin-example/tree/successful-config-option-1)
- [successful-config-option-2](https://github.com/dacrome/gradle-shadow-plugin-example/tree/successful-config-option-2)
