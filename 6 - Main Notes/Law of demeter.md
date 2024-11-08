2024-11-08 16:35

Tags: [[Clean Code]]

---

Avoid: `this.customer.lastPurchase.date` (Except dealing with data container/structures)
- ==Principle of Least Knowledge==: dont depend on the internals of "strangers" (other objects that you dont directly know), for example: `date`
- Code in a method should only access direct internals of:
	- Object it ==belong to==
	- Object ==stored in properties of that object==
	- objects which are ==received as method parameters==
	- Objects which are ==created in the method==
- =="Tell, dont ask"==: Dont ask for information and then use it. Instead, tell other class what to do
### Example
```js
class Customer {
	lastPurchase: any;
	getLastPurchaseDate() {
	return this.lastPurchase.date;
	}
}

class DeliveryJob {
	customer: any;
	warehouse: any;
	constructor(customer, warehouse) {
		this.customer = customer;
		this.warehouse = warehouse;
	}

	deliverLastPurchase() {
	
		// const date = this.customer.lastPurchase.date;
		// const date = this.customer.getLastPurchaseDate();
		// this.warehouse.deliverPurchasesByDate(this.customer, date);
		
		this.warehouse.deliverPurchase(this.customer.lastPurchase);
	
	}

}

```


---
# References