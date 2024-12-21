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
- 



---