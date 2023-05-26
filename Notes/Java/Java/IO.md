#### There are two types of streams: 
- Byte-based stream
- Character-based stream
# For Character-based operations:
### File class
- to create new file object for the sake of reading or writing:
```java
	File fileObj = new File(/*file name goes here*/);
```
- some useful methods in File class:
```java
fileObj.getName();
fileObj.getAbsolutePath();
fileObj.list(); // returns array of strings of file names inside the 
                //directory
fileObj.listFiles(); // returns array of file objects inside the directory
```
## File output:
- There are *three classes* to achieve this, you may use the one that you deem suitable for the implementation:
	- Writer class (that uses the FileWriter constructor)
	- PrintWriter class
	- Formatter class

	## Writer class
	- There are two ways to initialize any file writer object, you may use which one you like:
	```java
		// If a File object is already created
		Writer writerObject = new FileWriter(fileObj);
		// OR if you did not create a File object yet:
		Writer writerObject = new FileWriter(new File(/*file name*/));
	```
	- NOTE: to *append* text to a file, add an additional argument to the constructor, namely `true` :
	```java
	Writer writerObject = new FileWriter(fileObj, true);
	```
	- writing is simple: 
	```java
	writerObject.write("text");
	```
	##  PrintWriter class
	- same as writer class but we can use `println` to avoid using `\n` every time we want a new line, for example:
	```java
	PrintWriter writerObject = new PrintWriter(fileObj);
	writerObject.println("text");
	```
	## Formatter class
	- same as Writer class but we can format the text to our liking, and then output that text into the file:
	```java
	Formatter writerObject = new Formatter(fileObj);
	writerObject.format("%S", "text"/object);
	```
	#### NOTE: we have to initialize any writer object with a try-catch block:
	```java
	try {
		AnyWriter writerObject = new AnyWriter(fileObj);
		// any functions
		writerObject.close();
	} catch (IOException e) {
		e.printStackTrace();
	}
	```
	- always remember to **CLOSE** the writer, `writerObject.close();`

## File input:
- We will use the Scanner class to read from a file, we will also surround this in a try-catch block but I have omitted it for simplicity:
```java
Scanner scan = new Scanner(fileObj);
```
- To read until the last line in a text file:
```java
while (scan.hasNextLine()) {
	scan.next(); // to read one word
	//OR
	scan.nextLine(); // to read one whole line
}
```
# For Byte-based operations:
## Outputting objects to a file (serialization):
- We need two classes to do this:
	- FileOutputStream
	- ObjectOutputStream
// see lecture notes for this
## Inputting objects from a file (deserialization):
- We need two classes to do this:
	- FileInputStream
	- FileOutputStream
// see lecture notes for this