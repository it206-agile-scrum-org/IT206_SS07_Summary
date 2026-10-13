# Integrated Sprint Planning & Tracking Pack – CampusFood

*Sprint 10 ngày · Đội: Lan (FE), Minh (BE), Ngọc (QA/BA), Phúc (Tích hợp) · Các số liệu lấy từ đề bài; giả định ghi rõ ở từng phần.*

## 1. Biên bản ước lượng (Planning Poker, thang 1-2-3-5-8-13)

Nguyên tắc: không lấy trung bình, không ép số, không đổi SP sang giờ; PO không tự chốt SP. Phiếu lệch được giải quyết bằng thảo luận giả định, rồi bỏ phiếu lại.

| PBI | Phiếu | Phân loại | Căn cứ | Hành động |
| --- | --- | --- | --- | --- |
| CF03 Chọn điểm nhận | 3/5/5/8 | **Cần thảo luận lại** | Có thể có 2 giả định khác nhau: phiếu 3 hiểu chỉ trong trường, phiếu 8 tính cả ngoài trường. Quy tắc ngoài trường chưa có, nên 5 chưa phải đồng thuận thật. | Người ra 3 và 8 nêu giả định. **Tách** CF03a (điểm nhận trong trường) để bỏ phiếu lại; CF03b (ngoài trường) chờ PO cung cấp quy tắc (vùng, phí, thời gian). |
| CF04 Nhận đơn/cập nhật giao | 5/8/8/13 | **Cần thảo luận lại** | Số đông 8 nhưng chênh 5↔13 lớn. Phiếu 13 có thể thấy rủi ro phụ thuộc CF02, CF03, vòng đời trạng thái, thông báo; phiếu 5 có thể chỉ tính cập nhật trạng thái. Số phiếu nhiều không thay cho đồng thuận. | Nghe phiếu 5 và 13 giải thích; bỏ phiếu lại. Đề xuất **tách** "nhận đơn" và "cập nhật giao". |
| CF06 Thanh toán QR | 5/8/13/13 | **Thiếu dữ liệu** | Phiếu trải từ 5 đến 13, chưa có SLA cổng QR (thời gian phản hồi, timeout, callback, giới hạn). Không đủ thông tin để bàn tiếp bằng số. | **Spike** có giới hạn thời gian (Ngày 1-2) do Phúc và Minh làm, đầu ra là ghi chú SLA 1 trang; sau đó bỏ phiếu lại và tách theo kết quả. |
| CF08 Hoàn tiền quán hủy | 13 (tạm chốt) | **Thiếu dữ liệu** | Chưa có Acceptance Criteria; "tạm chốt" không bằng chốt. 13 là mức lớn nhất, gần cả Sprint, lại phụ thuộc thanh toán. | **Refine**: viết AC (ai hủy, hoàn toàn phần hay một phần, thời hạn, đối soát), **tách**, rồi poker lại. Không đưa vào Sprint này. |

Các PBI đã chốt: CF01 = 3, CF02 = 5, CF05 = 5, CF07 = 3, CF09 = 3. Lưu ý CF09 đã có số nhưng thiếu quy tắc sửa/xóa, nên chưa Ready.

## 2. Sprint Goal, Sprint Backlog và DoD

**Sprint Goal:** *Sinh viên có thể xem món còn, tạo đơn có mã xác nhận, thanh toán bằng QR và nhận món tại quầy bằng mã ở một căn tin, đủ an toàn (có xử lý lỗi chính) để chạy thử có kiểm soát.*

**Sprint Backlog (dự báo 16 SP, trần ngân sách):**

| PBI | SP | Trạng thái | Lý do |
| --- | --- | --- | --- |
| CF01 Xem thực đơn/còn món | 3 | Cam kết | Ưu tiên 1, Ready, là đầu luồng. |
| CF02 Tạo đơn/mã xác nhận | 5 | Cam kết | Ưu tiên 2, Ready sau CF01, cho ra mã xác nhận dùng khi nhận món. |
| CF06 Thanh toán QR (lát cắt) | ≤ 8 | **Cam kết có điều kiện** | Bắt buộc có cho Goal "đặt - thanh toán". Chỉ nhận phần ≤ 8 SP sau spike và poker lại. Nếu vượt, tách và đẩy phần còn lại sang Sprint sau. 8 là trần ngân sách, không phải kết quả ước lượng. |
| CF07 Biên nhận điện tử | 3 | **Dự phòng** | Chỉ làm nếu CF06 xong đúng tiến độ trước Ngày 7 và Minh không bị nghẽn. |

**Không chọn:** CF03/CF04/CF05 (giao tận nơi: CF03 thiếu quy tắc, CF04 chưa chốt SP và phụ thuộc CF03, CF05 phụ thuộc CF04); CF08 (thiếu AC, quá lớn, phụ thuộc CF06); CF09 (thiếu quy tắc, không cần cho luồng thử). Phạm vi nhận món là "nhận tại quầy bằng mã" nên luồng vẫn dùng thử được mà không cần giao.

**DoD:** (1) đạt Acceptance Criteria; (2) đã review; (3) đã kiểm thử luồng chính và luồng lỗi; (4) đã lên môi trường thử; (5) không còn lỗi nghiêm trọng. PBI chưa đủ 5 điều là chưa Done và không tính SP.

## 3. Capacity trước và sau biến động

| Thành viên | Ngày × giờ | Gián đoạn | Capacity (giờ) |
| --- | --- | --- | --- |
| Lan | 10 × 6 = 60 | −6 (hỗ trợ) | **54** |
| Minh | 8 × 6 = 48 | 0 | **48** |
| Ngọc | 10 × 5 = 50 | −5 (họp) | **45** |
| Phúc | 9 × 6 = 54 | −8 (tích hợp cũ) | **46** |
| **Toàn đội** |  |  | **193** |

**Sau khi Minh nghỉ thêm 2 ngày** (giả định: 8 ngày đã là số ngày làm được, nay còn 6): Minh = 6 × 6 = **36 giờ** (−12 giờ, giảm 25% của riêng anh), toàn đội = **181 giờ** (giảm khoảng 6%).

**Tác động:** Minh là điểm nghẽn backend của cả CF02 và CF06. Hệ quả: (1) bỏ CF07 khỏi cam kết, giữ ở dạng dự phòng; (2) Phúc nhận phần callback/đối soát cổng QR; (3) Lan dùng mock API để không chờ backend; (4) CF06 chỉ nhận lát cắt ≤ 8 SP. Capacity chỉ dùng để kiểm tra khả thi, không quy đổi từ SP.

## 4. Task Breakdown (3 PBI)

**CF01 – Xem thực đơn/còn món**

| Task | Người | Đầu ra | Phụ thuộc / phối hợp |
| --- | --- | --- | --- |
| T1 Làm rõ AC và dữ liệu món | Ngọc | AC + test case | Hỏi PO; trao đổi với Lan, Minh |
| T2 Xây API danh sách món và tồn | Minh | Endpoint + tài liệu hợp đồng API | Sau T1; Lan dùng làm mock |
| T3 Dựng màn hình thực đơn (còn/hết) | Lan | Màn hình chạy với mock | Song song T2 |
| T4 Kiểm thử luồng chính/lỗi (hết món, mất mạng) | Ngọc | Báo cáo kiểm thử | Sau T2, T3 |
| T5 Đưa lên môi trường thử | Phúc | Bản triển khai | Sau T4 |

**CF02 – Tạo đơn/mã xác nhận**

| Task | Người | Đầu ra | Phụ thuộc / phối hợp |
| --- | --- | --- | --- |
| T6 Viết AC tạo đơn và quy tắc mã xác nhận | Ngọc | AC (mã duy nhất, hết hạn) | Sau T1 |
| T7 Xây API tạo đơn, kiểm tồn, sinh mã | Minh | Endpoint + test đơn vị | Sau T2; chống tạo trùng đơn |
| T8 Dựng giỏ hàng và màn xác nhận đơn | Lan | Màn hình giỏ và mã | Dùng hợp đồng T7 |
| T9 Tích hợp giỏ - API, kiểm thử đơn đồng thời món cuối | Phúc + Ngọc | Báo cáo tích hợp | Sau T7, T8 |

**CF06 – Thanh toán QR (lát cắt)**

| Task | Người | Đầu ra | Phụ thuộc / phối hợp |
| --- | --- | --- | --- |
| T10 Làm spike SLA cổng QR (sandbox, timeout, callback) | Phúc + Minh | Ghi chú SLA 1 trang, hạn Ngày 2 | Không; kết quả quyết định phạm vi |
| T11 Poker lại và tách CF06 | Cả đội | PBI đã tách, SP mới | Sau T10 |
| T12 Xây tạo giao dịch QR và nhận callback idempotent | Minh | Endpoint + test | Sau T10, T7 |
| T13 Dựng màn hình QR, đếm ngược, trạng thái | Lan | Màn hình thanh toán | Dùng hợp đồng T12 |
| T14 Tích hợp sandbox và đối soát giao dịch | Phúc | Báo cáo đối soát | Sau T12 |
| T15 Kiểm thử đúng/sai/hết hạn/trả chậm | Ngọc | Báo cáo kiểm thử | Sau T12-T14 |

## 5. Velocity và quyết định phạm vi

**Velocity:** Sprint 3 = 18, Sprint 4 = 21, Sprint 5 = **15 SP**. Trung bình 3 Sprint = 18 SP; khoảng 15-21. Xu hướng: tăng rồi giảm 6 SP (khoảng −29%), chưa ổn định. PBI 8 SP mới hoàn thành 75% không được tính; nếu tính sẽ thành 23 và che mất vấn đề. Dự báo hợp lý: 15-18 SP, nghiêng về cận dưới vì Capacity giảm.

**Hai phương án:**

- **A (chủ yếu Velocity):** lấy theo ưu tiên đến mức Velocity cao, giả định SP tạm CF03 = 5, CF04 = 8: CF01 + CF02 + CF03 + CF04 = **21 SP**.
- **B (Capacity, sẵn sàng, rủi ro):** CF01 + CF02 + CF06 lát cắt ≤ 8 = **16 SP**, CF07 dự phòng.

| Tiêu chí | A | B |
| --- | --- | --- |
| Tin cậy | Thấp: 21 bằng mức cao nhất từng đạt; CF03/CF04 chưa chốt SP | Cao hơn: 16 nằm trong khoảng 15-18, 2 PBI đã chốt |
| Nghỉ/gián đoạn | Không chịu được việc Minh nghỉ (còn 181 giờ) | Có đệm; dự phòng CF07 bỏ được |
| Bảo vệ Goal | Không có thanh toán, không đạt Goal; CF03 thiếu quy tắc | Đủ xem - đặt - thanh toán - nhận tại quầy |
| Áp lực/gaming | Cao: dễ đổ dồn cuối Sprint, đóng PBI chưa qua kiểm thử | Thấp hơn, dự phòng rõ |

**Quyết định: chọn B.** Giả định: nhận tại quầy bằng mã chấp nhận được cho lần dùng thử; spike hoàn tất trước hết Ngày 2; cổng QR có sandbox.

## 6. Burndown và thích nghi

Số liệu thực tế là của đề bài, bắt đầu ở 21 SP; đường lý tưởng giảm đều 2,1 SP/ngày. (Biểu đồ này là chuỗi mẫu để tập đọc tín hiệu, không phải cam kết 21 SP của phương án B.)

| Ngày | Lý tưởng | Thực tế | Chênh | Thực tế (█ = 1 SP) |
| --- | --- | --- | --- | --- |
| 0 | 21 | 21 | 0 | █████████████████████ |
| 1 | 18,9 | 21 | +2,1 | █████████████████████ |
| 2 | 16,8 | 18 | +1,2 | ██████████████████ |
| 3 | 14,7 | 18 | +3,3 | ██████████████████ |
| 4 | 12,6 | 23 | +10,4 | █████████████████████████ |
| 5 | 10,5 | 18 | +7,5 | ██████████████████ |
| 6 | 8,4 | 18 | +9,6 | ██████████████████ |
| 7 | 6,3 | 13 | +6,7 | █████████████ |
| 8 | 4,2 | 8 | +3,8 | ████████ |
| 9 | 2,1 | 5 | +2,9 | █████ |
| 10 | 0 | 5 | +5 | █████ |

**Đọc tín hiệu (giả thuyết và dữ liệu cần kiểm tra):**

| Tín hiệu | Giả thuyết | Dữ liệu cần kiểm tra |
| --- | --- | --- |
| Ngày 4: tăng 18 → 23 (+5) | Phạm vi tăng do PO thêm mã khuyến mãi 5 SP, chưa qua poker, ngay giữa Sprint | Lịch sử Sprint Backlog; ai chấp nhận; có đánh giá tác động lên Goal không |
| Ngày 5: giảm 23 → 18 (−5) đúng bằng mã khuyến mãi, cùng ngày cổng QR chậm | Có thể mã khuyến mãi bị rút khỏi Sprint chứ không phải 5 SP hoàn thành thật; hoặc hoàn thành quá nhanh trong lúc QR đang nghẽn | Thẻ nào chuyển Done ngày 5; PBI nào bị gỡ; kết quả kiểm thử |
| Ngày 3 và Ngày 6 đứng yên; Ngày 6 họp không ghi quyết định | Họp ăn Capacity và không có quyết định gỡ nghẽn; nghẽn QR còn đó | Nhật ký Daily/họp; thời gian Lan, Ngọc, Phúc bị gián đoạn; task nào Blocked |
| Ngày 7-9: giảm 13 → 5 dồn cuối | Công việc dồn cuối, có nguy cơ đóng thẻ vội, bỏ bước kiểm thử | Thời điểm bắt đầu kiểm thử từng PBI; PBI Done có đủ DoD không |
| Ngày 10: còn 5 SP | Phần còn lại có thể liên quan QR hoặc kiểm thử | Mô tả 5 SP còn lại, lý do chưa Done |

**Đề xuất thích nghi:** (1) Ngày 4: PO, đội cùng đánh giá mã khuyến mãi (poker, tác động Goal) rồi mới quyết định; mặc định đưa vào Product Backlog. (2) Khi QR chậm: nêu nghẽn tại Daily, gọi cổng QR, cắt phạm vi QR về lát cắt tối thiểu. (3) Mọi cuộc họp ghi quyết định, người chịu trách nhiệm, hạn. (4) Không sửa lịch sử biểu đồ: giữ nguyên điểm Ngày 4-5, chú thích bằng lý do. (5) Phần chưa đạt DoD không tính Velocity.

## 7. Bảng xử lý ngoại lệ

| Tình huống | Xử lý | Tác động Goal / DoD | Velocity / Burndown | Công khai |
| --- | --- | --- | --- | --- |
| **QR lỗi sau khi tạo đơn** | Giữ đơn ở "Chờ thanh toán" có hạn; cho tạo lại QR; callback idempotent; đối soát với cổng; hết hạn thì hủy đơn và nhả món | Là luồng lỗi bắt buộc theo DoD; nếu không xử lý, Goal "đủ an toàn" không đạt | Làm trong CF06, không thêm SP; nếu vượt thì tách task, hiện trên bảng | Demo luồng lỗi tại Review; ghi giả định SLA |
| **Thiếu SĐT / điểm ngoài trường** | Chặn bước đặt đơn với thông báo rõ; ngoài trường: từ chối "chưa hỗ trợ" chứ không thử đoán; hỏi PO quy tắc | Giữ Goal (nhận tại quầy trong trường); CF03b nằm ngoài Sprint; AC có thêm ca lỗi | Không đổi SP; CF03b vào Product Backlog | Ghi câu hỏi mở cho PO; nêu tại Review |
| **PO thêm 5 SP** | Không nhận ngầm. PO không tự đặt SP: đội poker và đánh giá Ready; chỉ đổi lấy phần dự phòng (CF07) nếu Goal không bị ảnh hưởng; nếu không thì vào Product Backlog | Bảo vệ Goal; nếu Goal bị đe dọa thì PO và đội thương lượng phạm vi, không hạ DoD | Nếu nhận, đường Burndown tăng và ghi chú lý do; Velocity chỉ tính khi Done | Ghi quyết định và lý do trên bảng Sprint; trình bày tại Review |
| **PBI mới 80% chưa qua kiểm thử** | Không Done: không có điểm cho 80%. Chạy kiểm thử trong Sprint nếu còn thời gian; không thì chuyển sang Sprint sau, ước lượng lại phần còn lại | DoD giữ nguyên; nếu là PBI lõi thì Goal có nguy cơ, báo PO sớm | Velocity tính 0 SP; Burndown giữ nguyên SP của PBI | Trình bày ở Review là "chưa Done" và nêu việc còn lại; không demo như hoàn tất |

## 8. Giả định và rủi ro chính

- Nhận tại quầy bằng mã chấp nhận được cho bản dùng thử; giao tận nơi để Sprint sau.
- Minh nghỉ thêm 2 ngày; Phúc còn 8 giờ tích hợp cũ chưa giải quyết.
- Cổng QR có sandbox; nếu SLA chậm hoặc không có, cắt CF06 về lát cắt tối thiểu.
- Theo dõi: Burndown hằng ngày, số task Blocked, chênh so với đường lý tưởng; trên 3 SP trong 2 ngày liên tiếp thì họp thích nghi và ghi quyết định.
