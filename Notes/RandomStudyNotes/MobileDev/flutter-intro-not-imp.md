- app
	- screens
		- widgets: some out of the box from flutter, and some we build ourselves
			- state: internal data inside widget, we can modify the UI widgets by changing their state
			- listening to events and handling them
# Entry point
- it is the `main()` function
- for example:
```dart
void main() {
	// here MaterialApp is the root widget 
	// which wraps Scaffold that gives a
	// prewritten structure/theme to the Greeting widget
	runApp(
		const MaterialApp(
			home: Scaffold(
				appBar: AppBar(
					body: const Center(
						Greeting('World')
					) // center
				) // scaffold
			) //  MaterialApp
		)
	);
}
```
# Widget
- have different types of widgets:
	- layout widgets
## `StatelessWidgets`
- do not have internal states that changes
- example:
```dart
class Greeting extends StatelessWidget {
	final String name;
	const Greeting(this.name);

	@override
	Widget build(BuildContext  context) { // this method must be implemented
	return Text('Hello, $name');
	}
}
```
	- BuildContext context is used to pass the properties of the parent widget, like accessing themes etc.
## `StatefulWidgets`
