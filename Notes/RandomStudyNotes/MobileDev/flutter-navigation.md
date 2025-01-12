# Navigation
- moving between different screens
- to declare routes:
```dart
Widget build() {
	child: MaterialApp(
		routes : {
			'/' () :  
		}
	)
}
```
-  `Navigator` widget maintains a stack which we can `push`, `pop` to show/hide screens
	- does 2 things: screen is pushed to stack, and is visible
- and then we can do `push` or `pop`, for example:
```dart
Navigator.of(context).push( //the root widget `MaterialApp` initializes a `Navigator` by itself, and we can access it by Navigator.of()
	MaterialPageRoute( // wrap it with MateralPageRoute for platfrom specific animation
		builder: (context) {
			return screenName(args);
		}
	)
)
```
- we can declare routes for all screens, called `namedRoutes`, so instead of doing `Navigator.of(context).push()` we can do `Navigator.of(context).pushNamed()`, see `main.dart` in `Navigation` lecture code
# Provider Pattern
- better way to do state management than using `statefulWidget`
- disadvantage of `statefulWidget` is that we cannot use it in another widget, as it is declared inside the widget
- in a large app we dont want to mix the state logic with the UI, so we do state management. To do this, we use a library called `riverpod`
- so we kick the `state` logic from the UI widget, we put it in a separate class/file called a `Provider` which holds the state and gives methods to change the state, and the UI keeps looking at the `Provider`, and if there is change, then change the UI
- can make the `Provider` available to any screen/widget, there are different kinds of `Provider` such as `Provider<List>`, `FutureProvider<>`
```dart
class randomNotifier extends ChangeNotifier {
	final randomProvider = 
}
```
- `changeNotifier` comes from `riverpod`
- then in the UI:
	- instead of extending `StatefulWidget`, we will extend `ConsumerWidget`
```dart
class randomScreen extends ConsumerWidget {
	
}
```
## bypassing default behavior of `pop` in navigator
- as we visit screens, it adds it to the back-stack
- but we need more control than this such as log in flow, and if we go back, the default behavior will go to log in screen again will get poor UX,
- pop until and remove until
- so if we want to bypass screens when pressing the back button, for ex:
	- A -> B -> C, but when going back, I want to go C -> A, then will do
```dart
Navigator(context).popUntil(ModalRoute.withName('A'))
```
- another very useful one is `Navigator.pushAndRemoveUntil`, commonly used in log-in, and other screen navigations, as screens will be pushed and removed as soon as a new screen comes, upto a specified route/screen
```dart

```
- 