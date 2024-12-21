Source link: https://www.youtube.com/watch?v=4I103R4uiP0

Status: #source-eating 

---

# Gitlab
- Search "Scale Gitlab DB"
- Ban đâu: chior có 1 postgresSQL db server + 1 single replica for recovery
- Vấn đề 1: Viết query tệ -> chậm
> [!info] Chiến lược tối ưu 1: Tối ưu code để cải thiện hiệu suất (Tốt nhất là xem chiến lược thực thi)

> [!info] CHiến lược tối ưu 2: sử dụng connection pool -> quản lý và giảm số lượng kết nối

![[Cách thức mở rộng DB 2024-12-21 10.11.22.excalidraw]]

> [!info] Cân bằng tải giữa nhiều máy chủ
- Chia tải ra các DB read-only
![[Cách thức mở rộng DB 2024-12-21 10.20.27.excalidraw]]


> [!info] Phân mảnh (Shard) cơ sở dữ liệu 
- Sharding phù hợp trong trường hợp write-heavy
# Stackoverflow
- No need microservices
- Tăng ram
# Notion
- Center of Notion's data model is blocks -> It has billions of blocks
- Issue when using Postgres:
	- Postgres cho mỗi transaction sử dụng 1 token
	- Có thể sử dụng token xoay vòng
	- Chỉ hỗ trợ 2 tỉ transaction -> nếu hết 2 tỉ transaction mà transaction 1 chưa xong -> lỗi
- GIải pháp: có 1 "Vaccum" đánh dấu token có được ghi đè không -> vẫn có case người dọn dẹp chưa kịp xử lý đến
- Sự khác biệt trong việc chỉnh sửa records trong postgres: Postgres sẽ tạp thêm 1 bản ghi với giá trị mới -> Bỏ bản ghi cũ (công việc  của vacuum) --> User notion update rất nhiều -> vacuum hoatk động nhiều -> ảnh hưởng hiệu năng
> [!info] Xem thêm chơ chế MVCC
- Notion phải sharding do write nhiều
- Khi nhiều user hơn -> Vẫn quá tải connection pool
	- Tăng số physical DB
	- CDC
# Tổng kết
- Bắt đầu 1 cách đơn giản chỉ với 1 DB + 1 backup, tập trung ==tối ưu SQL query + tham số==
- ==Mở rộng read==: mở rộng các DB dự phòng, chi tải phần read sang
- ==Mở động write==: Sharding thành các DB nhỏ hơn
- ==Chi theo nghiệp vụ==: ví dụ tách phần thao tác user với phần phân tích, và có 1 bên ở giữa để đồng bộ data

> [!info] Có thể kết hợp các loại này



---