2024-12-31 13:03

Tags: [[Programming]]

---

- Anology: Imagine what happen when we shake the apple tree: All ripe apples (which are not tightly attached to the tree) fell down
![[Pasted image 20241231130434.png]]
- The same thing happens in tree shaking but with code, but the “tree” is a dependency tree. Only related parts are kept in the bundled file
![[Pasted image 20241231130533.png]]
- Bundlers like Webpack or Rollup natively support tree shaking, but we need to ensure that the code uses ES6 syntax to import/export, and only import what is needed
- Example:
![[Pasted image 20241231130842.png]]
![[Pasted image 20241231130857.png]]
![[Pasted image 20241231130914.png]]


---
# References