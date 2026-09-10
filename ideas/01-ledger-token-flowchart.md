Dưới đây là sơ đồ dòng chảy (Flowchart) mô tả chi tiết chu kỳ tuần hoàn của **Token Sổ cái (Ledger Token)** và hệ thống các **Ví con (Sub-wallets / Child Accounts)**, vận hành dựa trên cấu trúc khép kín: *Đầu vào $\rightarrow$ Điều kiện $\rightarrow$ Đầu ra/Giá trị $\rightarrow$ Người hưởng lợi $\rightarrow$ Luồng phản hồi ngược*.

---

### Sơ Đồ Dòng Chảy: Token Sổ cái & Các Ví Con

```
 [ 1. ĐẦU VÀO (Input) ] 
   ├── Master Smart Contract & Genesis Ledger State
   └── Yêu cầu phát hành / Chuyển hướng Token từ Ví Mẹ (Parent Wallet)
           │
           ▼
 [ 2. ĐIỀU KIỆN (Conditions) ]
   ├── Xác thực Chữ ký số (Cryptographic Signature Verification)
   ├── Kiểm tra Số dư & Hạn mức phân bổ của Ví con (Sub-wallet Allowance)
   └── Đồng thuận Mạng lưới (Consensus Validation - PoS / Layer 2)
           │
           ▼
 [ 3. ĐẦU RA & GIÁ TRỊ (Outputs & Values) ]
   ├── Cập nhật trạng thái Sổ cái toàn cục (Global Ledger State Transition)
   └── Phân rã dòng Token xuống các Ví con theo cơ chế Multi-sig / Hierarchical HD
           │
           ▼
 [ 4. NGƯỜI HƯỞNG LỢI (Beneficiaries) ]
   ├── Người dùng cuối sở hữu Ví con (End-users / Sub-account Holders)
   ├── Hệ thống DApp / Microservices tự động hóa giao dịch
   └── Validator / Network Operators nhận phí giao dịch (Gas Fees)
           │
           ▼
 [ 5. LUỒNG PHẢN HỒI NGƯỢC (Feedback Loop - Đầu vào tái tạo) ]
   ├── Nhật ký lỗi giao dịch (Revert / Failed Transaction Logs) đẩy về CI/CD Guard
   ├── Biến động số dư & Độ trễ mạng (Latency/Gas Metrics) điều chỉnh Smart Contract
   └── Dữ liệu tiêu thụ của Ví con tái cấu trúc hạn mức phân bổ cho chu kỳ mới

```

---

### Chi Tiết 5 Giai Đoạn Vận Hành Dòng Chảy

#### 1. Đầu vào (Inputs)

* **Thành phần:** Trạng thái sổ cái gốc (Genesis/Current Ledger State), mã nguồn hợp đồng thông minh quản lý tài sản, và yêu cầu khởi tạo giao dịch chuyển Token từ ví chính xuống các ví con (Hierarchical Deterministic Sub-wallets).
* **Mục tiêu:** Cung cấp nguồn nguyên liệu số (Token/Value) và quy tắc định danh nguồn gốc cho dòng chảy tài chính.

#### 2. Điều kiện (Conditions)

* **Thành phần:** Hệ thống kiểm tra tính hợp lệ thông qua mật mã khóa công khai, xác thực số dư thực tế của ví mẹ, và ràng buộc chính sách phân quyền (RBAC/Smart Contract Logic) đối với từng ví con.
* **Mục tiêu:** Ngăn chặn các hành vi gian lận, chi tiêu hai lần (Double-spending) hoặc truy cập trái phép vào tầng ví con.

#### 3. Đầu ra & Giá trị (Outputs & Values)

* **Thành phần:** Giao dịch được ghi nhận vĩnh viễn trên khối (On-chain Transaction Confirmation), số dư Token được cập nhật chính xác tại ví con nhận, tạo ra giá trị thanh khoản tức thời cho các module phần mềm hoặc người dùng cuối.
* **Mục tiêu:** Hoàn tất chu trình luân chuyển tài sản từ trung tâm ra các nhánh phân tán.

#### 4. Người hưởng lợi (Beneficiaries)

* **Thành phần:** Người dùng cá nhân sở hữu ví con, các ứng dụng phi tập trung (DApp) chạy trên nền tảng, và các nút mạng (Nodes/Validators) nhận phần thưởng phí giao dịch.
* **Mục tiêu:** Tối ưu hóa trải nghiệm tài chính tốc độ cao, bảo mật và phân quyền.

#### 5. Luồng phản hồi ngược (Feedback Loop)

* **Thành phần:** Các thông số kỹ thuật phát sinh sau giao dịch (Gas usage, failed execution logs, state drift, security warnings) được thu thập tự động.
* **Mục tiêu:** Quay trở lại làm dữ liệu đầu vào để vá lỗi hợp đồng thông minh, tối ưu hóa thuật toán định tuyến giao dịch cho các ví con trong các chu kỳ tiếp theo.