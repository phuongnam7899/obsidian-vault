2024-11-03 09:18

Tags: [[Clean Code]]

---

 Is a function that use to produce (return) a value
```js
	function getTransactionProcessors(transaction) {
		let processors = {
		processPayment: null,
		processRefund: null,
		};
		if (usesTransactionMethod(transaction, 'CREDIT_CARD')) {
			processors.processPayment = processCreditCardPayment;
			processors.processRefund = processCreditCardRefund;
		} else if (usesTransactionMethod(transaction, 'PAYPAL')) {
			processors.processPayment = processPayPalPayment;
			processors.processRefund = processPayPalRefund;
		} else if (usesTransactionMethod(transaction, 'PLAN')) {
			processors.processPayment = processPlanPayment;
			processors.processRefund = processPlanRefund;
		}
		return processors;
}
```

---
# References