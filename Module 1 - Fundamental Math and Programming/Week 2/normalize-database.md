# Chuẩn hóa dữ liệu trong Database và giới thiệu về phi chuẩn hóa

---

## Chuẩn hóa dữ liệu

Khi ta đánh giá, thiết kế cơ sở dữ liệu, gần như trong mọi trường hợp, dữ liệu ban đầu mà ta nhận được để thiết kế đều là dữ liệu thô, gặp rất nhiều vấn đề như dư thừa dữ liệu hay dữ liệu không nhất quán dẫn đến một số dị thường trong dữ liệu. Đó chính là lí do mà ta cần chuẩn hóa dữ liệu để dữ liệu trong Database.

Giả sử, ta có bảng `RawMovies` lưu thông tin phim, đạo diễn, diễn viên và thể loại, với các cột có nhóm lặp:

| MovieID | MovieTitle | Year | Rating | DirectorID | DirectorName      | Actors                                        | Genres | GenreDesc                 |
| ------- | ---------- | ---- | ------ | ---------- | ----------------- | --------------------------------------------- | ------ | ------------------------- |
| M1      | Inception  | 2010 | 8.8    | D1         | Christopher Nolan | A1–Leonardo DiCaprio; A2–Joseph Gordon-Levitt | G1; G2 | Science Fiction; Thriller |
| M2      | Titanic    | 1997 | 7.8    | D2         | James Cameron     | A1–Leonardo DiCaprio; A3–Kate Winslet         | G3; G4 | Romance; Drama            |

---

## Bước 1: Chuẩn hóa đến 1NF

Loại bỏ nhóm lặp, phân tách mỗi cặp (MovieID, ActorID, GenreCode) thành một dòng riêng, đưa `ActorID` và `GenreCode` về cột riêng.

| MovieID | MovieTitle | Year | Rating | DirectorID | DirectorName      | ActorID | ActorName            | GenreCode | GenreDesc       |
| ------- | ---------- | ---- | ------ | ---------- | ----------------- | ------- | -------------------- | --------- | --------------- |
| M1      | Inception  | 2010 | 8.8    | D1         | Christopher Nolan | A1      | Leonardo DiCaprio    | G1        | Science Fiction |
| M1      | Inception  | 2010 | 8.8    | D1         | Christopher Nolan | A1      | Leonardo DiCaprio    | G2        | Thriller        |
| M1      | Inception  | 2010 | 8.8    | D1         | Christopher Nolan | A2      | Joseph Gordon-Levitt | G1        | Science Fiction |
| M1      | Inception  | 2010 | 8.8    | D1         | Christopher Nolan | A2      | Joseph Gordon-Levitt | G2        | Thriller        |
| M2      | Titanic    | 1997 | 7.8    | D2         | James Cameron     | A1      | Leonardo DiCaprio    | G3        | Romance         |
| M2      | Titanic    | 1997 | 7.8    | D2         | James Cameron     | A1      | Leonardo DiCaprio    | G4        | Drama           |
| M2      | Titanic    | 1997 | 7.8    | D2         | James Cameron     | A3      | Kate Winslet         | G3        | Romance         |
| M2      | Titanic    | 1997 | 7.8    | D2         | James Cameron     | A3      | Kate Winslet         | G4        | Drama           |

* Khóa chính tạm thời: (MovieID, ActorID, GenreCode).
* Bảng đã đạt 1NF (mọi ô đều nguyên tử).

---

## Bước 2: Chuẩn hóa đến 2NF

Xác định các phụ thuộc một phần:

* `MovieID → MovieTitle, Year, Rating, DirectorID, DirectorName`
* `ActorID → ActorName`
* `GenreCode → GenreDesc`

Tách thành các bảng con, giữ lại bảng liên kết chứa đầy đủ thứ nguyên:

1. **Movies\_2NF** (MovieID là khóa):

   | MovieID | MovieTitle | Year | Rating | DirectorID | DirectorName      |
   | ------- | ---------- | ---- | ------ | ---------- | ----------------- |
   | M1      | Inception  | 2010 | 8.8    | D1         | Christopher Nolan |
   | M2      | Titanic    | 1997 | 7.8    | D2         | James Cameron     |

2. **Actors\_2NF** (ActorID là khóa):

   | ActorID | ActorName            |
   | ------- | -------------------- |
   | A1      | Leonardo DiCaprio    |
   | A2      | Joseph Gordon-Levitt |
   | A3      | Kate Winslet         |

3. **Genres\_2NF** (GenreCode là khóa):

   | GenreCode | GenreDesc       |
   | --------- | --------------- |
   | G1        | Science Fiction |
   | G2        | Thriller        |
   | G3        | Romance         |
   | G4        | Drama           |

4. **R\_MovieActorGenre\_2NF** (khóa: MovieID, ActorID, GenreCode):

   | MovieID | ActorID | GenreCode |
   | ------- | ------- | --------- |
   | M1      | A1      | G1        |
   | M1      | A1      | G2        |
   | …       | …       | …         |
   | M2      | A3      | G4        |

> **Lưu ý:** Ở giai đoạn này, chúng ta chỉ tách phụ thuộc một phần; còn phụ thuộc bắc cầu (`DirectorID → DirectorName`) vẫn nằm trong bảng `Movies_2NF`.

---

## Bước 3: Chuẩn hóa đến 3NF

Xác định phụ thuộc bắc cầu trong `Movies_2NF`:

```
MovieID → DirectorID → DirectorName
```

Vì `DirectorName` phụ thuộc qua `DirectorID` (một thuộc tính không phải khóa), ta tách:

1. **Movies\_3NF**: (chỉ giữ DirectorID)

   | MovieID | MovieTitle | Year | Rating | DirectorID |
   | ------- | ---------- | ---- | ------ | ---------- |
   | M1      | Inception  | 2010 | 8.8    | D1         |
   | M2      | Titanic    | 1997 | 7.8    | D2         |

2. **Directors\_3NF**: (DirectorID → DirectorName)

   | DirectorID | DirectorName      |
   | ---------- | ----------------- |
   | D1         | Christopher Nolan |
   | D2         | James Cameron     |

Các bảng **Actors\_2NF**, **Genres\_2NF** và **R\_MovieActorGenre\_2NF** trước đó cũng đều đã ở 3NF (không còn transitive nào).

---

## Bước 4: Chuẩn hóa đến 4NF

Trong bảng **R\_MovieActorGenre\_2NF**, ta có hai phụ thuộc đa giá trị độc lập trên cùng thuộc tính `MovieID`:

* `MovieID →→ ActorID`
* `MovieID →→ GenreCode`

Để loại bỏ, ta tách thành hai bảng:

1. **MovieActors**

   | MovieID | ActorID |
   | ------- | ------- |
   | M1      | A1      |
   | M1      | A2      |
   | M2      | A1      |
   | M2      | A3      |

2. **MovieGenres**

   | MovieID | GenreCode |
   | ------- | --------- |
   | M1      | G1        |
   | M1      | G2        |
   | M2      | G3        |
   | M2      | G4        |

Các bảng khác giữ nguyên. Vậy là các bảng hiện tại đã đạt được 4NF.

---

## Bước 5: Chuẩn hóa đến 5NF

5NF yêu cầu không còn phụ thuộc kết nối, nghĩa là tách thành các bảng nhỏ hơn và các bảng đó có thể nối lại tạo thành bảng ban đầu

* Các bảng hiện tại (`Movies_3NF`, `Directors_3NF`, `Actors_2NF`, `Genres_2NF`, `MovieActors`, `MovieGenres`) chỉ có 2-3 cột mỗi bảng, và mọi mối quan hệ đều qua khoá chính/khoá ngoại đơn giản.
* Không tồn tại một phân mảnh nào thêm mà khi ghép ngược sẽ sinh ra bảng ban đầu.

Vậy dữ liệu hiện tại đã đạt 5NF mà không cần tách thêm.

---

## Nên hay không nên chuẩn hóa dữ liệu?

Chuẩn hóa dữ liệu tồn tại vì những lý do sau:

- Giảm dư thừa, từ đó giảm khả năng xảy ra bất thường khi dữ liệu bị sửa đổi.

- Tiết kiệm không gian, thúc đẩy cấu trúc cơ sở dữ liệu tốt hơn, dễ bảo trì và mở rộng.

- Ngược lại, cơ sở dữ liệu lộn xộn với hàng chục cột sẽ cực khó duy trì — vừa phải sửa code cập nhật ID, vừa phải thêm cột khi muốn mở rộng.

Tuy nhiên, chuẩn hóa cũng có nhược điểm: khi dữ liệu được chia nhỏ ra nhiều bảng, truy vấn trở nên phức tạp hơn — có thể cần viết SQL với joins qua hàng chục bảng chỉ để lấy một trường. Quá mức chuẩn hóa (over-normalization) cũng dẫn đến cấu trúc cồng kềnh, kém hiệu quả.

Và không phải trường hợp nào cũng phù hợp — lúc này ta cân nhắc đến denormalization - phi chuẩn hóa.

---

## Phi chuẩn hóa dữ liệu

Trong khi chuẩn hóa là lý thuyết cơ bản của RDBMS, thực tế đôi khi buộc ta phi chuẩn hóa: thêm có chủ ý sự dư thừa vào cơ sở dữ liệu để cải thiện hiệu năng đọc, nhất là khi thao tác đọc nhiều hơn ghi. Ví dụ rõ nhất với kỹ sư dữ liệu là kho dữ liệu (data warehouse).

**Trường hợp sử dụng phi chuẩn hóa:**

- Báo cáo và phân tích: Khi nhắc đến mô hình dữ liệu, hầu hết sẽ nghĩ đến kho dữ liệu. Dĩ nhiên mô hình dữ liệu rộng hơn, bao gồm cả use case vận hành và phân tích.
- Ứng dụng đọc nhiều: Khi tốc độ đọc quyết định trải nghiệm người dùng.

**Các đánh đổi của phi chuẩn hóa:**

- Dư thừa dữ liệu, tăng nguy cơ bất thường và chi phí lưu trữ.
- Nhưng với hệ thống đọc nhiều, lợi ích về tốc độ truy xuất thường bù đắp được chi phí lưu trữ và rủi ro.
- Các kho dữ liệu hay hệ thống phân tích thường có kiểm tra chất lượng dữ liệu khi nạp bảng, giúp giảm rủi ro.

**Tìm sự cân bằng:**

Quyết định chuẩn hóa hay phi chuẩn hóa thường mang tính hướng dẫn hơn là tuyệt đối. Có thể bạn chủ động thiết kế một số phần của cơ sở vận hành thành phi chuẩn hóa. Thông thường, đối với cơ sở dữ liệu phục vụ việc vận hành của một công ty, giao dịch thì ta sẽ cần chuẩn hóa dữ liệu với việc ghi dữ liệu có hiệu suất tốt, tính mở rộng và toàn vẹn dữ liệu cao. Còn đối với việc thiết kế dữ liệu phục vụ nhu cầu phân tích hay phục vụ các mô hình ML, AI; ta sẽ chọn cách phi chuẩn hóa để tăng hiệu năng đọc trên dữ liệu lớn, nó sẽ tốt hơn cho mục đích phân tích, báo cáo, đòi hỏi các truy vấn phức tạp nếu không được phi chuẩn hóa.
