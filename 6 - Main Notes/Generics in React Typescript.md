2024-11-09 14:40

Tags: [[ReactJS]] [[Typescript]] 

---


```tsx
// Declare
interface Props<T> {
	oneProp: T;
}
function GenericComponent<T>(props: Props<T>) {}

// Using

<GenericComponent<T> />
```


---
# References