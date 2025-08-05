# Basic Pandas

## **Pandas: Người bạn đồng hành không thể thiếu của Data Analyst**

Trong thế giới phân tích dữ liệu, thư viện **Pandas** của Python nổi lên như một trợ thủ đắc lực, giúp các Data Analyst "chinh phục" những bộ dữ liệu phức tạp. Vậy, Pandas mang đến những "siêu năng lực" gì?

### 1. Đọc và Ghi Dữ Liệu (Data Import/Export) 📖

Đây là bước đầu tiên trong mọi quy trình phân tích. Pandas giúp nhà phân tích dễ dàng đọc dữ liệu từ nhiều định dạng file khác nhau và ghi kết quả ra file mới.

- **Đọc dữ liệu:** Dễ dàng nhập dữ liệu từ các nguồn như CSV, Excel, JSON, SQL databases, HTML, và nhiều định dạng khác.
- **Ghi dữ liệu:** Xuất `DataFrame` đã qua xử lý ra các định dạng file tương ứng để lưu trữ hoặc chia sẻ.

### 2. Làm Sạch Dữ Liệu (Data Cleaning) 🧹

Dữ liệu trong thực tế hiếm khi hoàn hảo. Pandas cung cấp một bộ công cụ mạnh mẽ để xử lý các vấn đề phổ biến.

- **Xử lý giá trị thiếu (Missing Values):** Dễ dàng tìm, loại bỏ hoặc thay thế các giá trị rỗng (`NaN`).
- **Chuẩn hóa kiểu dữ liệu:** Chuyển đổi các cột về đúng định dạng (ví dụ: từ text sang số hoặc ngày tháng).
- **Loại bỏ dữ liệu trùng lặp:** Tìm và xóa các hàng dữ liệu bị lặp lại.
- **Sửa lỗi dữ liệu:** Sử dụng các phương thức để sửa các giá trị không nhất quán hoặc sai định dạng.

### 3. Thao Tác và Chuyển Đổi Dữ Liệu (Data Manipulation & Transformation) 🔧

Đây là lúc nhà phân tích định hình lại dữ liệu để phù hợp với mục tiêu phân tích.

- **Lọc và lựa chọn:** Chọn các hàng và cột cụ thể dựa trên các điều kiện logic.
- **Thêm/Xóa cột:** Tạo các cột mới hoặc xóa các cột không cần thiết.
- **Sắp xếp dữ liệu:** Sắp xếp theo một hoặc nhiều cột.
- **Gộp và nối:** Kết hợp nhiều bộ dữ liệu lại với nhau (`merge`, `join`, `concat`).
- **Thay đổi cấu trúc:** Chuyển dữ liệu giữa dạng "dài" và "rộng" (`pivot_table`, `melt`).

### 4. Phân Tích và Thống Kê (Data Analysis & Aggregation) 📊

Sau khi dữ liệu đã sạch và định hình, Pandas giúp thực hiện các phân tích thống kê cơ bản.

- **Thống kê mô tả:** Trung bình, trung vị, độ lệch chuẩn, min, max,...
- **Phân nhóm và tổng hợp:** Tương tự `GROUP BY` trong SQL.
- **Phân tích chuỗi thời gian:** Làm việc với dữ liệu thời gian, resample, rolling,...

---

## Pandas Data Structures

### 1. Series 🐼

**`Series`** giống như **một cột duy nhất** trong Excel.

| Chỉ số (Index) | Name |
| --- | --- |
| 0 | A |
| 1 | B |
| 2 | C |

### 2. DataFrame 🐼🐼

**`DataFrame`** giống như **toàn bộ bảng tính** Excel.

| Chỉ số (Index) | Tên | Tuổi | Thành phố |
| --- | --- | --- | --- |
| 0 | An | 25 | Hà Nội |
| 1 | Bình | 30 | Đà Nẵng |
| 2 | Cường | 22 | TP.HCM |

Sử dụng `pd.concat(series_1, series_2)` để tạo `DataFrame` mới.

---

## Example: Thao tác pandas với dữ liệu dạng tabular

```python
import pandas as pd
DATASET_PATH = '/content/Pokemon.csv'
df = pd.read_csv(DATASET_PATH)

# 1. Đọc dữ liệu đứng đầu
data.head()

# 2. Đọc dữ liệu đứng cuối
data.tail(5)

# 3. Lấy tên cột (headers)
print(data.columns)

# 4. Đọc một cột cụ thể
print(data[['Name']].head())
print(data[['Name', 'Total', 'Attack']][:10:2])

# 5. Đọc một hàng cụ thể
data.iloc[[3]]
data.iloc[[3,6]]
data.iloc[3:5]
data.loc[data['Legendary'] == True].head(2)

# 6. Đọc giá trị trong một hàng
data.iloc[3,4]
data.loc[data['Attack'] == 49, ['Name']]

# 7. Thống kê dữ liệu
data.describe()

# 8. Sắp xếp dữ liệu
data.sort_values('Type 1').head(3)
data.sort_values('Type 1', ascending=False).head(3)
data.sort_values(['Type 1', 'HP'], ascending=[1, 0]).head(3)

# 9. Thay đổi bảng dữ liệu
data = data.drop(columns=['Total'])
data['Total'] = data['Attack'] + data['Defense'] + data['HP']

# 10. Sắp xếp lại thứ tự cột
cols = list(data.columns.values)
data[cols[0:4] + [cols[-1]] + cols[4:-1]].head(3)

# 11. Lưu bảng dữ liệu
data.to_csv('modified.csv')
data.to_excel('modified.xlsx', index=False)
data.to_csv('modified_tab.csv', sep='\t')

# 12. Filtering với điều kiện
data.loc[(data['Type 1']()]()
