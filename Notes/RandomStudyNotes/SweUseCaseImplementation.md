# Use-case:
- Submit papers for conference
## Classes to be used:
- Author
- Conference
- Paper
# Tools to use for the app/IDE:
- Gradle (for collaborating/dependency management)
- Git/Github (for collaborating)
- JUnit (for testing)
- OR [testFX](https://bennet-schulz.com/2015/05/how-to-test-your-javafx-fxml-with-testfx.html)

# With regards to testing:
- "To optimize your ROI, your code base should contain many unit tests, fewer integration tests, and still fewer functional tests." (insert picture of test automation pyramid)
- ==read gradle book to find out how to do all this==
# GUI:
[add event to tableView](https://stackoverflow.com/questions/36950130/how-to-add-a-click-event-to-a-tableview-cell-in-javafx)

# Gradle build.gradle for JavaFX
```groovy
plugins {
    id 'application'
    id 'org.openjfx.javafxplugin' version '0.0.9'
}

repositories {
    mavenCentral()
}

javafx {
    version = "19"
    modules = [ 'javafx.base', 'javafx.controls', 'javafx.fxml', 'javafx.graphics', 'javafx.media', 'javafx.swing', 'javafx.web' ]
}

dependencies {

	implementation group: 'org.openjfx.javafxplugin', name: 'org.openjfx.javafxplugin.gradle.plugin', version: '0.0.9', ext: 'pom'

}

mainClassName = 'com.tomgregory.GradleTutorial'
```

# View
- Login scene
	- provide details
	- pop up if account not present, and create the account
	- change scene
- select conference scene
	- tableView / observableList with conferences
	- when conference is clicked, pop up will show, and will confirm to save that conference with author
	- change scene when save the conference
- provide paper details and submit paper for conference scene

// need to add login model and connect to login gui
// need to add save paper details
// and save paper to conference after specifying location
// 
# Model
dataBufferPackage
	singleton DataBuffer class to get author, conference and store papers in files