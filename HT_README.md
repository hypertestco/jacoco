# How to build and use the project ?
1. Go to the project root. Run `mvn clean install` there. You might need to change your Java version to 17 and above. Use `sdkman` for that.

2.  Once built, you can find the `jacocoagent.jar` at `org.jacoco.agent/target/classes/jacocoagent.jar` (path is relative to the root). This jar needs to be run as a `javaagent` by using jvm argument -javaagent.
    ```bash
    -javaagent:/absolute/path/to/jacocoagent.jar=output=file,destfile=/absolute/path/to/coverage.exec
    ```



> **NOTE (JUST FOR INFORMATION):**
>
> The java-agent needs `org.jacoco.core` and `org.jacoco.cli` packages as dependencies. When you build the JaCoCo project, it also builds and installs these dependencies to your local m2 repository.
>
> This is a snippet from `java-agent/pom.xml`, showing `org.jacoco.core` and `org.jacoco.cli` are dependencies of the java-agent:
>
> ```xml
> <dependency>
>     <groupId>org.jacoco</groupId>
>     <artifactId>org.jacoco.core</artifactId>
>     <version>0.8.14-SNAPSHOT</version>
> </dependency>
> <dependency>
>     <groupId>org.jacoco</groupId>
>     <artifactId>org.jacoco.cli</artifactId>
>     <version>0.8.14-SNAPSHOT</version>
> </dependency>
> ```