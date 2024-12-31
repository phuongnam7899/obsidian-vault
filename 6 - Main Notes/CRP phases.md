2024-12-31 11:50

Tags: [[Frontend]]

---

![[Pasted image 20241231115049.png]]
# Phase 1: Resources loading
- In this step, the browser will try to get all needed resources (HTML, CSS, JS, Images, Font,...)
- The resources might come from various sources like Backend Server, CDN, Cache, Objects Store (for images), local file,...
- **Analogy**: the browser is a chef, before cooking, he try to get all ingredients from different locations (some of them are from the market, some of them need to be shipped from faraway stores, and some of them is right at the kitchen already,...)
![[Pasted image 20241231115152.png]]
# Phase 2: Parsing
- The browser will parse the loaded resources into DOM and CSS DOM
- DOM: an object that represents the model of the document. Each elements is a node in the DOM tree
![[Pasted image 20241231115310.png]]
- CSS DOM: similar to DOM, but for styles only.
![[Pasted image 20241231115326.png]]
- CSS DOM is separated from DOM
# Phase 3: Render Tree
- Render Tree: all elements that would be shown on the screen (includes both content and styles)
- Invisible elements (like head, element with display:none) are excluded from the Render Tree
![[Pasted image 20241231115415.png]]
# Phase 4: Layouting
- The browser uses the data from Render Tree to calculate the exact position, size,... that determine how each element appears on the screen
![[Pasted image 20241231115511.png]]
# Phase 5: Painting
- This is when all elements actually be painted to the screen
![[Pasted image 20241231115538.png]]


---
# References