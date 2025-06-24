# Thứ 2

Check: No

# OOP - Classes and Objects

## OOP: Object-Oriented Programming

- **OOP (Object-Oriented Programming)** là một phương pháp lập trình tập trung vào việc tạo ra các "đối tượng" (objects) để đại diện cho các thực thể trong thế giới thực hoặc các khái niệm trừu tượng. Các đối tượng này sẽ có **thuộc tính** (dữ liệu) và **hành vi** (các hàm/phương thức).
    - **Class (Lớp):** Là **khuôn mẫu, bản thiết kế** chung. Nó định nghĩa những đặc điểm (thuộc tính) và những việc có thể làm (hành vi) cho một loại đối tượng nào đó.
    - **Constructor** : `__init__()`: là một hàm **Tự động được gọi:** Mỗi khi bạn "tạo mới" một đối tượng (Object) từ một Class. **Khởi tạo (initialize) các thuộc tính:** Dùng để gán các giá trị ban đầu cho các `attributes` (thuộc tính) của đối tượng vừa được tạo.
    - **Object (Đối tượng):** Là **sản phẩm cụ thể, một thể hiện** được tạo ra từ Class. Mỗi object sẽ có các thuộc tính riêng (ví dụ: ngôi nhà số 1 có màu sơn xanh, ngôi nhà số 2 có màu sơn đỏ) nhưng vẫn tuân theo khuôn mẫu của Class.
    - **Class `ConMeo`**: Bản thiết kế cho tất cả các con mèo.
        - **Thuộc tính:** `mauLong`, `canNang`, `soChan`.
        - **Hành vi:** `keu()`, `chay()`, `ngu()`.
    - **Object `MeoTamThe`**: Một đối tượng cụ thể được tạo từ Class `ConMeo` bao gồm các **attributes** và **methods**.
        - **Thuộc tính (attributes) : là những đặc điểm, thông tin của object**
            - `mauLong = "tam the"`, `canNang = 4kg`, `soChan = 4`.
        - **Hành vi (methods) : những hành động mà object có thể thực hiện**
            - `MeoTamThe.keu()` (sẽ phát ra tiếng "meo meo").

## Cấu trúc cơ bản của một class :

> **Class → Constructor → Objects → attributes → methods**

![image.jpg](image.jpg)

```python
class Rectangle:
    def __init__(self, my_width, my_height):
        self.width = my_width
        self.height = my_height

    def calculate_area(self):
        self.area = self.width * self.height
        return self.area

    def calculate_perimeter(self):
        return (self.width + self.height) * 2

my_rec = Rectangle(4, 7)
Phương thức __call__ trong Python
```

Khi bạn định nghĩa phương thức __call__ trong một lớp, và sau đó tạo một đối tượng từ lớp đó, bạn có thể "gọi" đối tượng đó bằng cách sử dụng dấu ngoặc đơn () như thể nó là một hàm. Khi bạn làm như vậy, Python sẽ tự động gọi phương thức __call__ của đối tượng đó.
class MyClass:
    def __init__(self, value):
        self.value = value
        print("Đối tượng được tạo.")

    def __call__(self, *args, **kwargs):
        print(f"Đối tượng đã được gọi! Giá trị của đối tượng: {self.value}")
        print(f"Các đối số truyền vào: {args}")
        print(f"Các đối số từ khóa truyền vào: {kwargs}")
        # Bạn có thể thêm logic xử lý tại đây
        return "Kết quả từ __call__"

# Tạo một đối tượng từ lớp MyClass
my_object = MyClass(10)

# Gọi đối tượng như một hàm
result = my_object(1, 2, name="Alice")

print(result)
