## JavaFX
- Main window is called a Stage. 
- inside the Stage, we have scenes, we can change scenes.
- Inside the scenes, we have components (buttons, labels etc.).
- we put components in layout containers, for example:
	- Vbox container will have arrangement in rows stacked up.
	- Hbox container has arrangement side by side horizontally.
### to initialize a container/layout
```java
VBox root= new VBox(15);
root.getChildren().addAll(/**enter all the component variables/objects you want to add in vbox in order*/);
```
### FlowPane
- is a flexible layout that can change size in terms of screen size changes.
	- to set the orientation to vertical:
```java
	pane.setOrientation(Orientation.VERTICAL);
```
### nesting layouts
- For example, nesting other panes in borderPane:
```java
BorderPane pane = new BorderPane();
// to nest hbox or vbox in the BorerPane layout
pane.setTop(getHBox());
pane.setLeft(getVBox());
// getHBox() and getVBox will have the nested pane initialization and all contents of the panes
pane.setCenter(); // to set in center of BorderPane
```
## To initialize a scene then using stage.show() to display the main window screen
```java
Scene scene = new Scene(root); // enter container/layout name as argument
stage.setScene(scene); // stage is the Stage object 
stage.show(); 
```

# miscellaneous actions:
### applying action on buttons
```java
buttonExample.setOnAction(e -> /**function name*/)
```
### when taking input from text box
- when we take input from text box, it is a string type.
- we have to convert the input to double if we want to do calculations.


### checkbox:
```java
CheckBox vertCHK = new CheckBox();
vertCHK.setOnAction( e -> { if vertCHK.isSelected(){ /* Do some action*/}})
```

### radio button
- radio buttons must be put as members of one toggle group to **make only one button be selected at a time.**
- to make new toggleGroup:
```java
	ToggleGroup group = new ToggleGroup();
```
- set different radio buttons to the group:
```java
	radioButtonExample.setToggleGroup(group)
```
- now setOnAction:
```java
radioButtonExample.setOnAction( e -> {if radioButtonExample.isSelected() {/*Do some actions*/} } ;
```
### slider
- add functionality to the slider:
```java
Slider slide = new Slider();
slide.valueProperty().addListener( e -> { /*do some action*/})
```
