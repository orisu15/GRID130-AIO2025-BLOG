# Coding Methodology

## Phần 1: Clean code và tiêu chuẩn PEP-8:

### 1.1 Clean code: "Code không chỉ để máy hiểu – mà còn để con người đọc!”

- **Clean code** là mã nguồn **rõ ràng, dễ đọc, dễ bảo trì, có khả năng mở rộng và dễ dàng kiểm thử.** Code được viết theo cách mà người khác (đồng nghiệp) hoặc chính bạn trong tương lai có thể dễ dàng hiểu, cải tiến hoặc bảo trì
    - **4 mục tiêu chính cần đạt được:**
        
        
        | Readable | Dễ đọc và dễ hiểu  |
        | --- | --- |
        | Maintainable | Dễ bảo trì,  sửa đổi, mở rộng và tái sử dụng mà không gây ra lỗi phụ |
        | Testable | Thiết kế dễ dàng, uni test và kiểm thử tự động |
        | Extensible | Có khả năng mở rộng , thêm tính năng mới mà không cần thay đổi code hiện tại |
- **🗣️ “Code sạch không chỉ là việc máy chạy được – mà là khi đồng đội đọc không muốn... nghỉ việc!”**
    - **Đặt tên biến, formating:** **s**ử dụng **tên biến/hàm có ý nghĩa**, thêm tài liệu mô tả và tuân thủ các quy ước định dạng để tăng
    khả năng đọc hiểu.
    
    **Đặt tên biến có ý nghĩa**
    
    **Viết code có formatting**
    
    ```jsx
    # Bad example – unclear variable names
    print("Bad example – unclear variable names:")
    
    a = 5
    b = 10
    c = a + b
    print(f"a + b = {c}")
    
    # Good example – descriptive variable names
    print("\nGood example – descriptive variable names:")
    
    apples = 5
    oranges = 10
    total_fruits = apples + oranges
    
    print(f"Number of apples: {apples}")
    print(f"Number of oranges: {oranges}")
    print(f"Total fruits: {total_fruits}")
    
    ```
    
    ```jsx
    # Bad example – poor formatting
    print("Bad example – poor formatting:")
    
    def add_numbers(x,y,z):
      result=x+y+z
      return result
    
    print(f"add_numbers(1, 2, 3) = {add_numbers(1,2,3)}")
    
    # Good example – proper formatting with spaces
    print("\nGood example – proper formatting with spaces:")
    
    def add_numbers_clean(x, y, z):
        result = x + y + z
        return result
    
    print(f"add_numbers_clean(1, 2, 3) = {add_numbers_clean(1, 2, 3)}")
    
    ```
    
    - **Code dễ mở rộng**:  Thiết kế mở rộng mà không đụng chạm. Thiết kế này sử dụng các hàm riêng biệt và cấu trúc dữ liệu như dictionary để quản lý các phép toán – bí quyết của **Open-Closed Principle.**
    
    ```jsx
    def add(a, b):
        return a + b
    
    def subtract(a, b):
        return a - b
    
    def multiply(a, b):
        return a * b
    
    operations = {
        'add': add,
        'subtract': subtract,
        'multiply': multiply
    }
    
    def calculate(a, b, operation):
        func = operations.get(operation)
        if func:
            return func(a, b)
        else:
            raise ValueError("Invalid operation")
    
    print(f"Results: {calculate(1,2, operation='multiply')}")
    # Results: 2
    
    ```
    

---

- 😎 Khi Nào Bạn *"**Được Phép"* Bỏ Qua Clean Code?**
    - 🧪 **Thử nghiệm nhỏ :** *“Tôi chỉ chạy thử thôi mà!”*
    - ⏱ **Làm prototype thần tốc:** *Ý tưởng còn nóng, code phải gõ liền!*
    - 🚨 **Cháy nhà, vỡ app:** *System sập, khách gào, bug dội... viết nhanh còn hơn viết đẹp.*
    - 👤 **Chỉ mình bạn dùng:** *“Code của tôi, tôi hiểu.”*

## **1.2 PEP-8**: [Tiêu chuẩn định dạng code Python chính thức](https://peps.python.org/pep-0008/)

- [x]  Làm sao cho code dễ đọc, dễ hiểu
- [x]  Làm sao giảm lỗi
- [x]  Cải thiện việc làm việc nhóm
- **Quy Tắc Đặt Tên - Naming Convention :**
    
    
    **Biến/Hàm: snake_case:** chữ thường và dấu gạch dưới để phân tách các từ.
    
    ```jsx
    # Khai báo biến
    my_variable = 10
    
    # Định nghĩa hàm
    def my_function():
        print("Hello")
    
    ```
    
    **Class: PascalCase:** Viết hoa chữ cái đầu của mỗi từ, không có dấu gạch dưới.
    
    ```jsx
    # Đặt tên class
    class MyClass:
        def __init__(self, name):
            self.name = name
    
    ```
    
    **Hằng Số: UPPER_CASE:** Sử dụng tất cả chữ hoa và dấu gạch dưới giữa các từ.
    
    ```jsx
    # Đặt tên hằng số
    PI = 3.14
    MAX_VALUE = 100
    MIN_VALUE = 5
    
    def check_exam_result(score):
        if score >= PASSING_SCORE:
            return "Pass"
        return "Fail"
    
    ```
    
- **Căn lề và khoảng trắng:**
    
    
    | **Thụt lề** | Dùng 4 khoảng trắng cho mỗi cấp thụt lề. Không dùng tab! |
    | --- | --- |
    | **Khoảng trắng trong các biểu thức** | Thêm khoảng trắng hai bên phép toán: a = b + c |
    | **Tránh khoảng trắng thừa** | Sau dấu phẩy: f(a, b) không phải f(a , b) |
    | **Không thêm khoảng trắng trong ngoặc** | Đúng: list([1, 2, 3]) | Sai: list( [1, 2, 3] ) |
- **Ngắt dòng đúng chuẩn:**
    - Dùng dấu gạch chéo (\) để ngắt dòng trực tiếp
    - Ưu tiên dùng ngoặc đơn/vuông/nhọn () [] {} để ngắt dòng ẩn
    - Ngắt tại dấu phẩy hoặc trước toán tử binary (and, or, +, *)
- **Import chuẩn không cần “chỉnh”**:
    
    
    **Thư viện chuẩn**
    
    ```jsx
    import os
    import sys
    import math
    ```
    
    **Thư viện bên thứ ba**
    
    ```jsx
    import numpy as np
    import pandas as pd
    import requests
    ```
    
    **Module nội bộ**
    
    ```jsx
    from myproject.utils import
    parse_data
    from myproject.models import
    User
    ```
    
- **Dòng Trắng và Cấu Trúc Hàm/Class:**
    
    
    | **Giữa các hàm & class** | Cách nhau 2 dòng trắng. 
    Hàm trong class: cách nhau 1 dòng |
    | --- | --- |
    | **Trong thân hàm** | Dùng dòng trắng để tách nhóm logic.
     |
    | **Cấu trúc class** | Thứ tự: docstring → biến class → __ init__() → method thường → private → static. |
    | **Cấu trúc hàm** | Thứ tự:  docstring → kiểm tra input → xử lý → `return` . |
- Công cụ kiểm tra PEP-8 và code cơ bản:
    
    
    | Công cụ | Mô tả | Cài đặt | Sử dụng |
    | --- | --- | --- | --- |
    | **Flake8** | Kiểm tra code: cú pháp, style (PEP-8). Kết hợp pyflakes, pycodestyle và mccabe để phát hiện lỗi logic, độ phức tạp. | pip install flake8 | **flake** your_file.py |
    | **Black** | Format code tự động, chuẩn hóa style, giải quyết tranh chấp để nhất
    quán trong project | pip install black  | **black** your_file.py |
    | **Pylint** | Phân tích tĩnh code: lỗi, chất lượng, điểm số, chỉnh sửa. Phân tích
    sâu hơn Flake8 | pip install pylint  | **pylint** your_file.py |
    | **Mypy** | Kiểm tra kiểu dữ liệu tĩnh dựa trên type annotations để phát hiện lỗi.
    Hỗ trợ kiểm tra các type phức tạp | pip install mypy  | **mypy** your_file.py |

---

## **Phần 2: Viết Code “Pythonic”:**

### 2.1 The Zen of Python (Triết lý Python):

- [**Tập hợp 19 nguyên tắc hướng dẫn thiết kế Python](https://peps.python.org/pep-0020/)**

### 2.2 Pythonic: “đúng chất Python” – ngắn, rõ, đẹp và Zen.

**List Comprehensions**

```jsx
# Let's say we want to create a list of squares (1², 2², 3², etc.)

# Non-Pythonic way (the way you might do it in other languages)
print("Non-Pythonic way:")
squares = []
for i in range(1, 11):  # Numbers 1 to 10
    squares.append(i * i)

print(f"Squares: {squares}")

# Pythonic way using list comprehension
print("\nPythonic way:")
squares_pythonic = [i * i for i in range(1, 11)]
print(f"Squares: {squares_pythonic}")

```

**Dictionary Comprehensions**

```jsx
# Let's create a dictionary mapping numbers to their squares

# Non-Pythonic way
print("Non-Pythonic way:")
square_dict = {}
for i in range(1, 6):
    square_dict[i] = i * i

print(f"Dictionary of squares: {square_dict}")

# Pythonic way
print("\nPythonic way:")
square_dict_pythonic = {i: i * i for i in range(1, 6)}
print(f"Dictionary of squares: {square_dict_pythonic}")

```

<aside>
💡

**Đối với List, Dict và Set dùng comprehension giúp code gọn và nhanh hơn** 

</aside>

```jsx
numbers = [1, 2, 3, 4, 5]
squares = [n**2 for n in numbers]
```

```jsx
numbers = [1, 2, 2, 3, 4, 4]
unique_squares = {n**2 for n in numbers}
# {16, 1, 4, 9}
```

```jsx
names = ['Alice', 'Bob', 'Charlie']
lengths = {name: len(name) for name in names}
```

**Context Managers** `with` :giúp **quản lý tài nguyên tự động** (mở/đóng file, kết nối DB, lock…), đảm bảo **giải phóng đúng cách**, kể cả khi có lỗi xảy ra.

- 🔁 So sánh:
    
    
    | Không Pythonic | Pythonic (dùng `with`) |
    | --- | --- |
    | Phải `file.close()` thủ công | `with` tự động đóng file sau khi dùng |
    | Dễ quên → lỗi memory leak | An toàn, gọn gàng hơn |
    
    ```jsx
    Syntax: 
    with open("file.txt", "r") as file:
        content = file.read()
    ```
    
    <aside>
    💡
    
    ### ✅ Ưu điểm:
    
    - Tránh rò rỉ bộ nhớ (memory leak)
    - Xử lý lỗi tốt hơn
    - Code ngắn gọn, rõ ràng
    - Dùng được cho: file, database, lock, thời gian benchmark...
    </aside>
    
- **Context manager riêng với decorator: @contextmanager** từ module **contextlib** giúp chúng ta dễ dàng tạo context manager chỉ với một
hàm generator đơn giản, thay vì phải định nghĩa class với phương thức **__ enter __** và **__ exit__.**
    
    ```jsx
    # Context manager
    from contextlib import contextmanager
    
    @contextmanager
    def file_reader(filename):
        # Phần setup: mở file (được thực thi trước yield)
        f = open(filename, "r")
        try:
            # Trả về tài nguyên cho khối with
            yield f
        finally:
            # Phần cleanup: luôn đóng file (được thực thi sau khối with)
            f.close()
    
    # Sử dụng context manager tự tạo
    with file_reader("file.txt") as file:
        print(file.read())
    ```
    
    <aside>
    💡
    
    **Ứng dụng thực tế:**
    ✓ Tạm thay đổi cấu hình hệ thống và khôi phục sau khi xong
    ✓ Đo thời gian thực thi một đoạn code
    ✓ Quản lý kết nối database, Redis, hoặc APIs
    ✓ Tạo môi trường tạm thời để test
    
    </aside>
    
- **So Sánh và Điều Kiện - Pythonic Style:**
    - **Trường hợp 1: So sánh với None:**
        - **None** là singleton object, phải dùng **is/is not** để so sánh về mặt **identity**, không phải **equality.**
        • Sử dụng **==** có thể dẫn đến những kết quả không mong muốn
        
        | Tiêu chí | `==` (Equality) | `is` (Identity) |
        | --- | --- | --- |
        | **So sánh gì?** | So sánh **giá trị bên trong** của object | So sánh **có phải cùng một object trong bộ nhớ không** |
        | **Khi nào True?** | Nếu 2 object có **giá trị giống nhau** | Nếu 2 biến **trỏ về cùng một object** |
        | **Ứng dụng phổ biến** | So sánh số, chuỗi, danh sách,... | So sánh với `None`, `True`, `False`, `singleton` |
        | **Có thể bị ghi đè?** | ✅ Có – nếu object có định nghĩa `__eq__()` | ❌ Không – kiểm tra "cùng địa chỉ" nên luôn chính xác |
        | **Ví dụ minh họa** | `a = [1,2,3]; b = [1,2,3]; a == b → ✅ True` | `a is b → ❌ False (vì là 2 list khác nhau)` |
        | **Ví dụ dùng đúng với `None`** | `x is None` (✅ Pythonic) | `x == None` (⚠️ Có thể sai nếu object custom `__eq__`) |
    - **Trường hợp 2: Kiểm tra chuỗi/ list/ dict rỗng:**
        
        
        ❌ Non-Pythonic
        
        ✅ Pythonic
        
        ```jsx
        # Non-Pythonic
        name = "Python"
        if len(name) > 0:  # SAI, không Pythonic!
            print(name)
        
        items = []
        if len(items) == 0:  # SAI, nên dùng: if not items
            print("Empty")
        
        ```
        
        ```jsx
        # Pythonic
        name = "Python"
        if name:  # Tận dụng truthiness
            print(name)
        
        items = []
        if not items:  # Kiểm tra list rỗng
            print("Empty list")
        
        ```
        
- **Properties và dấu underscore _: @property** cho phép **sử dụng method như thuộc tính,** giúp code gọn, dễ kiểm soát truy cập. Tuân
theo quy chuẩn sử dụng dấu **underscore** giúp tránh lỗi khi thiết kế class.
    
    
    **S chữ nhật** với **@property**
    
    ```jsx
    # @property
    class Rectangle:
        def __init__(self, width, height):
            self.width = width
            self.height = height
    
        @property
        def area(self):
            return self.width * self.height
    
    rect = Rectangle(3, 4)
    print(rect.area)  # 12 (không cần rect.area())
    
    ```
    
    **S chữ nhật** với **underscore_**
    
    ```jsx
    # @property
    class Rectangle:
        def __init__(self, width, height):
            self.width = width
            self.height = height
    
        @property
        def area(self):
            return self.width * self.height
    
    rect = Rectangle(3, 4)
    print(rect.area)  # 12 (không cần rect.area())
    
    ```
    
    **4 kiểu sử dụng dấu underscore trong python:**
    
    | Cú pháp | Ý nghĩa chính |
    | --- | --- |
    | `_var` | **Biến private theo quy ước** (nên tránh dùng từ ngoài) |
    | `__var` | **Name mangling** – tránh ghi đè trong kế thừa |
    | `__var__` | **Dùng cho hàm đặc biệt** (dunder method như `__init__`) |
    | `_` | **Biến tạm thời / bỏ qua kết quả** (ví dụ: `_ = func()`) |

---

## **Phần 3: Nguyên lý chung để viết code tốt**

### 3.1 Cá**c nguyên lý như** DRY, YAGNI, KISS,… lập trình phòng thủ và phân chia trách nhiệm giúp viết code **gọn gàng, dễ hiểu và bền vững theo thời gian.**

> **“Không áp dụng nguyên lý thiết kế thì cũng được thôi… miễn là bạn thích sống mãi trong vòng lặp fix-bugs.”**
> 
- **Nguyên tắc DRY (Don't Repeat Yourself):  Tránh lặp lại code**
    
    
    ```jsx
    def print_morning_greeting(name):
        print(f"Good morning, {name}!")
        print("I hope you have a wonderful day.")
        print("Don't forget to drink water and take breaks.")
        print("--------------------------------------------------")
    
    def print_evening_greeting(name):
        print(f"Good evening, {name}!")
        print("I hope you had a wonderful day.")
        print("Don't forget to drink water and take breaks.")
        print("--------------------------------------------------")
    
    ```
    
    ```jsx
    def print_greeting(name, time_of_day):
        print(f"Good {time_of_day}, {name}!")
        print(f"I hope you {'have' if time_of_day == 'morning' else 'had'} a wonderful day.")
        print("Don't forget to drink water and take breaks.")
        print("--------------------------------------------------")
    
    print_greeting("Alice", "morning")
    print_greeting("Bob", "evening")
    
    ```
    
    ❌ Vi phạm nguyên lý **DRY** (Don't Repeat Yourself)
    
    ✅ Tuân thủ nguyên lý **DRY**
    
    **Cách áp dụng:** ✓ Tách các đoạn code lặp lại thành functions, classes, hoặc modules riêng để tái sử dụng trong toàn bộ dự án.
    
- **Nguyên tắc YAGNI (You Aren't Gonna Need It) : không nên thêm chức năng cho đến khi thực sự cần thiết.**
    
    
    | Vi phạm YAGNI  | Tuân thủ YAGNI |
    | --- | --- |
    
    ```jsx
    class SuperCalculator:
        """A calculator with many features we might not need."""
    
        def __init__(self):
            self.history = []
            self.memory = 0
            self.scientific_mode = False
            self.conversion_rates = {
                "USD_to_EUR": 0.85,
                "EUR_to_USD": 1.18,
                "USD_to_GBP": 0.73,
                "GBP_to_USD": 1.37
            }
            # ... and even more conversion rates
    
        def add(self, a, b):
            """Add two numbers."""
            result = a + b
            self.history.append(f"{a} + {b} = {result}")
            return result
    
        def subtract(self, a, b):
            """Subtract b from a."""
            result = a - b
            self.history.append(f"{a} - {b} = {result}")
            return result
    
        def toggle_scientific_mode(self):
            """Toggle scientific mode."""
            self.scientific_mode = not self.scientific_mode
            return self.scientific_mode
    
    ```
    
    ```jsx
    class SimpleCalculator:
        """A calculator that starts with just what we need."""
    
        def add(self, a, b):
            """Add two numbers."""
            return a + b
    
        def subtract(self, a, b):
            """Subtract b from a."""
            return a - b
    
    # We can add more methods later when we actually need them
    
    # Using the simple calculator
    simple_calc = SimpleCalculator()
    result = simple_calc.add(5, 3)
    print(f"5 + 3 = {result}")
    
    ```
    
    **Khi nào nên áp dụng:**
    ✓ Áp dụng khi bạn đang muốn thêm một tính năng
    "phòng khi cần" mà chưa có yêu cầu cụ thể. Hãy trì
    hoãn việc thêm tính năng cho đến khi có nhu cầu thực
    tế.
    
- **Nguyên tắc KISS (Keep It Simple, Stupid) : ưu tiên giải pháp đơn giản và dễ hiểu nhất**
    
    
    | **Quá phức tạp** | **Rõ ràng, đơn giản hơn** |
    | --- | --- |
    
    ```jsx
    def is_even_complex(number):
        """Determine if a number is even using a complex algorithm."""
        
        # Convert to binary string
        binary = bin(number)[2:]  # Remove '0b' prefix
    
        # Check last digit of binary (1 for odd, 0 for even)
        last_digit = binary[-1]
    
        # Convert to integer and check if it's zero
        return int(last_digit) == 0
    
    ```
    
    ```jsx
    def is_even_simple(number):
        """Determine if a number is even using the modulo operator."""
        return number % 2 == 0
    
    ```
    
    **Khi nào nên áp dụng**
    ✓ Python vốn được thiết kế theo triết lý "Đơn giản hơn
    tốt hơn phức tạp" - tận dụng điều này để viết code rõ
    ràng, ngắn gọn.
    
- **Defensive Programming (Lập trình phòng thủ): luôn giả định rằng sẽ có lỗi xảy ra.**
    
    
    | Thiếu kiểm tra đầu vào | Kiểm tra rõ ràng |
    | --- | --- |
    
    ```jsx
    	# Non-defensive programming
    def divide(a, b):
        return a / b
    
    print(divide(5, 0))  # lỗi ZeroDivisionError
    
    def get_element(lst, index):
        return lst[index]  # Lỗi nếu index ngoài range
    
    ```
    
    <aside>
    💡
    
    **Nguyên tắc cơ bản**
    ✓ Luôn kiểm tra và xác thực dữ liệu đầu vào từ mọi nguồn: người dùng, file, API và các nguồn bên ngoài. Không bao giờ tin tưởng bất kỳ input nào.
    
    **Lợi ích**
    ✓ Lập trình phòng thủ tạo ra code bền vững, có khả năng xử lý các tình huống bất ngờ và dễ dàng debug khi gặp vấn đề. Trong Python, việc kết hợp kiểm tra kiểu dữ liệu, assert và try-except sẽ giúp xây dựng code an toàn.
    
    </aside>
    
    ```jsx
    # Defensive programming
    def divide(a, b):
        if not isinstance(a, (int, float)) or not isinstance(b, (int, float)):
            raise TypeError("Tham số phải là số.")
        if b == 0:
            raise ValueError("Không thể chia cho 0.")
        return a / b
    
    def get_element(lst, index):
        if not isinstance(lst, list):
            raise TypeError("Tham số phải là list.")
        if index < 0
    
    ```
    
- **Xử lý lỗi (Error handling)**
    
    
    | Bắt lỗi quá chung chung B | Bắt lỗi cụ thể rõ ràng hơn |
    | --- | --- |
    
    ```jsx
    # Bad example
    try:
        with open("file.txt") as f:
            data = f.read()
            parsed = json.loads(data)
            result = 10 / parsed["value"]
    except Exception:
        pass  # lỗi bị bỏ qua hoàn toàn!
    
    ```
    
    <aside>
    💡
    
    ✓ Xử lý lỗi tốt không chỉ là bắt lỗi mà còn là truyền thông tin lỗi đúng cách.
    ✓ Sử dụng logging thay vì print và tạo custom exceptions khi cần thiết để làm rõ ngữ cảnh lỗi.
    
    </aside>
    
    ```jsx
    try:
        with open("file.txt") as f:
            data = f.read()
            parsed = json.loads(data)
            result = 10 / parsed["value"]
    except FileNotFoundError:
        logger.error("Không tìm thấy file.")
        raise ConfigError("File cấu hình không tồn tại")
    except json.JSONDecodeError:
        logger.error("File không đúng định dạng JSON.")
    except KeyError:
        logger.error("Thiếu trường 'value' trong dữ liệu.")
    except ZeroDivisionError:
        logger.error("Giá trị 'value' không thể bằng 0.")
    
    ```
    

---

## Phần 4: Nguyên tắc SOLID và Design Patterns (Nâng Cao)

### 4.1 Giới Thiệu SOLID Principles

| **Nguyên tắc** | Mô tả |
| --- | --- |
| **Single Responsibility** | Mỗi lớp chỉ nên có một lý do để thay đổi. Tập trung vào một nhiệm vụ duy nhất. |
| **Open/Closed** | Mở để mở rộng, đóng để sửa đổi. Code nên dễ mở rộng mà không cần sửa đổi. |
| **Liskov Substitution** | Các lớp con phải thay thế được lớp cha. Đảm bảo tính nhất quán. |
| **Interface Segregation** | Nhiều interface nhỏ tốt hơn một interface lớn. Tránh phụ thuộc không cần thiết. |
| **Dependency Inversion** | Phụ thuộc vào abstraction, không phụ thuộc vào cụ thể. Giảm sự ràng buộc. |

### 4.2 Áp Dụng SOLID Vào Python

| **Khái niệm** | Mô tả |
| --- | --- |
| **Tính Linh Hoạt** | Python dynamic typing cho phép dễ dàng thay đổi hành vi object trong runtime. Điều này giúp thiết kế các interface linh hoạt, đặc biệt hữu ích cho Open/Closed Principle khi mở rộng tính năng. |
| **Duck Typing** | Python thực hiện "nếu nó đi như vịt và kêu như vịt, thì nó là vịt". Các objects chỉ cần hiện thực các phương thức tương thích, không cần kế thừa, hỗ trợ tốt cho Liskov Substitution và Interface Segregation. |
| **Abstractions** | Module `abc` (Abstract Base Classes) cung cấp `@abstractmethod` decorator và ABC class để định nghĩa interface thuần khiết. Điều này đảm bảo các lớp con phải triển khai đúng các phương thức được yêu cầu, tăng cường Dependency Inversion. |
| **Composition** | Python khuyến khích "composition over inheritance" thông qua mixins và dependency injection. Thay vì kế thừa nhiều tầng, việc kết hợp các đối tượng nhỏ giúp đạt Single Responsibility và giảm phụ thuộc giữa các module. |

---

## Tổng kết:

- **Viết code sạch không chỉ giúp dễ đọc, mà còn dễ bảo trì và mở rộng.**

Áp dụng các nguyên tắc như PEP-8, tài liệu hóa bằng docstring/type hints và kiểm tra tự động giúp chuẩn hóa code ngay từ đầu.

- **Hiểu rõ Pythonic code giúp tận dụng tối đa sức mạnh của Python.**

Sử dụng `list/dict comprehensions`, `context managers`, và `assignment expressions` giúp viết code ngắn gọn, hiệu quả hơn.

- **Nguyên tắc SOLID**

Giúp kiến trúc phần mềm linh hoạt, giảm phụ thuộc và dễ mở rộng về sau.
