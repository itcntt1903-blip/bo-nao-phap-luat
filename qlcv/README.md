# QLCV – Hệ thống Quản lý Công việc & Đánh giá KPI

**Ban Quản lý dự án đầu tư xây dựng**

Ứng dụng web phân công, quản lý, nhắc việc và đánh giá KPI công việc hằng ngày cho từng chuyên viên thuộc Ban QLDA đầu tư xây dựng. Giao diện tiếng Việt, trực quan bằng biểu đồ Gantt, phân quyền chi tiết đến từng chức năng.

> Toàn bộ ứng dụng nằm trong **một file `index.html` duy nhất**, không cần cài đặt, không cần máy chủ. Mở bằng trình duyệt là chạy được ngay.

---

## 1. Tính năng chính

- **Tổng quan (Dashboard):** thống kê tổng công việc, đang thực hiện, hoàn thành, quá hạn; biểu đồ phân bố trạng thái; tỷ lệ đúng hạn; khối lượng theo chuyên viên; danh sách sắp đến hạn.
- **Quản lý công việc:** tạo – phân công – chỉnh sửa – xóa công việc; lọc theo trạng thái, ưu tiên, chuyên viên, dự án; cập nhật tiến độ (%), trạng thái; trao đổi/nhật ký trong từng việc; duyệt (nghiệm thu) công việc; xuất CSV.
- **Kế hoạch công việc ngày:** xem kế hoạch theo từng ngày, nhóm theo chuyên viên, nhận diện việc đến hạn / quá hạn.
- **Biểu đồ Gantt tiến độ:** trực quan toàn bộ kế hoạch trên trục thời gian, thanh màu theo trạng thái, hiển thị % tiến độ và mốc "Hôm nay".
- **Nhắc việc & thông báo:** chuông thông báo tự động nhắc việc quá hạn, đến hạn hôm nay, sắp đến hạn và việc chờ duyệt.
- **Đánh giá KPI chuyên viên:** chấm điểm và xếp hạng theo tỷ lệ đúng hạn, tỷ lệ hoàn thành, tiến độ và khối lượng; phân loại Xuất sắc / Tốt / Khá / Trung bình / Cần cải thiện; trọng số tùy chỉnh.
- **Quản lý tài khoản:** tạo/mời tài khoản bằng **số CCCD, email hoặc số điện thoại**; khóa/mở khóa; đặt lại mật khẩu.
- **Phân quyền chi tiết:** tài khoản quản trị phân quyền đến từng chức năng cho mỗi tài khoản — theo vai trò mặc định hoặc tùy chỉnh riêng.
- **Cài đặt hệ thống:** thông tin đơn vị, danh mục dự án, sao lưu/phục hồi dữ liệu, nhật ký hoạt động.
- **Khác:** giao diện sáng/tối, responsive (máy tính, máy tính bảng, điện thoại).

---

## 2. Tài khoản quản trị mặc định

| Mục | Giá trị |
|---|---|
| Tài khoản | `admin` |
| Mật khẩu | `admin@123` |

Có thể đăng nhập bằng **tên đăng nhập, số CCCD, email hoặc số điện thoại**. Các tài khoản mẫu khác (trưởng ban, phó ban, chuyên viên…) dùng mật khẩu `123456`.

> ⚠️ **Hãy đổi mật khẩu quản trị ngay sau lần đăng nhập đầu tiên** (menu người dùng → Đổi mật khẩu).

---

## 3. Vai trò & phân quyền

Hệ thống có 5 vai trò, mỗi vai trò có bộ quyền mặc định:

| Vai trò | Phạm vi |
|---|---|
| **Quản trị viên** | Toàn quyền hệ thống |
| **Trưởng ban** | Quản lý toàn bộ công việc, duyệt, xem KPI, cấu hình |
| **Phó ban** | Phụ trách mảng được giao, phân công & duyệt công việc |
| **Tổ trưởng** | Phụ trách tổ/nhóm, phân công trong phạm vi phòng/tổ |
| **Chuyên viên** | Thực hiện và cập nhật công việc được giao |

Quản trị viên có thể **tùy chỉnh chi tiết** quyền của từng tài khoản tại mục **Phân quyền** (ghi đè quyền mặc định của vai trò).

---

## 4. Công thức điểm KPI

Điểm KPI (thang 100) của mỗi chuyên viên trong kỳ đánh giá được tính theo trọng số (mặc định, có thể chỉnh):

```
Điểm KPI = 50% × Tỷ lệ đúng hạn
         + 30% × Tỷ lệ hoàn thành
         + 10% × Tiến độ trung bình
         + 10% × Khối lượng (tương đối so với nhóm)
```

Phân loại: **Xuất sắc** (≥90) · **Tốt** (75–89) · **Khá** (60–74) · **Trung bình** (40–59) · **Cần cải thiện** (<40).

---

## 5. Cách sử dụng / triển khai

### Cách 1 — Mở trực tiếp
Tải file `index.html` về máy và mở bằng trình duyệt (Chrome, Edge, Firefox…).

### Cách 2 — Đưa lên GitHub Pages (khuyến nghị, miễn phí)
1. Mở repo trên GitHub → **Settings** → **Pages**.
2. Mục **Source**, chọn nhánh `main`, thư mục `/ (root)` → **Save**.
3. Chờ 1–2 phút, truy cập đường dẫn: `https://<tên-tài-khoản>.github.io/qlcv-ban-qlda/`

### Cách 3 — Chạy máy chủ nội bộ
```bash
python3 -m http.server 8000
# rồi mở http://localhost:8000
```

---

## 6. Lưu ý quan trọng về dữ liệu

Phiên bản này là **ứng dụng chạy phía trình duyệt**, dữ liệu (tài khoản, công việc, KPI…) được lưu trong **bộ nhớ cục bộ của trình duyệt (localStorage)** trên **chính máy/thiết bị đang dùng**.

Điều đó có nghĩa là:
- Dữ liệu **không tự đồng bộ** giữa các máy/thiết bị khác nhau.
- Rất phù hợp để: demo, dùng cho một đầu mối điều phối, hoặc triển khai thử nghiệm.
- Để nhiều chuyên viên trên nhiều máy **dùng chung một kho dữ liệu thời gian thực**, cần kết nối một **máy chủ/cơ sở dữ liệu** (ví dụ Firebase, Supabase, hoặc API riêng). Lớp dữ liệu trong mã nguồn (`Store`) được thiết kế tách biệt để dễ nâng cấp sau này.

👉 Hãy dùng **Cài đặt → Dữ liệu → Xuất dữ liệu (.json)** để sao lưu định kỳ, và **Nhập dữ liệu** để phục hồi.

---

## 7. Công nghệ

- HTML5, CSS3 (hệ thống thiết kế tùy biến), JavaScript thuần (ES2020).
- Không phụ thuộc thư viện ngoài. Biểu đồ Gantt, biểu đồ tròn và vòng KPI đều được dựng thủ công.
- Font: Be Vietnam Pro / Inter (Google Fonts, có font dự phòng khi không có mạng).

---

## 8. Giấy phép

Phát hành theo giấy phép **MIT** — xem file `LICENSE`.
