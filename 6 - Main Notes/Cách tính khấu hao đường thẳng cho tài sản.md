2024-11-01 21:35

Tags: [[Finance]] [[Accounting]]

---

## Các định nghĩa
- Tổng giá trị tài sản (**Total Asset Value**): tổng tất cả các chi phí phải bỏ ra cho tài sản
- Ngày bắt đầu tính khấu hao (**Depreciation Start Date**): thường là ngày tài sản bắt đầu được đưa vào sử dụng
- Kỳ khấu hao (**Depreciation Period Length**): sau mỗi bao lâu thì gía trị tài sản sẽ giảm 1 lần (thường theo tháng)
- Số kỳ khấu hao (**Total Depreciation Periods**): sau bao nhiêu kỳ khấu hao thì tài sản hết giá trị
## Tính khấu hao đường thẳng
- Trước tiên phải tính khấu khao trung bình mỗi kỳ (Depreciation Amount):
```python
depreciation_amount = total_asset_value / total_depreciation_periods
```
- Ta chia các lần khấu hao thành 3 nhóm:
	- Lần khấu hao đầu tiên (First Depreciation)
	- Lần khấu hao cuối cùng (Last Depreciation)
	- Các lần khấu hao còn lại -> Chính là **depreciation_amount**
### Tính lần khấu hao đầu tiên
- Lần khấu hao đầu tiên phụ thuộc vào việc ngày tài sản được đưa vào sử dụng có gần với ngày bắt đầu 1 chu kỳ mới không, càng gần thì giá trị khấu hao lần đầu càng ít, cụ thể
```python
first_depreciation = (days_until_next_period / total_days_in_one_period) / depreciation_amount
```

> [!warning] Lưu ý
> day_until_next_period phải tính cả ngày bắt đầu. Ví dụ ngày bắt đầu là 29/1 -> còn 3 ngày nữa là sang period tiếp theo
> 

### Tính lần khấu hao cuối cùng
- Lần khấu hao cuối cùng sẽ bằng giá trị khấu hao trung bình trừ đi lần khấu hao đầu tiên

---
# References