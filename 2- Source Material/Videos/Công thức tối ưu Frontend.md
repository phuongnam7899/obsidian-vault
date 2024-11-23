Source link: https://youtu.be/WE2N07bd8ro?si=H04D6vpttyLL8icO

Status:

---

# Gốc rễ để tối ưu - CRP
Thay vì tìm tips & trick -> Cần biết gốc rễ là cách mà browser hiển thị website

> [!info] Bản chất khi muốn tối ưu thứ gì -> Cần biết được tuần tự các bước thực hiện thứ đó

## Giới thiệu cung về CRP
- CRP: critical rendering path ~ Brower rendering pipeline: Là trình tự các bước mà browser thực hiện để hiển thị 1 trang web
![[Công thức tối ưu Frontend 2024-11-19 15.48.27.excalidraw]]
## Các bước trong CRP
![[Công thức tối ưu Frontend 2024-11-19 15.54.56.excalidraw]]
### 1.Load các resourse
### 2. Từ các resource tạo thành DOM và CSS DOM
- DOM là 1 **Object** mô ta cho cấu trúc (**Model**) trang web (**Document**)
- Mỗi phần tử trên HTML được coi là 1 node trong cây
![[Pasted image 20241119160705.png]]
- Tương tự CSS cũng sẽ được tạo thành CSS DOM
![[Pasted image 20241119162126.png]]
> [!info] DOM và CSS DOM  tồn tại độc lập với nhau

### 3. Kết hợp DOM và CSS DOM thành Render Tree
- Render tree: mô tả các thành phần sẽ được hiển thị trên trang (những thành phần không cần hiển thị sẽ không được lấy vào render tree)
![[Pasted image 20241119162045.png]]
### 4. Tính toán các thông tin của các phần tử sẽ được render
- Tính toán từ thông tin trên render tree
- Ví dụ: width: 50% -> 50% của cái gì? Là bao nhiêu px
### 5. Vẽ lên giao diện
- Sau khi có tất cả thông tin -> vẽ lên màn hình

> [!info] Nếu bất kỳ bước nào trong số 4 bước đầu bị chậm -> chậm tới bước Pain

## Blocking resources
- Là những ==resouce mà khiến browser phải dừng lại chờ== để tải hoàn tất thì mới có thể đi tới bước tiếp theo
- 2 loại:
	- **Render blocking**: tài nguyên block việc render của browser (tức là ==ngăn từ bước 2 sang bước 3== trong CRP)
	- **Parser blocking**: tài nguyên ngăn chạn việc parseHTML (tức là ngăn cảm HTML -> DOM trong bước 2)
		- Ví dụ (thẻ script nằm giữa html) -> browser đọc file html từ trên xuống -> sẽ bị block tới khi script đc load xong (vì JS có thể tác động được tói DOM/CSS DOM, browser không chắc script có tác động không -> buộc phải chờ cho chắc)

# Kỹ thuật
- 3 cạnh
## 1. Tối ưu về size - Giảm kích thước cần load
- Kích thước to -> Xử lý lâu
### Minified
- Khi develop, con người cần có xuoogns dòng, tab, khoảng trống, comment để đọc code dễ hơn
- Nhưng máy thì ko cần -> bỏ các phần đó đi có thể giúp giảm kích thước file
- -> Minified giúp thực hiện điềun đó
- Ở thực tế thường tích hợp sẵn công cụ build (như webpack/vite) giúp minified code
	- babel-minify-webpack-pluggin
### Tree-shaking
 - Rung cây -> cành lá héo rụng ~ cắt bỏ các hàm không được dùng đến
 - Các build tool có thể support ddieuf này ==nếu như== sử dụng import đúng (chỉ import những hàm có sử dụng) 
![[Pasted image 20241121140330.png]]
- Công cụ check tree-shaking cho npm: bundlephobia
### Phân tích file bundle
- Bundle analyzer
- Khi sử dụng tool sẽ cho ra kết quả:
![[Pasted image 20241121141720.png]]
- Có thể nhận biết xem file nào lớn hoặc bị load những hàm ko cần thiết
### Code split - Lazy loading
- Nguyên tắc: chỉ load những gì cần load trước
- Ví dụ: 
![[Pasted image 20241121155140.png]]
- Bản chất Tương tự với việc split database => Partition 
### Compress
- Cần xử lý compress ở server
- 2 thuật toán zip:
	- gzip: re trước
	- br: ra sau, tối ưu hơn
- Để biết đã áp dụng thành công chưa, xem trong request load resourse có `content-encoding: gzip` chưa
![[Pasted image 20241121155708.png]]

![[Công thức tối ưu Frontend 2024-11-21 16.00.16.excalidraw]]
### Đối với ảnh
- Cách 1: Làm dung lượng ảnh nhỏ đi nhưng chất lượng ko đổi -> tool: tinypng.com
- Cách 2: chuyển sang định dạng khác (WebP)
	- <mark style="background: #BBFABBA6;">Giảm kích thước</mark> rất nhiều
	- <mark style="background: #BBFABBA6;">Chất lượng ảnh không đổi</mark>
	- <mark style="background: #FFB8EBA6;">Chưa chắc được support </mark>bởi tất cả trình duyệt (có thể check qua caniuse.com)
## 2. Tối ưu cache - Giảm số lần load
- Phừ hợp với các loại resource ==ít thay đổi + sử dụng nhiều==
- Đảnh đổi với sự sai sót nếu data bị thay đổi thường xuyên
- CDN - Content delivery network
	- Bản chất là để các resource ở nhiều server khác nhau trên thế giới
	- User ở đâu -> load từ server gần đó
- Cache trên máy user
	- Kiểm tra xem có ùng cache không -> check header có `Expires`(thời hạn cache đến bao giờ)
		![[Pasted image 20241121163312.png]]
	- Sử dụng ==IndexedDB==:
		- Tại sao ko dùng local storage hay session storage? -> vì giới hạn dung lượng

## Tối ưu wait - Giảm thời gian load
### Async & Defer
- Để giải quyết parser blocking
	- async: 
		- xây dựng DOM chạy song song với load script, chỉ dừng lại khi execute script
		- hường áp dụng cho script như google analytic -> do ==cần chạy script nhanh nhất== có thể
	- defer: 
		- Xây dựng DOM chạy song song với load script, không dừng lại để execute mà chờ parsing xong mới execute
		- Thường áp dụng với script ==ko cần chạy luôn== (popup quảng cáo,...)
![[Pasted image 20241121164301.png]] 
### Lazy loading
- Bản chất: ==chỉ load những gì cần trước==
- Fold: ngăn cách giữa cái nhìn thấy và ko thấy
	![[Pasted image 20241121165126.png]]
- Chỉ load những cái phía trên Fold
- Có thể áp dụng ==IntersectionObserver== cho:
	- Ảnh
	- Call API
- Ảnh/iframe cũng có thể dung propertiy `loading="lazy"` để lazy loading
- Áp dụng Virtual Scroll: lấy sẵn, chỉ giảm thiểu xây dựng DOM
	- Call Lấy hết 100 bản ghi
	- Hiện lần lượt khi scroll xuống
- Áp dụng Infinity Scroll: giảm thiểu cả việc lấy
	- Call lấy 1 phần
	- Khi scroll xuống -> call tiếp
### Optimize long tasks
- Chia thành các chunk
- Chạy lần lượt từng chunk, chạy settimeout 0
![[Pasted image 20241121170511.png]]

### Web worker - Xử lý multi thread
- [[Web Workers - Công cụ tăng hiệu năng trang web mạnh mẽ]]
### Pref-X
- Cốt lõi: Phỏng đoán cần gì -> chuẩn bị trước
#### Preload
- Ngược với lazyload
- 
- Ví dụ:
	- Load trước ảnh: `<link rel="preload" href="image.png" as="image">`
#### Prefetch
- Tải trước để cache lại những tài nguyên cần dùng trong tương lai
#### Preconnect
- Thiết lập kết nối với bên thứ 3 (GG Analytics,...) song song với việc render
- Nên giới hạn 3-4 preconnect để đỡ tranh chấp tài nguyên
#### DNS Prefetch
- Sử dụng để phân giải domain trước
- Dùng cho các resource chưa cần luôn khi load trang
## Công cụ
### Lighthouse
- Đánh giá trang và đưa ra hướng tối ưu
### Coverage
- Kiểm tra % code đã sử dụng
### Request blocking
- Chặn thử ko load để Xác định cái nào quan trọng cái nào không
## Demo


---