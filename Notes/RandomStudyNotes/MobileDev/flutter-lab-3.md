# Navigation (`GoRouter`)
- first make `AppRouter` class and records of the paths to make it easier
```dart
class AppRouter {
 static const home = (name: 'home', path : '/');
 static const account = (name : 'account', path : '/account');
 // etc, and query params can be declared as follows
 static const deposit = (name : 'deposit', path : '/deposit:accountNo');
}
```
- then inside the `AppRouter` declare the `router` as follows:
```dart
static final router = GoRouter(
 initialLocation : home.path
 routes : [
  ShellRoute(
   routes : [
    GoRoute(
	  name : home.name,
	  path : home.path,
	  builder : (context, state) => HomeScreen(),
	  routes : [
	    GoRoute(
	     path : account.path,
	     name : account.name,
	     builder : (context, state) => const AccountScreen(),
	    ),
	  ]
	),
   ],
   builder : (context, state, child) => ShellScreen(child: child),
  )
 ],
);
```
- then go to `main.dart` and rename `MaterialApp`, to use `MaterialApp.router()` constructor:
```dart
Widget build(BuildContext context) {
	return MaterialApp.router(
	 router.Config: AppRouter.router,
	 title: //...,
	)
}

```
# State (`riverPod`)
- first will make `notifier` which will give a ready-made variable called `state` which will notify the `consumers` whenever `state` is assigned using `=` assignment operator
```dart
class AccountNotifier extends Notifier<List<Account>> {
 @override
 List<Account> build() {
  initializeAccounts();
  return [];
 }

 void initializeAccounts() async {
  String data = await rootBundle.loadString('assets/data/accounts.json');
  var accountsMap = jsonDecode(data);
  // ...
  var account = accountsMap.map((e) => Account.fromJson(e));
  state = account
 }
}
```
- next we will make a `NotifierProvider` outside of the `Notifier` class: 
```dart
final accountNotifierProvider = 
	NotifierProvider<AccountNotifier, List<Account>>(() => AccountNotifier())
```
- next in `main.dart` wrap it with:
```dart
void main() {
 runApp(const ProviderScope(child: MyApp()));
}
```
- then to 
```dart
class ShellScreen extends ConsumerStatefulWidget {
 @override
 ConsumerState<ShellScreen> createState() => _ShellScreenState();
 
 
}
```