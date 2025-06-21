# Git & Github for version control

## Git và GitHub: Tại sao chúng lại cần thiết?

> **💡 Trong thế giới phát triển phần mềm, việc quản lý mã nguồn và cộng tác nhóm luôn là một thách thức lớn.** Các hệ thống kiểm soát phiên bản tập trung (Centralized VCS) được tạo ra để giải quyết vấn đề này, nhưng lại có nhiều **hạn chế và rủi ro đáng kể**. Hệ thống này phụ thuộc hoàn toàn vào một **máy chủ trung tâm duy nhất** — điểm yếu nghiêm trọng có thể khiến toàn bộ dự án bị đình trệ khi gặp sự cố. Ngoài ra, nó còn gây khó khăn trong việc làm việc ngoại tuyến và làm phức tạp hóa quy trình phân nhánh và hợp nhất mã nguồn. Từ những hạn chế này, các **hệ thống kiểm soát phiên bản phân tán (Distributed VCS)** đã ra đời và phát triển mạnh mẽ, trong đó nổi bật nhất là **Git**.
>
> Với Git, mỗi nhà phát triển đều sở hữu một bản sao hoàn chỉnh của toàn bộ kho mã nguồn, mở ra một kỷ nguyên mới của sự linh hoạt, bền vững và hiệu quả vượt trội trong phát triển phần mềm theo nhóm.

- **Nguyên lý hoạt động của Git**
    - 📸 **Snapshot thay vì Diff** (Chụp hình toàn bộ thay vì chỉ ghi sự thay đổi)
    - 🛡️ **Toàn vẹn dữ liệu với SHA-1**
        - Mỗi “ảnh chụp” của bạn sẽ được **đánh dấu bằng một mã đặc biệt rất dài (40 ký tự)** – gọi là mã SHA-1. **Nếu bạn thay đổi chỉ 1 chữ**, mã đó sẽ **thay đổi hoàn toàn**, nên Git biết chính xác khi nào bài làm bị thay đổi.
    - 🛰️ **Nguyên lý "Offline-first"**
        - **Cho phép bạn làm mọi việc mà không cần mạng Internet**: viết code, lưu lại, tạo phiên bản mới...

---

## Cài đặt và cấu hình Git cho Windows

- **Cấu hình cơ bản:**
    - Thiết lập thông tin người dùng và các tùy chọn căn bản:
    ```bash
    git config --global user.name "Tên Của Bạn"
    git config --global user.email "email@example.com"
    git config --global core.editor "code --wait" # (nếu IDE là VScode)
    git config --global color.ui auto
    ```
- **Sử dụng Git Bash (nếu bạn đã cài đặt Git cho Windows):**
    - Mở tìm kiếm Windows (nhấn phím Windows + S hoặc click vào biểu tượng kính lúp).
    - Gõ `Git Bash` và chọn ứng dụng `Git Bash` để mở.
    - Sau đó, dán từng lệnh vào cửa sổ Git Bash và nhấn Enter.
- **Sử dụng Command Prompt (CMD) hoặc PowerShell:**
    - Mở tìm kiếm Windows.
    - Gõ `cmd` hoặc `powershell` và mở ứng dụng tương ứng.
    - Dán từng lệnh vào cửa sổ và nhấn Enter.
- Nếu bạn nhận được thông báo "The system cannot find the file specified." (Hệ thống không thể tìm thấy tệp được chỉ định) khi chạy lệnh `notepad C:\Users\admin\.gitconfig` hoặc `type C:\Users\admin\.gitconfig` trong CMD, điều đó có thể do một trong các lý do sau:
    - **Bạn gõ sai tên người dùng hoặc đường dẫn:**
        - Hãy chắc chắn rằng `admin` là tên người dùng chính xác của bạn. Bạn có thể xác nhận tên người dùng bằng cách mở Command Prompt và gõ `echo %username%` hoặc mở File Explorer và xem tên thư mục trong `C:\Users`.
    - File `.gitconfig` chưa tồn tại:
        - Đây là lý do phổ biến nhất. File `.gitconfig` chỉ được tạo ra sau khi bạn chạy các lệnh cấu hình Git toàn cục lần đầu tiên, ví dụ: `git config --global user.name "Tên Của Bạn"`.
- **Làm thế nào để kiểm tra xem cấu hình đã được áp dụng chưa?**
    - Bạn có thể chạy lệnh sau trong Git Bash để kiểm tra tên người dùng hiện tại của Git:
        ```bash
        git config --global user.name
        ```
    - Nếu nó trả về `Nguyễn Văn A`, nghĩa là cấu hình đã thành công.

---

## Hướng Dẫn Markdown Cho Blog GitHub Của Bạn!

### 1. Tiêu Đề (Headings): Giúp cấu trúc bài viết của bạn một cách rõ ràng. Sử dụng dấu `#` cho các cấp độ tiêu đề khác nhau:

```markdown
# Tiêu đề cấp 1
## Tiêu đề cấp 2
### Tiêu đề cấp 3
#### Tiêu đề cấp 4
##### Tiêu đề cấp 5
###### Tiêu đề cấp 6

### 2. Định Dạng Văn Bản (Text Formatting): Làm nổi bật những phần quan trọng:

- **In đậm:** `**văn bản in đậm**` hoặc `__văn bản in đậm__`
- **In nghiêng:** `*văn bản in nghiêng*` hoặc `_văn bản in nghiêng_`
- **In đậm và Nghiêng:** `***văn bản in đậm và nghiêng***`
- **Gạch ngang:** `~~văn bản gạch ngang~~`

### 3. Danh Sách (Lists): Tổ chức thông tin một cách ngăn nắp:

- **Danh sách không có thứ tự:**
    ```markdown
    - Mục thứ nhất
    - Mục thứ hai
      - Mục con của mục thứ hai
    * Mục khác
    ```
- **Danh sách có thứ tự:**
    ```markdown
    1. Bước một
    2. Bước hai
       1. Bước con của bước hai
    3. Bước ba
    ```

### 4. Liên Kết (Links): Kết nối bài viết của bạn với các tài nguyên bên ngoài:

```markdown
[Văn bản liên kết](https://www.example.com)
