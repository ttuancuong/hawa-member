# TÀI LIỆU ĐẶC TẢ NGHIỆP VỤ (SRS) - MODULE QUẢN LÝ HỘI PHÍ
**Dự án Giai đoạn 1:** HỆ THỐNG QUẢN LÝ HỘI VIÊN HAWA
**Định hướng Giai đoạn 2:** HỆ THỐNG QUẢN LÝ HỘI HAWA (Toàn diện)
**Tổ chức:** HỘI MỸ NGHỆ VÀ CHẾ BIẾN GỖ THÀNH PHỐ HỒ CHÍ MINH (HAWA)

---

## I. GIỚI THIỆU CHUNG
Tài liệu này quy định các quy tắc nghiệp vụ, quy trình vận hành và yêu cầu kỹ thuật cho Module **Hội phí**. Đây là module cốt lõi nhằm tự động hóa việc tính toán, nhắc nợ và ghi nhận các khoản thu từ hội viên.

## II. THÔNG TIN TỔ CHỨC & KHỐI NGÀNH
Hệ thống áp dụng các quy tắc dựa trên cơ cấu ngành nghề hiện tại của HAWA:
- **Tên đầy đủ:** HỘI MỸ NGHỆ VÀ CHẾ BIẾN GỖ THÀNH PHỐ HỒ CHÍ MINH
- **Tên thường gọi:** HAWA
- **Các khối ngành nghề áp dụng:** 
  1. Chế biến gỗ
  2. Thủ công mỹ nghệ
  3. Thương mại - Dịch vụ
  4. Đào tạo / Trường học

## III. QUY TẮC NGHIỆP VỤ CHI TIẾT (BUSINESS RULES)

### 1. Phân loại Mức đóng Hội phí (Niên độ 2026)
Hệ thống tự động xác định mức phí dựa trên danh mục ngành nghề:

| STT | Khối ngành nghề | Hội phí hàng năm (VNĐ) | Lệ phí gia nhập (VNĐ) |
|:---:|:---|:---:|:---:|
| 1 | Thủ công mỹ nghệ | 2.000.000 | 1.000.000 |
| 2 | Chế biến gỗ | 5.000.000 | 1.000.000 |
| 3 | Thương mại - Dịch vụ | 5.000.000 | 1.000.000 |
| 4 | Đào tạo / Trường học | 2.000.000 | 1.000.000 |

### 2. Quy định về Lệ phí Gia nhập (Joining Fee)
- **Đối tượng:** Chỉ áp dụng cho Hội viên đăng ký tham gia **lần đầu tiên**.
- **Mức phí:** **1.000.000 VNĐ** (Một triệu đồng).
- **Cách thu:** Thu đồng thời cùng với Hội phí của năm đầu tiên. Từ năm thứ hai trở đi, hội viên chỉ đóng Hội phí thường niên theo quy định.

> [!IMPORTANT]
> **Công thức tính thu lần đầu:** 
> `Số tiền thu = Hội phí (theo ngành nghề) + 1.000.000 VNĐ (Lệ phí gia nhập)`

### 3. Chính sách Chiết khấu & Tính toán
Hệ thống hỗ trợ tự động tính toán khi hội viên đóng nhiều năm liên tiếp (Lưu ý: Chiết khấu chỉ áp dụng cho phần Hội phí, không áp dụng cho Lệ phí gia nhập):
- **Đóng 02 năm liên tiếp:** Giảm **10%** tổng số tiền.
- **Đóng 03 năm liên tiếp:** Giảm **15%** tổng số tiền.

> [!IMPORTANT]
> **Quy tắc hiển thị:** Khi được chiết khấu, tổng số tiền sẽ được chia đều cho mỗi năm trong sổ cái. 
> *Ví dụ:* Đóng 3 năm khối Chế biến gỗ (5tr/năm) được giảm 15%. Tổng thu: 12.750.000 VNĐ. Hệ thống sẽ ghi nhận mỗi năm là 4.250.000 VNĐ kèm ghi chú "(Đóng hội phí 03 năm liên tiếp)".

### 3. Quy trình tính hạn & Gia hạn (Membership Validity)
Quy trình được phân loại dựa trên thời điểm gia nhập:

*   **Trường hợp 1 (Gia nhập Tháng 01 - Tháng 10):**
    *   Hạn hội viên là 01 năm kể từ ngày ký quyết định gia nhập.
    *   *Ví dụ:* Gia nhập 15/05/2025 → Hết hạn 15/05/2026.
*   **Trường hợp 2 (Gia nhập Tháng 11 - Tháng 12):**
    *   Được miễn hội phí 02 tháng cuối năm gia nhập.
    *   Khoản phí đóng lần đầu được tính cho cả năm tiếp theo.
    *   Hạn gia hạn tiếp theo sẽ bắt đầu từ **01/01** của năm sau nữa.
    *   *Ví dụ:* Gia nhập 05/11/2025 → Hạn đóng tiếp theo là 01/01/2027.

### 4. Trường hợp Miễn Hội phí (0 VNĐ)
Hệ thống cho phép admin ghi nhận các trường hợp thu 0 đồng (Miễn phí):
- **Yêu cầu:** Phải nhập **Lý do (Ghi chú)** cụ thể cho năm được miễn.
- **Mục đích:** Đảm bảo tính liên tục của lịch sử hội viên và không làm gián đoạn trạng thái "Hoạt động".

## IV. QUẢN LÝ TRẠNG THÁI & NHẮC NỢ

### 1. Hệ thống Trạng thái Hội viên (5 Trạng thái)

| Trạng thái | Màu sắc | Ý nghĩa nghiệp vụ |
|:---|:---:|:---|
| **Hoạt động** | ![#2ecc71](https://via.placeholder.com/15/2ecc71?text=+) **Xanh lá** | Đang sinh hoạt và hoàn thành đầy đủ nghĩa vụ phí. |
| **Ngừng hoạt động** | ![#95a5a6](https://via.placeholder.com/15/95a5a6?text=+) **Xám** | Đã rời hội, đóng mã số thuế hoặc bị xóa tên. |
| **Xét duyệt gia nhập**| ![#3498db](https://via.placeholder.com/15/3498db?text=+) **Xanh dương**| Hội viên mới đang chờ Ban chấp hành phê duyệt. |
| **Xét duyệt rời hội** | ![#e67e22](https://via.placeholder.com/15/e67e22?text=+) **Cam** | Đang xử lý hồ sơ xin nghỉ hoặc chuyển công tác. |
| **Tạm ngưng** | ![#e74c3c](https://via.placeholder.com/15/e74c3c?text=+) **Đỏ** | Hội viên nợ phí lâu ngày hoặc vi phạm nội quy. |

### 2. Kế hoạch Nhắc nợ Tự động (Notifications)

| Mốc cảnh báo | Đối tượng | Hành động của hệ thống |
|:---|:---|:---|
| **45 ngày trước hạn** | Hội viên sắp hết hạn | Hiển thị cảnh báo trên Dashboard nhân sự. |
| **Tháng 3 hàng năm** | Hội viên cũ & nợ cũ | Gửi Email nhắc nợ đồng loạt (Template Q1). |
| **Tháng 6 hàng năm** | Các hội viên còn nợ | Gửi Email nhắc nợ đồng loạt (Template Q2). |
| **Tháng 9 hàng năm** | Các hội viên còn nợ | Gửi Email nhắc nợ đồng loạt (Template Q3). |
| **Nợ 18 - 24 tháng** | Nợ xấu | Báo đỏ nổi bật, chuẩn bị chuyển trạng thái Tạm ngưng. |
| **Nợ trên 5 năm** | Nợ rất xấu | Đánh dấu hồ sơ cần xử lý đặc biệt bởi Ban chấp hành. |

## V. YÊU CẦU VỀ GIAO DIỆN & TÍNH NĂNG (Portal)

1.  **Dashboard Linh hoạt:** Cho phép người dùng chọn **Ẩn/Hiện** các cột thông tin tùy theo nhu cầu báo cáo.
2.  **Hệ thống Email (Mẫu sẵn):**
    *   Tích hợp nút gửi Email trực tiếp từ thông tin hội viên.
    *   Sử dụng Template gán sẵn các tham số (Tên công ty, Số tiền nợ, Hạn đóng).
    *   Người dùng có thể chỉnh sửa nội dung Email trước khi bấm gửi.
3.  **Lịch sử Thu phí:** Hiển thị danh sách phiếu thu theo năm, ghi chú rõ ràng các khoản chiết khấu hoặc miễn phí (0đ).

---
*Tài liệu được cập nhật dựa trên Biên bản Review 01 ngày 07/04/2026 và các yêu cầu bổ sung về Miễn hội phí.*
