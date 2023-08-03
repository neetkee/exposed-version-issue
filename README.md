# Exposed version issue

Works fine with 0.41.1:

```bash
./gradlew build

BUILD SUCCESSFUL in 888ms
```

Doesn't work with 0.42.0:

```bash
./gradlew build -P newVersion

> Task :compileKotlin FAILED

FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':compileKotlin'.
> Could not resolve all files for configuration ':compileClasspath'.
   > Could not find org.jetbrains.exposed:exposed-spring-boot-starter:0.42.0.
     Required by:
         project :

* Try:
> Run with --stacktrace option to get the stack trace.
> Run with --info or --debug option to get more log output.
> Run with --scan to get full insights.
> Get more help at https://help.gradle.org.

BUILD FAILED in 809ms
```

nerVersion parameter is handled in build.gradle.kts:

```
if (project.hasProperty("newVersion")) {
    implementation("org.jetbrains.exposed:exposed-spring-boot-starter:0.42.0")
}
else {
    implementation("org.jetbrains.exposed:exposed-spring-boot-starter:0.41.1")
}
```