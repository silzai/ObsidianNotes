# State
- To detect there is any typing/change on a text field:
- first set the listener `onChanged`
- then to call the build method again to reflect the change add `setState()`
```dart
var _textFieldValue = 'helllo';

TextField(
	onChanged: (value) {
		setState(() {_textFieldValue = value;});
	},
)
```
- for button
```dart
var sum = "";

ElevatedButton(
	onPressed: () {
		setState(() {sum = getSum();});
	},
	child: const Text('add')
)
```
# State using `Controller`
- to assign state without adding an `onChange` to the widget
```dart
final _textFieldController = TextEdititngController();
```
- and
```dart
TextField(
	controller: _textFieldController
)
```
- then we can use the `controller` variable like this:
```dart
value = double.parse(_textFieldController.text)
```
# `initState()`
- used to do stuff in the initial load of the app
# `ListView`
```dart
Expanded( // Expanded to make the list scrollable
	ListView.bulder(
		itemBuilder: (context, index) {
			return ListTile( // styling for each list item
				title: Text('The title'),
				leading: Image.asset('assets/images/abc.jpg'),
				subtitle: Text()
			)
		}
	)
)
	
```
# add/remove widgets from the widget tree
- just do simple if-else on the widget declaration
```dart

```
