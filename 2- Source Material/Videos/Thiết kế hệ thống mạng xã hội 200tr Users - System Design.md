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
- TÌm cách giảm số lần phải đọc và ghi, bằng cách <mark style="background: #BBFABBA6;">phân loại người dùng</mark>
	- Online
	- Active: online trang 3 ngày
	- Inactive: chưa online trong >3 ngày 
	- Blocked: User đã bị khóa tài khảon
- Post processor <mark style="background: #BBFABBA6;">chỉ tìm + cập nhật home cho user online</mark>
- Vấn đề phát sinh: user active/inactive khi online lại không thấy bài viết mới -> <mark style="background: #FFB8EBA6;">không đáp ứng</mark> <mark style="background: #FFB8EBA6;">được nhất quán dữ liệu</mark>
# Giải pháp
- Update timeline service -> query secondary db -> lấy các post mới của user mà user đó theo dõi
- 

---