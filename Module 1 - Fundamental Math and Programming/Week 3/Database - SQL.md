
# 📚 SQL trong Phân tích Dữ liệu

## Giới thiệu

SQL là một công cụ quan trọng trong **phân tích dữ liệu**. Bài học này giúp bạn tìm hiểu cách sử dụng SQL cho các tác vụ phân tích dữ liệu nâng cao, bao gồm **subqueries**, **stored procedures**, **triggers**, và một số **SQL nâng cao** khác như **joins** và **common table expressions**.

---

## 1. SQL Join

### Đặc điểm
- **Join** là phương thức kết nối dữ liệu từ hai hoặc nhiều bảng trong cơ sở dữ liệu.
- **INNER JOIN** trả về các bản ghi chỉ khi có sự kết nối giữa các bảng.
- Các loại **Join**:
  - **LEFT JOIN**: Trả về tất cả bản ghi từ bảng bên trái và dữ liệu khớp từ bảng bên phải.
  - **RIGHT JOIN**: Trả về tất cả bản ghi từ bảng bên phải và dữ liệu khớp từ bảng bên trái.
  - **FULL OUTER JOIN**: Trả về tất cả dữ liệu từ cả hai bảng.

#### Ví dụ:
```sql
SELECT c.customer_id, c.first_name, o.order_id
FROM customers c
INNER JOIN orders o
ON c.customer_id = o.customer_id;
```

---

## 2. Common Table Expression (CTE)

### Đặc điểm
- CTE giúp viết truy vấn **tạm thời** dễ đọc và tổ chức hơn trong SQL.
- Cú pháp sử dụng `WITH`:
```sql
WITH cte_name AS (
    SELECT ...
    FROM ...
)
SELECT ...
FROM cte_name;
```

#### Ví dụ:
```sql
WITH invoice_amount AS (
    SELECT client_id, SUM(invoice_total) AS total_amount
    FROM invoices
    GROUP BY client_id
)
SELECT c.client_id, c.name, i.total_amount
FROM clients c
JOIN invoice_amount i
ON c.client_id = i.client_id;
```

---

## 3. SQL Subqueries

### Đặc điểm
- **Subquery** là một truy vấn lồng trong một truy vấn khác.
- Dùng để tính toán các giá trị trung gian cho truy vấn chính.

#### Ví dụ:
```sql
SELECT client_id, name
FROM clients c
WHERE c.client_id = (
    SELECT client_id
    FROM payments
    WHERE amount > 1000
    LIMIT 1
);
```

---

## 4. SQL Temp Table

### Đặc điểm
- **Temporary Tables** được sử dụng để lưu trữ tạm thời kết quả truy vấn trong suốt phiên làm việc.
- Dữ liệu trong bảng tạm thời sẽ bị xóa khi kết thúc phiên làm việc.

#### Ví dụ:
```sql
CREATE TEMPORARY TABLE temp_invoice AS
SELECT client_id, SUM(invoice_total) AS invoice_sum
FROM invoices
GROUP BY client_id;
```

---

## 5. SQL Stored Procedures

### Đặc điểm
- **Stored Procedures** là những tập hợp các câu lệnh SQL được lưu trữ và thực thi dưới dạng một hàm đã được viết sẵn.

#### Ví dụ:
```sql
DELIMITER //
CREATE PROCEDURE update_invoice_total()
BEGIN
    UPDATE invoices
    SET total_amount = total_amount * 1.1;
END //
DELIMITER ;
```

---

## 6. SQL Trigger

### Đặc điểm
- **Trigger** là một tập hợp các câu lệnh SQL tự động được thực thi khi có sự thay đổi trong bảng (INSERT, UPDATE, DELETE).

#### Ví dụ:
```sql
CREATE TRIGGER after_employee_update
AFTER UPDATE ON employees
FOR EACH ROW
    INSERT INTO audit_log (action, employee_id)
    VALUES ('Updated', NEW.employee_id);
```

---

## 7. Luyện tập SQL

### Ví dụ thực hành
1. **Sử dụng database sql_hr**: Tạo một truy vấn để liệt kê các nhân viên có mức lương cao hơn quản lý của họ.
2. **Sử dụng database sql_store**: Tạo một bảng tạm thời để lưu trữ tổng số sản phẩm đã bán và tổng doanh thu cho mỗi khách hàng.

---

## Kết luận

SQL là công cụ không thể thiếu trong phân tích dữ liệu. Các kỹ thuật như **JOIN**, **Subquery**, **CTE**, **Temp Table**, **Stored Procedures**, và **Trigger** sẽ giúp bạn tối ưu hóa và nâng cao hiệu quả khi làm việc với cơ sở dữ liệu. Bạn hãy thực hành để làm quen và sử dụng chúng hiệu quả trong các bài toán thực tế.
