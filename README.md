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


## Phạm vi MVP trong 7 tuần

Trong thời gian 7 tuần, dự án tập trung xây dựng **MVP (Minimum Viable Product)** với các chức năng cốt lõi để hệ thống CAB có thể vận hành đầy đủ quy trình:

**Đăng ký → Đăng nhập → Đặt xe → Tìm tài xế → Thực hiện chuyến → Tính cước → Thanh toán → Đánh giá**

## MVP Scope

| Module | Chức năng MVP | Mức độ |
|---|---|---|
| **Quản lý người dùng** | Đăng ký tài khoản | Must Have |
| | Đăng nhập / đăng xuất | Must Have |
| | Cập nhật thông tin cá nhân | Must Have |
| | Xác thực người dùng | Must Have |
| | Phân quyền cơ bản | Must Have |
| **Quản lý tài xế** | Quản lý thông tin tài xế | Must Have |
| | Quản lý thông tin phương tiện | Must Have |
| | Bật / tắt trạng thái sẵn sàng nhận chuyến | Must Have |
| | Cập nhật trạng thái hoạt động | Must Have |
| | Ghi nhận vị trí tài xế | Must Have |
| **Quản lý chuyến đi** | Nhập điểm đón và điểm đến | Must Have |
| | Lựa chọn loại xe | Must Have |
| | Tạo yêu cầu đặt xe | Must Have |
| | Theo dõi trạng thái chuyến | Must Have |
| | Cập nhật trạng thái chuyến | Must Have |
| | Xem lịch sử chuyến đi | Must Have |
| | Hủy chuyến | Should Have |
| **Phân công tài xế** | Tìm tài xế đang sẵn sàng | Must Have |
| | Ưu tiên tài xế phù hợp và gần khách hàng | Must Have |
| | Gửi yêu cầu chuyến cho tài xế | Must Have |
| | Tài xế chấp nhận / từ chối chuyến | Must Have |
| | Tìm tài xế khác khi bị từ chối / không phản hồi | Must Have |
| | Thông báo khi không tìm được tài xế | Must Have |
| **Quản lý cước** | Tính cước chuyến đi | Must Have |
| | Xác định số tiền khách hàng phải trả | Must Have |
| | Lưu thông tin cước | Must Have |
| **Thanh toán** | Thanh toán tiền mặt | Must Have |
| | Thanh toán điện tử | Must Have |
| | Tích hợp một nhà cung cấp thanh toán | Must Have |
| | Ghi nhận kết quả thanh toán | Must Have |
| | Xử lý thanh toán thất bại | Should Have |
| **Thông báo** | Thông báo tiếp nhận yêu cầu đặt xe | Must Have |
| | Thông báo tài xế nhận chuyến | Must Have |
| | Thông báo tài xế đến điểm đón | Must Have |
| | Thông báo hoàn thành chuyến | Must Have |
| | Thông báo kết quả thanh toán | Must Have |
| | Thông báo chuyến mới cho tài xế | Must Have |
| **Quản lý vận hành** | Quản lý khách hàng | Must Have |
| | Quản lý tài xế và phương tiện | Must Have |
| | Theo dõi chuyến đang diễn ra | Must Have |
| | Theo dõi trạng thái tài xế | Must Have |
| | Xử lý chuyến bị lỗi | Must Have |
| | Tra cứu lịch sử chuyến | Should Have |
| | Tra cứu lịch sử giao dịch | Should Have |
| **Đánh giá** | Khách hàng đánh giá tài xế sau chuyến | Must Have |
| | Lưu kết quả đánh giá | Must Have |
| **Báo cáo** | Báo cáo số lượng chuyến | Should Have |
| | Báo cáo doanh thu | Should Have |
| | Báo cáo tỷ lệ hoàn thành / hủy | Should Have |
| | Báo cáo hiệu quả tài xế | Could Have |
| **Bảo mật & Quản trị** | Xác thực người dùng | Must Have |
| | Phân quyền người dùng theo vai trò | Must Have |
| | Bảo vệ thông tin cá nhân và dữ liệu giao dịch | Must Have |
| | Không lưu trực tiếp thông tin nhạy cảm của thẻ / tài khoản thanh toán | Must Have |
| | Lưu vết các thao tác quản trị quan trọng | Should Have |


# B5. Chuyển các yêu cầu thành yêu cầu nghiệp vụ

### 1. Quản lý người dùng

| ID | Yêu cầu nghiệp vụ | Mức độ |
|---|---|---|
| BR-01 | Người dùng có thể đăng ký, đăng nhập, đăng xuất và cập nhật thông tin tài khoản. | Must Have |
| BR-02 | Hệ thống có thể xác thực người dùng trước khi sử dụng các chức năng yêu cầu tài khoản. | Must Have |
| BR-03 | Hệ thống có thể phân quyền người dùng theo vai trò. | Must Have |

### 2. Quản lý tài xế

| ID | Yêu cầu nghiệp vụ | Mức độ |
|---|---|---|
| BR-04 | Hệ thống cho phép quản lý thông tin tài xế và phương tiện. | Must Have |
| BR-05 | Tài xế có thể bật hoặc tắt trạng thái sẵn sàng và cập nhật trạng thái hoạt động. | Must Have |
| BR-06 | Hệ thống có thể ghi nhận vị trí hiện tại của tài xế. | Must Have |

### 3. Quản lý chuyến đi

| ID | Yêu cầu nghiệp vụ | Mức độ |
|---|---|---|
| BR-07 | Khách hàng có thể nhập điểm đón, điểm đến và lựa chọn loại xe khi đặt xe. | Must Have |
| BR-08 | Khách hàng có thể tạo yêu cầu đặt xe. | Must Have |
| BR-09 | Khách hàng có thể theo dõi trạng thái chuyến đi. | Must Have |
| BR-10 | Tài xế có thể cập nhật trạng thái chuyến đi trong quá trình thực hiện chuyến. | Must Have |
| BR-11 | Khách hàng có thể xem lịch sử chuyến đi. | Must Have |
| BR-12 | Khách hàng có thể hủy chuyến theo chính sách của doanh nghiệp. | Should Have |

### 4. Phân công tài xế

| ID | Yêu cầu nghiệp vụ | Mức độ |
|---|---|---|
| BR-13 | Hệ thống tự động tìm và ưu tiên tài xế phù hợp, gần khách hàng và đang sẵn sàng nhận chuyến. | Must Have |
| BR-14 | Hệ thống gửi yêu cầu chuyến đến tài xế phù hợp và cho phép tài xế chấp nhận hoặc từ chối chuyến. | Must Have |
| BR-15 | Hệ thống tiếp tục tìm tài xế khác khi tài xế từ chối hoặc không phản hồi. | Must Have |
| BR-16 | Hệ thống thông báo cho khách hàng khi không tìm được tài xế. | Must Have |

### 5. Quản lý cước

| ID | Yêu cầu nghiệp vụ | Mức độ |
|---|---|---|
| BR-17 | Hệ thống có thể tính cước dựa trên loại dịch vụ và thông tin chuyến đi. | Must Have |
| BR-18 | Hệ thống xác định và lưu số tiền khách hàng phải thanh toán. | Must Have |

> **Lưu ý:** Công thức tính cước cụ thể cần được khách hàng xác nhận trước khi triển khai.

### 6. Thanh toán

| ID | Yêu cầu nghiệp vụ | Mức độ |
|---|---|---|
| BR-19 | Khách hàng có thể thanh toán bằng tiền mặt hoặc phương thức điện tử. | Must Have |
| BR-20 | Hệ thống tích hợp với một nhà cung cấp thanh toán bên ngoài để xử lý giao dịch điện tử. | Must Have |
| BR-21 | Hệ thống ghi nhận kết quả giao dịch thanh toán. | Must Have |
| BR-22 | Hệ thống hỗ trợ xử lý lại giao dịch thanh toán thất bại theo chính sách doanh nghiệp. | Should Have |

### 7. Thông báo

| ID | Yêu cầu nghiệp vụ | Mức độ |
|---|---|---|
| BR-23 | Hệ thống thông báo cho khách hàng về các sự kiện quan trọng của chuyến đi như tiếp nhận yêu cầu, tài xế nhận chuyến, tài xế đến điểm đón và hoàn thành chuyến. | Must Have |
| BR-24 | Hệ thống thông báo cho khách hàng về kết quả thanh toán. | Must Have |
| BR-25 | Hệ thống thông báo cho tài xế khi có chuyến mới hoặc thay đổi quan trọng liên quan đến chuyến. | Must Have |

### 8. Quản lý vận hành

| ID | Yêu cầu nghiệp vụ | Mức độ |
|---|---|---|
| BR-26 | Nhân viên vận hành có thể quản lý thông tin khách hàng, tài xế và phương tiện. | Must Have |
| BR-27 | Nhân viên vận hành có thể theo dõi các chuyến đang diễn ra và trạng thái tài xế. | Must Have |
| BR-28 | Nhân viên vận hành có thể xử lý các chuyến bị lỗi. | Must Have |
| BR-29 | Nhân viên vận hành có thể tra cứu lịch sử chuyến đi và giao dịch. | Should Have |

### 9. Đánh giá

| ID | Yêu cầu nghiệp vụ | Mức độ |
|---|---|---|
| BR-30 | Khách hàng có thể đánh giá tài xế sau khi hoàn thành chuyến. | Must Have |
| BR-31 | Hệ thống lưu kết quả đánh giá để phục vụ theo dõi chất lượng dịch vụ. | Must Have |

### 10. Báo cáo

| ID | Yêu cầu nghiệp vụ | Mức độ |
|---|---|---|
| BR-32 | Hệ thống cung cấp báo cáo về số lượng chuyến đi. | Should Have |
| BR-33 | Hệ thống cung cấp báo cáo về doanh thu. | Should Have |
| BR-34 | Hệ thống cung cấp báo cáo về tỷ lệ chuyến hoàn thành và tỷ lệ chuyến hủy. | Should Have |
| BR-35 | Hệ thống cung cấp báo cáo về hiệu quả hoạt động của tài xế. | Could Have |

### 11. Bảo mật & Quản trị

| ID | Yêu cầu nghiệp vụ | Mức độ |
|---|---|---|
| BR-36 | Hệ thống kiểm soát quyền truy cập theo vai trò người dùng. | Must Have |
| BR-37 | Hệ thống bảo vệ thông tin cá nhân, thông tin phương tiện và dữ liệu vị trí. | Must Have |
| BR-38 | Hệ thống bảo vệ dữ liệu giao dịch và thông tin thanh toán. | Must Have |
| BR-39 | Hệ thống không lưu trực tiếp thông tin nhạy cảm của thẻ hoặc tài khoản thanh toán. | Must Have |
| BR-40 | Hệ thống lưu vết các thao tác quản trị quan trọng để phục vụ kiểm tra và xử lý sự cố. | Should Have |
