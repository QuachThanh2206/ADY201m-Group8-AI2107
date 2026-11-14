# ADY201m | Olist Freight Prediction

**FPT University · Group 2 · AI2107**

Dự án phân tích dữ liệu thương mại điện tử Olist (Brazil) và xây dựng mô hình **dự đoán phí vận chuyển (`freight_value`, đơn vị BRL)** ở cấp sản phẩm trong đơn hàng. Mục tiêu là nhận diện các yếu tố liên quan đến phí vận chuyển và hỗ trợ người bán ước tính chi phí.

## Mục tiêu và phương pháp

- **Dữ liệu:** Bộ dữ liệu Olist gồm 9 bảng liên quan đến đơn hàng, sản phẩm, khách hàng, người bán và vị trí địa lý.
- **Xử lý:** Kiểm tra chất lượng dữ liệu, làm sạch, kết hợp bảng và xây dựng đặc trưng.
- **Phân tích:** Sử dụng SQL và EDA để tìm hiểu phân phối, chênh lệch và các yếu tố liên quan đến `freight_value`.
- **Dự đoán:** So sánh Linear Regression và Random Forest; đánh giá bằng MAE, RMSE và R².

## Thành viên và phân công

| Thành viên | MSSV | Phụ trách | Tỷ trọng phân công |
|---|---|---|---|
| **Kiều Đại Dương** | HE201928 | Data Understanding, phân tích SQL, tổng hợp câu hỏi và kết quả kinh doanh | ~35% |
| **Trần Chí Kiên** | HE200774 | Data Cleaning, Data Preparation và mô hình Random Forest và đánh giá, so sánh mô hình | ~35% |
| **Quách Xuân Thành** | HE204852 | EDA, Visualization, mô hình Linear Regression và đánh giá, so sánh mô hình | ~30% |

Ba thành viên cùng rà soát kết quả, hoàn thiện báo cáo, slide và chuẩn bị bảo vệ. Tỷ trọng trên là **phân công công việc của nhóm**

## Quy trình thực hiện

1. **Problem & Data Understanding:** Xác định bài toán, kiểm tra cấu trúc và chất lượng các bảng dữ liệu.
2. **Data Cleaning & Preparation:** Xử lý dữ liệu, ghép bảng và tạo tập dữ liệu phục vụ phân tích.
3. **SQL Analysis:** Truy vấn và tổng hợp các chỉ số liên quan đến phí vận chuyển.
4. **Exploratory Data Analysis (EDA):** Phân tích phân phối, ngoại lệ, mối quan hệ và rút ra nhận xét.
5. **Modeling & Evaluation:** Huấn luyện, so sánh mô hình hồi quy và đánh giá sai số dự đoán.

## Cấu trúc repository

```text
ADY201m-Group8-AI2107/
├── data/        # Dữ liệu gốc và dữ liệu sau xử lý
├── notebooks/   # Notebook xử lý, SQL, EDA và Modeling
├── report/      # Báo cáo dự án
├── slide/       # Slide thuyết trình
└── README.md    # Giới thiệu và hướng dẫn
```

## Nguyên tắc thực hiện

- Không thay đổi trực tiếp dữ liệu gốc; ghi rõ lý do và số lượng bản ghi bị ảnh hưởng khi làm sạch.
- Kiểm tra khóa và số dòng trước/sau khi ghép dữ liệu; phân biệt cấp đơn hàng với cấp sản phẩm.
- Tránh sử dụng dữ liệu phát sinh sau thời điểm dự đoán làm đầu vào mô hình; báo cáo kết quả trên dữ liệu đánh giá riêng.

**Nguồn dữ liệu:** [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce).
