Source link: https://www.youtube.com/watch?v=E19bDedgsyo&t=415s

Status: #source-eating 

---
# Yêu cầu
## Functional
- Đăng được bài
- Xem được bài viết
- (Follow được)
# Mô tả hệ thống hiện tại
![[Thiết kế hệ thống mạng xã hội 200tr Users - System Design 2024-11-30 09.58.59.excalidraw]]

>[!info] Tại sao cần Primary DB và Object Storage riêng?
>Một cái chỉ lưu ảnh, một cái chỉ lưu nội dung bài
- Timeline service: xử lý việc  lấy timeline
- Post service: xử lý đăng bài
- PrimaryDB: để lưu và write các nội dung bài viết
- Secondary DB: chỉ để read (sẽ đồng bộ data tư PrimaryDB)
- Object Storage: để lưu ảnh
- Cache
- Post process service: Phần phôí thông tin sau khi có bài
	- Tìm thông tin người đang theo dõi người đăng post (ở cache / DB)
	- Cập nhật trang home của follower

# Vấn đề 1
- User có 200tr followers -> 
	- tắc ở<mark style="background: #FFB8EBA6;"> post processor service</mark>
		- Do phải đọc thông tin 200tr người theo dõi -> cập nhật timeline
	- tắc ở <mark style="background: #FFB8EBA6;">cache data store/ second data store</mark>
# Giải pháp
- Đối với những user có lượng follower nhiều -> TÌm cách giảm số lần phải đọc và ghi, bằng cách <mark style="background: #BBFABBA6;">phân loại người dùng</mark>
	- Online
	- Active: online trang 3 ngày
	- Inactive: chưa online trong >3 ngày 
	- Blocked: User đã bị khóa tài khảon
- Post processor <mark style="background: #BBFABBA6;">chỉ tìm + cập nhật home cho user online</mark>
- Vấn đề phát sinh: user active/inactive khi online lại không thấy bài viết mới -> <mark style="background: #FFB8EBA6;">không đáp ứng</mark> <mark style="background: #FFB8EBA6;">được nhất quán dữ liệu</mark>
# Giải pháp
- Update timeline service: khi active user online -> query secondary db -> lấy các post:
	- của user mà:
		- người đó theo dõi
		- có lượng follower lớn (để tránh bị duplicate dữ liệu với cơ chế cho các user bình thường)
	- có thời gian post sau lần gần nhất user đó offline
- Cập nhật vào cache data store + trả về client
	- Sau đó lúc user online -> query lấy lần nữa -> bị duplicate các bài của user ít follower
# Tối ưu cache store
- <mark style="background: #BBFABBA6;">Chỉ lưu cho những user active và online</mark> 
- Những inactive user -> khi vào phải tạo lại home timneline
- Vấn đề: <mark style="background: #FFB8EBA6;">khi user online offline liên tục</mark> -> Vẫn phải hit vào second db nhiều
# Giải pháp
-  Lưu lại giá trị lần gấn nhất query
- Khi active user online -> check xem lần query gần nhất có >X phút không -> thì mới update timeline nữa
- Cần cache lại thông tin những users mà user đang theo dõi
- Vấn đề: <mark style="background: #FFB8EBA6;">khi nhiều người cùng online</mark> -> KOL đăng 1 bài -> vẫn phải update home cho rất nhiều follower
# Giải pháp
- <mark style="background: #BBFABBA6;">Chuyển tải cho phía follower</mark>:
	- Khi KOL đăng bài
		- Post process service cập nhật vào cache bài viết mới của KOL (thay vì upodate cho tất cả followers)
	- Khi follower online:
		- Query trong cache/second db -> lấy danh sách KOL đang theo dõi
		- Lấy danh sách bài viết mới của những KOL đó
		- Update vào home timeline
- Vấn đề: khi lưu nhiều vào cache -> <mark style="background: #FFB8EBA6;">tải sẽ dồn vào cache data store</mark> => cache down -> down hết
# Giải pháp
- Tách ra các cache riêng
	- Cho post
	- Cho danh sách người đang theo dõi
- Vấn đề:
	- Primary data store: nếu chậm là chậm hết
# Giải pháp tăng tốc độ write cho primary db
- Tìm DB hỗ trợ in-memory write (Cassandra)
- Tăng khả năng mở rộng (Cassandra có khả năng mở nhiều node)
- Cấu hình DB
	- Tăng size redo log -> lâu đầy -> ít switch -> nhanh hơn
	- Setup buffer dung lượng sẵn cho các loại cần ghi nhiều -> không tốn thời gian tự động nở ra khi đầy
	- (Ghi parallel,...)
![[Thiết kế hệ thống mạng xã hội 200tr Users - System Design 2024-12-01 13.42.20.excalidraw]]
# Tối ưu cho object store
- Tối ưu dung lượng:
	- Nén lại trước khi lưu
	- CDN cache
# Tối ưu read-db
- Cache
- Nhân bản lên theo chiều ngang
# Local cache
- Giải quyết vấn đề khi đang đăng bài mà mất mạng -> tránh mất dữ liệu cho người dùng

# ĐÚC KẾT
- Các bước xây dựng system design
	- Phân tích yêu cầu bài toán (functional, non-functional)
	- Thiết kế ở mức đơn giản nhất: đảm bảo tính đúng đắn cho các functional requirements (MVP)
	- Phân tích yêu cầu phi chức năng (scalability, hiệu năng, availability)
	- Update lại thiết kế ban đầu để đáp ứng được
- Mindset tách DB: Tách thành đọc và ghi
- Cache để giảm tải DB
- Tách các service để giảm tải
- Khi cần lưu ảnh cần object store
- Xử lý bất đồng bộ -> message queue -> tránh user phải chờ những thứ ko cần

---