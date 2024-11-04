2024-11-02 14:21

Tags: [[Clean Code]]

---

## Functions should be small and do 1 thing
### Bad
```js
	function renderContent(renderInformation) {
	
		const element = renderInformation.element;
		
		if (element === 'script' || element === 'SCRIPT') {
		
			throw new Error('Invalid element.');
		
		}
		
		let partialOpeningTag = '<' + element;
		
		const attributes = renderInformation.attributes;
		
		for (const attribute of attributes) {
		
			partialOpeningTag =
			
			partialOpeningTag + ' ' + attribute.name + '="' + attribute.value + '"';
		
		}
		
		const openingTag = partialOpeningTag + '>';
		
		const closingTag = '</' + element + '>';
		
		const content = renderInformation.content;
		
		const template = openingTag + content + closingTag;
		
		const rootElement = renderInformation.root;
		
		rootElement.innerHTML = template;
	
	}
```
### Good
- Do not need to know the detail logic of related functions, ony that functon is enough
```js
	function renderContent(renderInformation) {
	
		const element = renderInformation.element;
		
		const rootElement = renderInformation.root;
		
		validateElementType(element);
		
		const content = createRenderableContent(renderInformation);
		
		renderOnRoot(rootElement, content);

	}
	
	function validateElementType(...) {...}
	
	function createRenderableContent(...) {...}

	function renderOnRoot(...) {...}
	
```
### What's "One thing"
- Different operations: Operation 1 + Operation 2 (validate + create user)

---
# References