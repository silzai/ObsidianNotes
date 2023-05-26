- app
- controller
- repository

- Order of execution:
	- first the main method in the app calls *launch(args)* and then the GUI pops up which automatically calls the *initialize()* method in the controller class and that will call a method from Repository class that will **load** the data in.

