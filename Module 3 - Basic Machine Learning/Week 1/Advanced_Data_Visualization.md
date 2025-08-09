# Advanced_Data_Visualization: Cách Chọn Và Trực Quan Hóa Biểu Đồ Phù Hợp Sử Dụng Python

## Giới Thiệu
Trực quan dữ liệu là quá trình chuyển đổi thông tin thành các dạng trực quan như đồ thị hoặc biểu đồ, giúp bộ não con người dễ dàng hiểu và rút ra những thông tin quan trọng. Bằng cách sử dụng biểu đồ, nó giúp đơn giản hóa các dữ liệu phức tạp và dễ dàng nhận diện các mô hình và xu hướng.

---

## 1. Trực Quan Dữ Liệu Cơ Bản

### 1. Nghiên Cứu Tình Huống: Hiệu Suất Học Sinh
Trong nghiên cứu tình huống này, chúng ta sẽ khám phá các loại biểu đồ có thể được sử dụng để trực quan hóa hiệu suất của học sinh qua các hạng mục khác nhau:

- **Giới thiệu các biểu đồ thông dụng**:
  - **Biểu đồ cột**: Hữu ích để so sánh các danh mục hoặc biến.
  - **Biểu đồ đếm**: Hiển thị số lần xuất hiện của mỗi danh mục.

### 2. Nghiên Cứu Tình Huống: Bộ Dữ Liệu Iris
Bộ dữ liệu Iris thường được sử dụng trong phân tích và trực quan hóa dữ liệu để minh họa các loại biểu đồ khác nhau:

- **Các biểu đồ được đề cập**:
  - **Biểu đồ tần suất (Histogram)**: Hiển thị sự phân bố tần suất của một biến đơn lẻ.
  - **Biểu đồ phân tán, Biểu đồ bong bóng, Biểu đồ KDE (Kernel Density Estimate)**: Hiển thị mối quan hệ giữa các biến.
  - **Biểu đồ DisPlot**: Biến thể của biểu đồ tần suất với các tính năng bổ sung.
  - **Trực quan hóa 3D**: Đại diện các điểm dữ liệu trong không gian ba chiều cho phân tích đa biến.

### 3. Cách Chọn Biểu Đồ Phù Hợp

#### Hướng dẫn từng bước để chọn biểu đồ phù hợp:

- **Bước 1**: Xác định **Loại Dữ Liệu**:
  - Dữ liệu số (số liệu định lượng)
  - Dữ liệu phân loại (dữ liệu định tính)
  - Dữ liệu theo thời gian (dữ liệu theo thời gian)
  - Dữ liệu không gian (dữ liệu theo vị trí)

- **Bước 2**: Xác định **Mối Quan Hệ Giữa Các Biến**:
  - **So sánh**: Sử dụng biểu đồ cột hoặc biểu đồ thanh.
  - **Phân bố**: Sử dụng biểu đồ tần suất hoặc biểu đồ hộp.
  - **Mối quan hệ**: Sử dụng biểu đồ phân tán hoặc biểu đồ bong bóng.

- **Bước 3**: Xác định **Mục Đích Trực Quan**:
  - Hiển thị xu hướng theo thời gian? Sử dụng biểu đồ đường hoặc biểu đồ diện tích.
  - So sánh các điểm dữ liệu? Sử dụng biểu đồ cột hoặc thanh.
  - Hiển thị sự phân bố dữ liệu? Sử dụng biểu đồ tần suất hoặc hộp.
  - Hiển thị mối quan hệ giữa các biến? Sử dụng biểu đồ phân tán hoặc bong bóng.

- **Bước 4**: **Xác Định Đối Tượng Khán Giả**:
  - Đối tượng chuyên môn: Các biểu đồ phức tạp như heatmap.
  - Đối tượng không chuyên: Các biểu đồ đơn giản như biểu đồ tròn hoặc thanh.

- **Bước 5**: **Chọn Loại Biểu Đồ Phù Hợp**:
  - Hãy thử nghiệm với nhiều loại biểu đồ nếu cần thiết để tìm ra biểu đồ hiệu quả nhất cho dữ liệu của bạn.

---

## 2. Nghiên Cứu Tình Huống: Bộ Dữ Liệu ETTH

### 1. Biểu Đồ Cột, Tròn Và Thanh
Những biểu đồ này giúp phân tích xu hướng theo thời gian và phân phối các danh mục:

- **Biểu đồ đường**: Đại diện cho dữ liệu liên tục theo thời gian.
- **Biểu đồ tròn**: Hiển thị tỷ lệ đại diện của các danh mục.
- **Biểu đồ thanh**: So sánh các danh mục khác nhau hoặc các khoảng thời gian.

### 2. Biểu Đồ Hộp
Biểu đồ hộp giúp nhận diện các điểm ngoại lai và trực quan hóa sự phân bố dữ liệu theo các phân vị.

---

## Thư Viện Python Cho Trực Quan Dữ Liệu

- **Matplotlib**: Cung cấp khả năng tùy chỉnh mạnh mẽ nhưng yêu cầu nhiều mã hơn để thực hiện các biểu đồ phức tạp.
- **Seaborn**: Giúp đơn giản hóa các biểu đồ thống kê với các chủ đề tích hợp sẵn, dễ sử dụng hơn Matplotlib.
- **Plotly**: Tập trung vào các biểu đồ động và tương tác, cho phép người dùng tạo các biểu đồ đẹp mắt cho ứng dụng web.

---

## Trực Quan Dữ Liệu Với Python

Khi tạo các trực quan dữ liệu, bạn cần xem xét:
- Những gì bạn muốn thể hiện: So sánh, mối quan hệ, phân bố, hay thành phần.
- Loại dữ liệu bạn có: Dữ liệu số, phân loại, thời gian, hay không gian.

Ví dụ, khi sử dụng **Bộ Dữ Liệu Máy Biến Áp ETTH**, bạn có thể muốn:
- Trực quan hóa sự thay đổi theo thời gian của nhiệt độ (biểu đồ đường).
- Hiển thị phân phối của công suất (biểu đồ tần suất).
- So sánh các điểm dữ liệu khác nhau (biểu đồ cột).

### Mã Python Ví Dụ Cho Bộ Dữ Liệu ETTH:
```python
import plotly.express as px
import pandas as pd

df = pd.read_csv("/content/ETTh.csv", parse_dates=['date'])
fig = px.line(df, x="date", y="OT", title="Nhiệt Độ Dầu Theo Thời Gian")
fig.show()
```

---

## 3. Nghiên Cứu Tình Huống: Phân Tích Các Chuyến Đi Uber

### Giới Thiệu Bộ Dữ Liệu:
Bộ dữ liệu chứa thông tin về 4,5 triệu chuyến đi Uber tại Thành Phố New York từ tháng 4 đến tháng 9 năm 2014 và 14,3 triệu chuyến từ tháng 1 đến tháng 6 năm 2015.

Những thông tin chính:
- **Ngày thứ Hai** là ngày Uber có doanh thu cao nhất.
- Vào **thứ Bảy**, ít người sử dụng Uber.
- **6 giờ chiều** là giờ cao điểm.
- Các chuyến đi bắt đầu tăng vào khoảng **5 giờ sáng**.

---

## 4. Kết Luận

### Những Điểm Chính:
- Luôn lựa chọn loại biểu đồ phù hợp với loại dữ liệu và thông tin bạn muốn truyền đạt.
- Sử dụng **biểu đồ đường** cho các xu hướng theo thời gian, **biểu đồ cột** cho so sánh, **biểu đồ tần suất** cho phân bố, và **biểu đồ phân tán** cho mối quan hệ.
- Chọn biểu đồ phù hợp nhất với dữ liệu và nhu cầu của đối tượng người xem.