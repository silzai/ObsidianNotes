### Instantiation
- When SinglyLinkedList (SLL) is instantiated, the head and tail are both null so nothing is materialized here. (When an element is add, the element will act as the head, and will contain the data)
- When DoublyLinkedList (DLL) is instantiated, the head and tail are both created as empty nodes, and with them pointing to each other, They are dummy nodes (not containing data). (When an element is added, the element is added after the head (so not replacing head by itself))
### Adding elements
- In DLL we will add using the method addBetween():
```java

private void addBetween(E e, Node<E> prev, Node<E> next) {

	Node<E> newest = new Node<>(e, prev, next);
	prev.setNext(newest);
	next.setPrev(newest);
	size++;

}

```
- We will use this method for the addFirst() and addLast() methods.
- In SLL, to add/insert element after the head and before the tail, we have to traverse the whole list from the head only, unlike addBetween in the DLL.
### Removing Elements
```java

private E Remove(Node<E> node) {

	Node<E> prev = node.getPrev();
	Node<E> next = node.getNext();
	prev.setNext(next);
	next.setPrev(prev);
	size--;
	return node.getData();

}

```
