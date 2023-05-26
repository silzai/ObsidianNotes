##### Menu
- book room/give booking number
- cancel booking
- guest checkin
- guest checkout
##### Hotel
- room
- List of guests currently residing
- list of previous guests
- list of reserved rooms
- list of available rooms
##### Date
- date
- month
- year
##### guest
- details
	1) ID
	2) bookingNo
- interface RoomBooking
- invoice/payment 
- BookedByReceptionist
- CanceledByReceptionist
##### room
- details
	1) roomArea enum
	2) Kitchenette bool
	3) balcony bool
	4) highRise bool
	5) isBooked bool
- guest
##### receptionist
- details
	1) ID
	2) password

// Booking interface(which contains many things) can be implemented by receptionist, guest and room.**still dont know if we will use this or not**

```java
interface RoomBooking {
	public getbookingDate();
	public getbookedBy();
}
```
// person Super class, can be inherited by guest and receptionist

```java
public abstract Person() {
	protected ID;
}
```
- GUI mein checkbox use hoga to select different room properties (has kitchenette, has balcony etc).