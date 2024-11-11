2024-11-09 14:26

Tags: [[Clean Code]] 

---

# ==A class should be open for extension, but closed for modification==
# Bad
- When need to print other things, need to create more function, and if the `verifyData` updated, need to update in all functions
```js
class Printer {

	printPDF(data: any) {}
	
	printWebDocument(data: any) {}
	
	printPage(data: any) {}
	
	verifyData(data: any) {}

}
```
## Good
- The root `PrinterImplementation` that other class extends. The interface to advoid update in many places
- Not update the logic, extends it => Not grow classes
```js
interface Printer {
	print(data: any);
}

class PrinterImplementation {
	verifyData(data: any) {}
}

class WebPrinter extends PrinterImplementation implements Printer {
	print(data: any) {
}

class PDFPrinter extends PrinterImplementation implements Printer {
	print(data: any) {
}

class PagePrinter extends PrinterImplementation implements Printer {
	print(data: any) {
}
```


---
# References