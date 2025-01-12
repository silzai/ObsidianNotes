# `Text` class
```dart
// ...
child: Text('Welcome to Flutter', style: TextStyle(
	fontSzie: 24,
	color: Colors.black,
	decoration: TextDecoration.none,
	fontFamily: 'Times New Roman',
))
// ...
```
# centering widgets
```dart
@override
  Widget build(BuildContext context) {
    return const Center( // Center used for centering
      /* child: Icon(
        Icons.abc,
        color: Colors.white,
        size: 50
      ),
      ('Welcome to Flutter:D'); */
    )
  }
```
# change background color of widget
```dart
// basically the container is what we are going to change the color of which will effectively change the background color.
@override
  Widget build(BuildContext context) {
    return Container( // Container is like a div in web dev
      color: Colors.white, // background color
      child: const Center(
	      child: Text('Welcome to Flutter'))
    )
  }
```
# `Row` and `Column` widgets
```dart
// spaceAround
child: Column(
	mainAxisAlignment: MainAxisAlignment.spaceAround,
	children: [/* add the widgets to show here*/]
)
// spaceBetween
child: Row(
	mainAxisAlignment: MainAxisAlignment.spaceBetween,
	children: [/* add the widgets to show here*/]
)
// 
```
# `SafeArea` widget
```dart
// different phones have different sizes, so SafeArea positions widgets so that it always stays within the bounds of the phone
// put SafeArea in place of Column widget
return Container(
  child: const SafeArea(
	// ... widgets
	),
  ),
);

```
# `SizedBox` widget
```dart
// whenever we want to give a small gap between widgets, we can put a SizedBox with no color
SizedBox(
	height: 50;
),
// otherwise we can also use Container widget for this
// otherwise we can also use Padding:
  /* Padding(
	padding: EdgeInsets.only(top: 20, bottom: 20, left: 80),
	// (can also do EdgeInsets.all(10.0))
	child: Icon(
	  Icons.transfer_within_a_station,
	  color: Colors.white,
	  size: 60,
	),
  ), */
```
# `TestField` widget
```dart

```
# `Image` widget
```dart
// for image from internet
Image.network('http://example.com/image')
// for image from local device
// first uncomment pubspec.yaml: assets: image/, then do this:
Image.asset('')
```
# `Scaffold` widget
```dart
// Flutter provides a default template called Scaffold
// main things are appBar, body, floatingActionButton, and bottomNavigationBar
return Scaffold(
	appbar: AppBar(title: const Text('My cat app')), // the top bar on the page
	// Scaffolds dont have a child, they have a body
	body: Container(...),
	floatingActionButton: FloatingActionButton(
		onPressed: () {},
		child: const Icon(...) // icon on button, can also put Text()	
	),
	bottomNavigationBar: const BottomNavigation(
		items: const [
			BottomNaviagtionBarItem(
				// one item to add to the bottomNavigationBar
			),...
		]
	)
)
```
# Icon inside text field
- we have prefix and suffix icons to see where to put the icon in the text field/widget
```dart
TextField(
	decoration: InputDecoration(
		suffixIcon: const Icon(Icons.search) // can do any icon like Icon.person
	)
)
```
- there are also `IconButton` which can also be pressed
# border radius
```dart
TextField(
	decoration: InputDecoration(
		border: OutlineInputBorder(
			borderRadius: BorderRadius.circular(10.0)),
	)
)
```