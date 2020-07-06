# Gradle Shadow plugin example

This is just an example of how to use the [Gradle Shadow plugin](https://github.com/johnrengelman/shadow).

My use case: Build a Java library with a relocated Google Guice dependency (could be every other dep) to avoid
dependency problems in the downstream project but leaves the other dependencies like they are. This means the downstream
project still fetching these dependencies via a Maven repository.

## Branches

- [master](https://github.com/dacrome/gradle-shadow-plugin-example): Overview
- [wrong-config](https://github.com/dacrome/gradle-shadow-plugin-example/tree/wrong-config)
- [successful-config-option-1](https://github.com/dacrome/gradle-shadow-plugin-example/tree/successful-config-option-1)
- [successful-config-option-2](https://github.com/dacrome/gradle-shadow-plugin-example/tree/successful-config-option-2): This branch!

## Create jar

`./gradlew clean build`

=> Creates jar in build/libs folder. You can unpack the jar and check the content. Guice was successfully relocated.

## Publish jar

`./gradlew clean publishToMavenLocal`

Publishes jar in `~/.m2/repository/de/davidcrome/gradle/gradle-shadow-plugin-example/1.0-SNAPSHOT` folder. You can
unpack the jar and check the content. Guice was successfully relocated. Please check also the POM in this folder.

## Result

This is working because the transitive dependencies of the relocated dependency `Guice` are added to the published pom
as runtime dependencies. This happens because I added the transitive deps to the `shadow` configuration in the
`dependencies` block!

Upside:
- Small jar because only the relocated dependency was added to the Jar

Downside:
- I need to remember the specific versions of the deps which are used by Guice
