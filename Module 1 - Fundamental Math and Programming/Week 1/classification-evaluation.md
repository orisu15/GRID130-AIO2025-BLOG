# 📊 Các độ đo thường được sử dụng để đánh giá bài toán phân loại

Trong học máy, khi xây dựng một mô hình phân loại, bạn không chỉ dừng lại ở việc huấn luyện xong mô hình rồi đánh giá bằng accuracy (độ chính xác). Bạn có tin rằng trên thực tế, có những bài toán mà accuracy cao nhưng mô hình lại hoạt động kém không?

---

## 🎯 Accuracy không phải là hoàn hảo

Trước hết, ta sẽ cùng tìm hiểu độ đo accuracy là gì nhé! Công thức của độ đo accuracy được định nghĩa như sau:

> Độ đo Accuracy được tính bằng cách lấy tỉ lệ số chẩn đoán đúng và tổng số chẩn đoán

Với công thức cụ thể như sau:

$$\text{accuracy} = \frac{\text{Số lượng chẩn đoán đúng}}{\text{Tổng số lượng chẩn đoán}}$$

Trong trường hợp bình thường, có thể accuracy sẽ là một độ đo tổng quát và phù hợp, nhưng hãy cùng mình xem thử trường hợp sau:

Giả sử bạn đang xây dựng một mô hình phát hiện bệnh hiếm gặp. Trong 1.000 người, chỉ có 10 người mắc bệnh. Nếu mô hình đoán tất cả đều "không bệnh", bạn vẫn đạt được accuracy = 99% — nhưng bạn đã bỏ lỡ toàn bộ 10 người cần phát hiện.

Vậy về cơ bản, với tỉ lệ accuracy lên tới 99% nhưng mô hình này sẽ không có tác dụng thực tiễn nào. Đây chính là lúc các độ đo precision, recall và f1-score trở nên hữu dụng

---

## 🔍 Confusion Matrix
 
Trước khi đi vào các độ đo, bạn cần hiểu Confusion Matrix — một bảng thể hiện 4 loại kết quả mà mô hình phân loại có thể đưa ra:

|                       | Dự đoán: Positive         | Dự đoán: Negative      |
| --------------------- | ------------------------- | ---------------------- |
| **Thực tế: Positive** | TP (True Positive)        | FN (False Negative)    |
| **Thực tế: Negative** | FP (False Positive)       | TN (True Negative)     |

- TP: Dự đoán là Positive, thực tế là Positive, dự đoán đúng
- FP: Dự đoán là Positive, thực tế là Negative, dự đoán sai
- FN: Dự đoán là Negative, thực tế là Positive, dự đoán sai
- TN: Dự đoán là Negative, thực tế là Negative, dự đoán đúng

---

## 🎯 Precision

Precision đo lường trong số những trường hợp mà mô hình dự đoán là Positive, thì có bao nhiêu phần trăm là đúng.

**Công thức:**

$$\text{precision} = \frac{\text{TP}}{\text{TP} + \text{FP}}$$

**Ý nghĩa:**

Bạn có thể hiểu Precision là trả lời cho câu hỏi: “Trong các mẫu mà tôi bảo là ‘có bệnh’, tôi đúng bao nhiêu phần trăm?”

**Khi nào nên ưu tiên Precision?**

- Khi FP là điều cần tránh (dự đoán sai là dương có hậu quả nghiêm trọng).

- Ví dụ: Hệ thống phát hiện thư rác - Bạn không muốn loại bỏ nhầm các thư bình thường nhưng lại bị mô hình coi là thư rác.

---

## 🔎 Recall – Độ bao phủ

Recall đo lường trong số những mẫu thực sự là Positive, mô hình phát hiện được bao nhiêu phần trăm.

**Công thức:**

$$\text{recall} = \frac{\text{TP}}{\text{TP} + \text{FN}}$$

**Ý nghĩa:**

Recall trả lời cho câu hỏi: “Trong tất cả người bị bệnh, tôi phát hiện được bao nhiêu?”

**Khi nào nên ưu tiên Recall?**

- Khi FN là điều cần tránh (bỏ sót trường hợp dương là nguy hiểm).

- Ví dụ: Phát hiện bệnh nhân ung thư – bỏ sót một người có thể để lại hậu quả nghiêm trọng.

---

## ⚖️ F1-score – Sự cân bằng giữa Precision và Recall
Khi Precision và Recall kéo nhau theo hai hướng đối lập, F1-score là cách để cân bằng cả hai. Đây là trung bình điều hòa (harmonic mean) giữa Precision và Recall:

**Công thức:**

$$\text{f1-score} = \frac{2 * (\text{precision} * \text{recall})}{\text{precision} + \text{recall}}$$

**Khi nào dùng F1-score?**

- Khi bạn cần cân bằng giữa Precision và Recall.

- Phù hợp với các bài toán mất cân bằng dữ liệu (imbalanced classes).

---

## Code triển khai

**Code**

```python
def evaluate_f1_components(tp, fp, fn):
    """
    Tính điểm F1 Score từ các giá trị:
    - tp: Số lượng true positives
    - fp: Số lượng false positives
    - fn: Số lượng false negatives

    Công thức:
        precision = tp / (tp + fp)
        recall = tp / (tp + fn)
        f1_score = 2 * (precision * recall) / (precision + recall)

    Trả về:
        f1_score: Điểm F1 Score dưới dạng float
    """

    # Kiểm tra kiểu dữ liệu
    if not isinstance(tp, int):
        print('tp must be int')
        return None

    if not isinstance(fp, int):
        print('fp must be int')
        return None

    if not isinstance(fn, int):
        print('fn must be int')
        return None

    # Kiểm tra giá trị không âm
    if tp < 0 or fp < 0 or fn < 0:
        print('tp, fp, and fn must be non-negative integers')
        return None

    # Tính precision và recall với xử lý chia cho 0
    precision = tp / (tp + fp) if (tp + fp) > 0 else 0.0
    recall = tp / (tp + fn) if (tp + fn) > 0 else 0.0

    # Tính F1 Score
    f1_score = 2*(precision*recall)/(
        precision+recall) if (precision+recall) > 0 else 0.0

    return precision, recall, f1_score

precision, recall, f1_score = evaluate_f1_components(tp=2, fp=3, fn=5)
print(precision, recall, f1_score)
```

**Kết quả:**

```
0.4 0.2857142857142857 0.3333333333333333
```
