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
- PrimaryDB: để lưu và write các nội dung bài viết
- Secondary DB: chỉ để read
- Object Storage: để lưu ảnh
- 
---