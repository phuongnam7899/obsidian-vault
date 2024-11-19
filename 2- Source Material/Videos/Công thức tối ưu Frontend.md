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
- Là những resouce mà khiến browser phải dừng lại để tải hoàn tất thì mới có thể đi tới bước tiếp theo
- 2 loại:
	- **Render blocking**: tài nguyên block việc render của browser (tức là ==ngăn từ bước 2 sang bước 3== trong CRP)
	- Parser blocking: tài nguyên ngăn chạn việc parseHTML (tức là ngăn cảm HTML -> DOM trong bước 2)
		- Ví dụ (thẻ script nằm giữa html)

## Kỹ thuật
## Công cụ
## Demo

---