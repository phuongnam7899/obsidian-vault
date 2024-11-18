Source link: https://www.youtube.com/watch?v=ZCAq55BzZ3I

Status: #source-absorbing  

---

## Giới thiệu
- Web worker là tính năng trong JS cho phép chạy các tác vụ song song với luồng chính (main thread/ui thread)
- Main thread: các dòng code chạy từ trên xuống dưới
- -> 1 luồng -> Nếu có bất kỳ tác vụ vào chưa xong -> block các tác vụ phía sau (người dùng ko thao tác được gì trên UI, hay nói cách khác là treo)
- Worker giúp giảm thiểu điều đó: với các tác vụ mất thời gian -> tách ra để chạy trên luồn khác mà không block ui -> trải nghiệm mượt hơn
- Máy tính hiện tại có nhiều nhân -> có thể chạy nhiều luồng -> JS mà chỉ chạy 1 luông thì lãng phí
- Luống hoạt động:
	- Main thread bắn message cho worker
	- Worker có event listener để nghe được 
	- Worker xử lý tác vụ
	- Worker bắn lại message cho main thread
	- Main thread cũng có event listener
![[Web Workers - Công cụ tăng hiệu năng trang web mạnh mẽ 2024-11-18 21.07.12.excalidraw]]

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