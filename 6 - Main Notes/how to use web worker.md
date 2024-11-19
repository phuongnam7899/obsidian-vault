2024-11-19 14:36

Tags: [[JS]]

---

## Cách dùng
- Tạo 1 file chứa code worker (chỉ cần là file JS)
```js

function heavyCalculationFunc(data) {}

self.onmessage = (e) => {
	const data = e.data;
	const result = heavyCalculation(data)

	self.postmessage({result})
}

```
- Ở file js chính, có thể gửi message cho worker thực hiện:
```js

worker = new Worker(new URL('./worker.js', import.meta.url))

worker.onmessage = (e) => {
	const { result } = e.data;
}


function calculateWithWorker() {

	worker.postmessage(data)

}

```

> [!info] `import.meta.url` để đảm bảo đường dẫn đến worker luôn đúng
- Chú ý khi không cần dùng worker nữa thì cần tắt đi:
```js

worker.terminate()

```


---
# References