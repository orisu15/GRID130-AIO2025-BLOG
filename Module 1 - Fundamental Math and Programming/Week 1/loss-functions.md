# 🎯 Giới thiệu 3 hàm mất mát trong bài toán hồi quy: MAE, MSE và RMSE

Khi bạn xây dựng một mô hình học máy để **dự đoán số liên tục** – ví dụ như giá nhà, nhiệt độ, điểm số – bạn đang làm việc với **bài toán hồi quy** (regression). Nhưng làm sao để biết mô hình của bạn đang dự đoán tốt đến đâu?

Đó là lúc **hàm mất mát (loss function)** phát huy tác dụng. Bài viết này sẽ giúp bạn hiểu 3 hàm mất mát phổ biến nhất trong hồi quy: **MAE**, **MSE**, và **RMSE**.

---

## 1. ❓ Loss function là gì?

**Loss function** là cách chúng ta đo “độ sai” giữa giá trị mô hình dự đoán và giá trị thực tế. Nó giống như thước đo để huấn luyện mô hình: càng sai nhiều, loss càng lớn, và mô hình sẽ cần điều chỉnh để sai ít hơn trong lần huấn luyện tiếp theo.

### Ví dụ đơn giản:

* Thực tế: Giá nhà là 1 tỷ
* Mô hình dự đoán: 950 triệu → sai 50 triệu

Chúng ta muốn một con số nào đó phản ánh mức sai lệch này để tối ưu mô hình. Đó chính là vai trò của loss function.

---

## 2. 📏 MAE – Mean Absolute Error (Sai số tuyệt đối trung bình)

### ✅ Công thức:

$$
MAE = \frac{1}{n} \sum_{i=1}^{n} |y_i - \hat{y}_i|
$$

Trong đó:

* $y_i$: giá trị thực tế
* $\hat{y}_i$: giá trị dự đoán

### ✅ Ý nghĩa:

MAE đo lường trung bình khoảng cách tuyệt đối giữa dự đoán và thực tế. Nói cách khác, mỗi lần dự đoán sai bao nhiêu, lấy tuyệt đối và tính trung bình.

### ✅ Ưu điểm:

* Dễ hiểu
* Không bị ảnh hưởng mạnh bởi các sai số quá lớn (outliers)

### ❌ Nhược điểm:

* Không phân biệt giữa sai số lớn và nhỏ: giả sử ta có tổng 10 sai số nhỏ mới tương đương 1 sai số lớn → vẫn tính như nhau

### 📌 Khi nào dùng MAE?

* Khi bạn muốn mô hình công bằng và không bị chi phối bởi vài điểm sai nghiêm trọng
* Phù hợp khi dữ liệu có nhiễu hoặc outliers

---

## 3. 🧮 MSE – Mean Squared Error (Sai số bình phương trung bình)

### ✅ Công thức:

$$
MSE = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2
$$

### ✅ Ý nghĩa:

MSE cũng đo sai số trung bình, nhưng bình phương sai số trước khi tính trung bình. Điều này khiến các sai số lớn bị phóng đại, nên mô hình sẽ chú ý nhiều hơn đến các lỗi nghiêm trọng.

### ✅ Ưu điểm:

* Phạt nặng hơn đối với các sai số lớn → giúp mô hình cải thiện những dự đoán với sai số lớn
* Dễ tính toán và khả vi (dễ áp dụng cho gradient descent)

### ❌ Nhược điểm:

* Rất nhạy với outliers
* Đơn vị đo bị thay đổi (vd: dự đoán nhiệt độ với đơn vị là độ C, nó sẽ thành độ C bình phương ???)

### 📌 Khi nào dùng MSE?

* Khi bạn muốn mô hình tránh sai số lớn
* Khi bạn không ngại mất tính trực quan (do thay đổi đơn vị)

---

## 4. 🧮 RMSE – Root Mean Squared Error (Căn bậc hai của MSE)

### ✅ Công thức:

$$
RMSE = \sqrt{MSE} = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2}
$$

### ✅ Ý nghĩa:

RMSE là khá tương đồng của MSE nhưng đã lấy căn bậc hai để trả lại đơn vị gốc của dữ liệu. Điều này giúp kết quả dễ hiểu hơn khi so sánh với dữ liệu thật.

### ✅ Ưu điểm:

* Dễ diễn giải (cùng đơn vị với output gốc)
* Vẫn giữ được đặc tính nhấn mạnh vào sai số lớn như MSE

### ❌ Nhược điểm:

* Vẫn bị ảnh hưởng bởi outliers

### 📌 Khi nào dùng RMSE?

* Khi bạn muốn mô hình tránh sai số lớn nhưng vẫn cần kết quả có ý nghĩa thực tế (ví dụ: sai số trung bình là 10 độ C thay vì 10 độ C bình phương)
