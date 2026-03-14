# Tóm tắt Nghiên cứu Khoa học Sinh viên

## Thông tin chung

| Mục | Nội dung |
|-----|----------|
| **Tên đề tài** | Phân tích mạch máu võng mạc nâng cao có sử dụng Deep Learning để phân đoạn ảnh có độ phân giải cao |
| **Mã đề tài** | SV2025-164 |
| **Chủ nhiệm** | Nguyễn Nhật Phát (MSSV: 23110053) |
| **Thành viên** | Huỳnh Gia Hân, Bùi Trần Tấn Phát, Trần Huỳnh Xuân Thanh |
| **Người hướng dẫn** | PGS.TS. Hoàng Văn Dũng |
| **Đơn vị** | Khoa Đào tạo Quốc tế – ĐH Sư phạm Kỹ thuật TP.HCM |
| **Thời gian** | 06/2025 |

---

## Vấn đề nghiên cứu

Phân đoạn mạch máu võng mạc là bước quan trọng trong chẩn đoán sớm các bệnh lý về mắt như **tiểu đường (Diabetic Retinopathy)** và **Glaucoma**. Thách thức cốt lõi là các mạch máu nhỏ và siêu nhỏ (1–2 pixel) thường bị bỏ sót bởi các phương pháp truyền thống, đặc biệt khi xử lý ảnh độ phân giải cao mà không làm giảm kích thước ảnh gốc.

---

## Điểm mới và sáng tạo

1. **Quy trình huấn luyện tuần tự 4 giai đoạn (Sequential 4-Phase Training)**
   Mô hình học từ dữ liệu độ phân giải thấp (DRIVE) → nâng cao xử lý ảnh độ phân giải cao (HRF) → tối ưu hóa chuyển giao tri thức.

2. **Kỹ thuật patch-based thông minh**
   Phân đoạn ảnh độ phân giải cực cao mà không cần giảm kích thước, bảo toàn toàn bộ chi tiết mao mạch nhỏ, không bị giới hạn bởi bộ nhớ GPU.

3. **Kiến trúc lai UNet++ + EfficientNet-B4**
   Kết hợp UNet++ decoder với EfficientNet-B4 encoder (pre-trained từ ImageNet), tạo hybrid model ~19.3M tham số, tích hợp **FOV-aware loss** giúp giảm nhiễu và tăng độ chính xác.

---

## Dữ liệu sử dụng

| Tập dữ liệu | Đặc điểm |
|-------------|----------|
| **DRIVE** | Digital Retinal Images for Vessel Extraction – độ phân giải thấp, dùng để huấn luyện nền |
| **HRF** | High-Resolution Fundus – độ phân giải cao, gồm 3 nhóm: Diabetic Retinopathy (DR), Glaucoma (G), Healthy (H) |

---

## Kết quả đạt được

Trên tập **HRF** (độ phân giải cao):

| Chỉ số | Giá trị |
|--------|---------|
| Accuracy | 0.9642 ± 0.0048 |
| Precision | 0.7455 ± 0.0729 |
| Recall | 0.8031 ± 0.0411 |
| F1-Score / Dice | 0.7710 ± 0.0447 |
| IoU | 0.6295 ± 0.0600 |

Kết quả vượt trội so với các nghiên cứu trước trong bài toán phân đoạn mạch máu võng mạc trên ảnh độ phân giải cao.

---

## Ý nghĩa ứng dụng

- Hỗ trợ **phát hiện sớm** bệnh lý võng mạc (tiểu đường, Glaucoma).
- Tiềm năng triển khai trong **sàng lọc diện rộng** tại các cơ sở y tế.
- Đóng góp vào **giáo dục y tế** và giảm gánh nặng cho hệ thống y tế.

---

## Hạn chế và hướng phát triển

- Hiệu suất trên mạch máu siêu nhỏ vẫn còn dư địa cải thiện.
- Có thể mở rộng tích hợp kiến trúc **Transformer** (ViT, TransUNet) để nắm bắt quan hệ tầm xa trong cấu trúc mạch máu.
- Tiềm năng áp dụng **federated learning** để huấn luyện đa bệnh viện mà không vi phạm quyền riêng tư dữ liệu bệnh nhân.
