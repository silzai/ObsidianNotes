# To use Gradle dependencies in java/eclipse
- we first make a Gradle project in eclipse (or import an existing one)
- Then we simply add the dependencies in the build script
- Then right click on the project in eclipse, and in Gradle context menu, will click *Refresh Gradle Project*
- This will let us use external JARS in our project, and eclipse will successfully recognize the libraries when we type `import` statements in our code.