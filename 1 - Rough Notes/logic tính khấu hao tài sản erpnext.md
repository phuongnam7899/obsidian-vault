- Validate các thông tin về **finance book** (Finance book là child của Asset)
- Tính **giá trị sau khi khấu hao** tính đến thời điểm hiện tại (**value_after_depreciation**) -> Update vào finance book row
- Tính số lần khấu hao còn lại (final_number_of_depreciations)
	- Tổng số lần khauashao - số lần khấu hao đã ghi nhận
	- nếu là pro_data => số lần khấu hao +1 (là pro_data: depreciation_amount cho kỳ đầu và kỳ cuối sẽ khác nhau, trong trường hợp asset được sử dụng từ giữa tháng)

## Cách tính giá trị khấu hao tháng đầu tiên