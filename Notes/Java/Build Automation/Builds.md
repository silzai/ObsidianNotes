## CI (Continuous Integration)
- Is a combination of *Triggered builds* and *scheduled builds*

## Builds

>*What are builds?*
>They rely on tasks, that are in a specific order, such as compiling source code, copying a file from directory A to directory B, or assembling a ZIP file.

- We need build tools to automatically take care of all these tasks instead of manually doing them one by one.

## Build Tools
- a programming utility that lets you express your automation needs as executable, ordered tasks.
- It has the following components:

>*Build File:*
>contains the configuration needed for the build, defines external dependencies, a scripting language is used to express the build logic, so a Build file can also be called a *Build Script*.

## Gradle
- We can use Gradle to build java applications
- has the DSL (Domain Specific Language) groovy or Kotlin (will use groovy as it is easier for scripting)
- building a java applications would include, 
	- tasks for adding dependencies/external libraries
	- tasks for automatically testing using JUnit
	- tasks for packaging the app into a JAR file

- We will do most common "tasks" in Gradle using the Java plugin, such as building, packaging