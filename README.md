# 23634501_TranHuynhMinhNhat_Cabsystem
## Business Requirements
### Hiện tại, doanh nghiệp ABC đang cung cấp dịch vụ đặt xe nhưng hệ thống hiện có còn nhiều hạn chế. Việc phân công tài xế chủ yếu được thực hiện thủ công, gây mất thời gian, dễ xảy ra sai sót và khó xử lý khi số lượng khách hàng và tài xế tăng cao. Khách hàng khó theo dõi trạng thái chuyến đi, không biết hệ thống đang tìm tài xế, tài xế nào đã nhận chuyến hoặc chuyến đang ở trạng thái nào. Bên cạnh đó, thông tin thanh toán chưa được quản lý tập trung, gây khó khăn trong việc tra cứu và xử lý các giao dịch. Bộ phận vận hành cũng gặp khó khăn khi theo dõi các chuyến đang diễn ra, quản lý tài xế, xử lý các trường hợp chuyến bị lỗi và tổng hợp báo cáo.
### Vì vậy, doanh nghiệp có nhu cầu xây dựng một hệ thống CAB mới nhằm tự động hóa toàn bộ quy trình đặt xe, từ khi khách hàng tạo yêu cầu, hệ thống tìm và phân công tài xế, tài xế thực hiện chuyến, tính cước, thanh toán đến đánh giá sau chuyến. Hệ thống cần hỗ trợ khách hàng, tài xế và nhân viên vận hành, giúp quản lý tập trung thông tin và nâng cao hiệu quả hoạt động. Đồng thời, hệ thống phải ổn định, bảo mật, có khả năng mở rộng khi số lượng người dùng tăng và cho phép doanh nghiệp dễ dàng bổ sung các loại dịch vụ, phương thức thanh toán hoặc kênh thông báo mới trong tương lai.

## Stakeholder

| Stakeholder | Vai trò |
|---|---|
| **Ban giám đốc** | Đưa ra mục tiêu, yêu cầu kinh doanh; phê duyệt phạm vi và định hướng phát triển hệ thống; theo dõi báo cáo và hiệu quả hoạt động. |
| **Khách hàng** | Sử dụng hệ thống để đăng ký, đặt xe, theo dõi chuyến, thanh toán, xem lịch sử và đánh giá tài xế. |
| **Tài xế** | Nhận và thực hiện chuyến; cập nhật trạng thái hoạt động, thông tin phương tiện, vị trí và trạng thái chuyến đi. |
| **Nhà cung cấp thanh toán** | Xử lý thanh toán điện tử và trả kết quả giao dịch. |
| **Nhà cung cấp bản đồ/GPS** | Cung cấp vị trí, bản đồ, khoảng cách và ETA. |
| **Bộ phận CSKH** | Tiếp nhận khiếu nại, hỗ trợ khách hàng/tài xế, xử lý vấn đề chuyến đi. |
| **Nhà cung cấp thông báo** | Gửi SMS, email, push notification. |
| **Nhân viên vận hành** | Quản lý khách hàng, tài xế, phương tiện và chuyến đi; theo dõi hoạt động và xử lý các trường hợp chuyến bị lỗi. |
| **Bộ phận tài chính** | Theo dõi, kiểm tra và đối soát các giao dịch thanh toán, doanh thu từ các chuyến đi. |

## Stakeholder Matrix

Stakeholder Matrix được xây dựng dựa trên hai tiêu chí:

- **Power:** Mức độ quyền lực và khả năng ảnh hưởng đến dự án.
- **Interest:** Mức độ quan tâm và tham gia vào hệ thống CAB.

```mermaid
quadrantChart
    title Stakeholder Matrix - CAB System
    x-axis Interest thấp --> Interest cao
    y-axis Power thấp --> Power cao

    quadrant-1 Manage Closely
    quadrant-2 Keep Satisfied
    quadrant-3 Monitor
    quadrant-4 Keep Informed

    Ban giám đốc: [0.85, 0.90]
    Nhân viên vận hành: [0.82, 0.80]

    Khách hàng: [0.85, 0.30]
    Tài xế: [0.80, 0.25]
    Bộ phận CSKH: [0.78, 0.40]
    Bộ phận tài chính: [0.75, 0.55]

    Nhà cung cấp thanh toán: [0.40, 0.25]
    Nhà cung cấp bản đồ/GPS: [0.35, 0.20]
    Nhà cung cấp thông báo: [0.30, 0.15]
```
## Business Goals

| ID | Business Goal | Mô tả |
|---|---|---|
| **BG-01** | **Tự động hóa quy trình đặt xe** | Giảm việc tiếp nhận và phân công tài xế thủ công bằng cách tự động hóa quy trình đặt xe và tìm kiếm tài xế. |
| **BG-02** | **Nâng cao trải nghiệm khách hàng** | Giúp khách hàng dễ dàng đặt xe, theo dõi trạng thái chuyến, biết thông tin tài xế, thời gian dự kiến đến và đánh giá sau chuyến. |
| **BG-03** | **Tối ưu hóa việc phân công tài xế** | Tự động tìm và ưu tiên tài xế phù hợp, gần khách hàng; tiếp tục tìm tài xế khác nếu tài xế không phản hồi hoặc từ chối chuyến. |
| **BG-04** | **Hỗ trợ đa dạng phương thức thanh toán** | Cho phép khách hàng thanh toán bằng **tiền mặt hoặc thanh toán điện tử/chuyển khoản**, đồng thời tích hợp với nhà cung cấp thanh toán bên ngoài để xử lý giao dịch điện tử. |
| **BG-05** | **Quản lý tập trung hoạt động kinh doanh** | Tập trung quản lý thông tin khách hàng, tài xế, phương tiện, chuyến đi, thanh toán và lịch sử giao dịch trên một hệ thống. |
| **BG-06** | **Nâng cao hiệu quả vận hành** | Hỗ trợ nhân viên vận hành theo dõi chuyến đi, trạng thái tài xế, xử lý các trường hợp bất thường và tra cứu thông tin cần thiết. |


## Phạm vi dự án

Trong 7 tuần, dự án tập trung xây dựng các module cốt lõi để hệ thống CAB có thể vận hành đầy đủ quy trình đặt xe.

### 1. Quản lý người dùng (User Management)

- Đăng ký tài khoản khách hàng.
- Đăng nhập / đăng xuất.
- Cập nhật thông tin cá nhân.
- Xác thực người dùng.
- Phân quyền người dùng cơ bản.

**Đối tượng:** Khách hàng, Tài xế, Nhân viên vận hành.

---

### 2. Quản lý tài xế (Driver Management)

- Quản lý thông tin tài xế.
- Quản lý thông tin phương tiện.
- Cập nhật trạng thái hoạt động.
- Bật / tắt trạng thái sẵn sàng nhận chuyến.
- Ghi nhận vị trí hiện tại của tài xế.
- Theo dõi trạng thái tài xế.

**Đối tượng:** Tài xế, Nhân viên vận hành.

---

### 3. Quản lý chuyến đi (Trip Management)

- Khách hàng nhập điểm đón và điểm đến.
- Lựa chọn loại xe.
- Tạo yêu cầu đặt xe.
- Theo dõi trạng thái chuyến.
- Cập nhật trạng thái chuyến:
  - Đang tìm tài xế
  - Đã nhận chuyến
  - Tài xế đã đến
  - Đã đón khách
  - Đang di chuyển
  - Hoàn thành
  - Hủy
- Xem lịch sử chuyến đi.
- Hỗ trợ xử lý các trường hợp chuyến bị lỗi.

**Đối tượng:** Khách hàng, Tài xế, Nhân viên vận hành.

---

### 4. Quản lý phân công tài xế (Driver Matching & Dispatch)

- Tìm tài xế đang sẵn sàng nhận chuyến.
- Ưu tiên tài xế phù hợp và gần khách hàng.
- Gửi yêu cầu chuyến cho tài xế.
- Tài xế chấp nhận hoặc từ chối chuyến.
- Tiếp tục tìm tài xế khác nếu tài xế không phản hồi hoặc từ chối.
- Thông báo cho khách hàng khi không tìm được tài xế.

**Đối tượng:** Khách hàng, Tài xế, Nhân viên vận hành.

---

### 5. Quản lý cước phí (Fare Management)

- Xác định số tiền khách hàng phải trả.
- Tính cước dựa trên loại dịch vụ và thông tin chuyến đi.
- Lưu thông tin cước của chuyến.
- Cung cấp số tiền cần thanh toán cho khách hàng.

**Đối tượng:** Khách hàng, Bộ phận tài chính.

> Lưu ý: Công thức tính cước cụ thể cần được khách hàng xác nhận trước khi phát triển.

---

### 6. Quản lý thanh toán (Payment Management)

- Hỗ trợ thanh toán tiền mặt.
- Hỗ trợ thanh toán điện tử.
- Tích hợp với nhà cung cấp thanh toán bên ngoài.
- Nhận kết quả giao dịch.
- Xử lý thanh toán thành công / thất bại.
- Cho phép xử lý lại giao dịch thất bại theo chính sách doanh nghiệp.
- Tra cứu lịch sử giao dịch.

**Đối tượng:** Khách hàng, Bộ phận tài chính.

---

### 7. Quản lý thông báo (Notification Management)

- Thông báo khi yêu cầu đặt xe được tiếp nhận.
- Thông báo khi tài xế nhận chuyến.
- Thông báo khi tài xế đến điểm đón.
- Thông báo khi chuyến hoàn thành.
- Thông báo kết quả thanh toán.
- Thông báo chuyến mới cho tài xế.
- Thông báo các thay đổi quan trọng của chuyến đi.

**Đối tượng:** Khách hàng, Tài xế.

---

### 8. Quản lý vận hành (Operation Management)

- Quản lý khách hàng.
- Quản lý tài xế.
- Quản lý phương tiện.
- Theo dõi các chuyến đang diễn ra.
- Theo dõi trạng thái tài xế.
- Hỗ trợ xử lý chuyến bị lỗi.
- Tra cứu lịch sử chuyến.
- Tra cứu lịch sử giao dịch.
- Phân quyền nhân viên vận hành.

**Đối tượng:** Nhân viên vận hành.

---

### 9. Quản lý đánh giá (Rating Management)

- Khách hàng đánh giá tài xế sau khi hoàn thành chuyến.
- Lưu điểm đánh giá.
- Nhân viên vận hành có thể tra cứu đánh giá.
- Sử dụng dữ liệu đánh giá để hỗ trợ theo dõi chất lượng tài xế.

**Đối tượng:** Khách hàng, Tài xế, Nhân viên vận hành.

---

### 10. Báo cáo cơ bản (Basic Reporting)

- Số lượng chuyến.
- Doanh thu.
- Tỷ lệ chuyến hoàn thành.
- Tỷ lệ chuyến hủy.
- Hiệu quả hoạt động của tài xế.

**Đối tượng:** Ban giám đốc, Nhân viên vận hành, Bộ phận tài chính.

---

## Out of Scope

Các chức năng sau chưa thực hiện trong phạm vi 7 tuần:

- AI / Machine Learning.
- AI tối ưu phân công tài xế.
- Dự đoán nhu cầu đặt xe.
- Dynamic Pricing nâng cao.
- Voucher / Khuyến mãi.
- Loyalty / Điểm thưởng.
- Báo cáo BI nâng cao.
- Các loại dịch vụ vận chuyển mới.
- Tích hợp nhiều nhà cung cấp thanh toán.
- Tích hợp nhiều nhà cung cấp thông báo.
- Các chức năng nâng cao khác chưa được khách hàng yêu cầu.

Các chức năng Out of Scope sẽ được xem xét ở giai đoạn sau khi hệ thống MVP đã hoàn thành và vận hành ổn định.
| **BG-07** | **Xây dựng nền tảng có khả năng mở rộng** | Đảm bảo hệ thống có thể phục vụ số lượng lớn khách hàng và tài xế, đồng thời dễ dàng bổ sung dịch vụ, phương thức thanh toán, kênh thông báo và tính năng mới trong tương lai. |

