# ADY201m - Olist Freight Prediction

Đây là project ADY201m của nhóm mình, sử dụng dữ liệu Olist để tìm hiểu các yếu tố ảnh hưởng đến phí vận chuyển (`freight_value`) và hướng tới xây dựng mô hình dự đoán.

Hiện tại nhóm đang làm **bản cơ bản (v0)** để cả 3 cùng chạy được code, hiểu cách xử lý dữ liệu rồi mới làm sâu hơn. Đây chưa phải bản final.

## Thành viên

| Họ và tên | MSSV | Phụ trách chính |
| --- | --- | --- |
| Kiều Đại Dương | HE201928 | SQL |
| Trần Chí Kiên | HE200774 | Data Cleaning |
| Quách Xuân Thành | HE204852 | EDA |

## Sơ đồ thư mục
ADY201m-Group8-AI2107/
│
├── data/
│   ├── raw/                           
│   │   ├── olist_orders_dataset.csv
│   │   ├── olist_order_items_dataset.csv
│   │   ├── olist_customers_dataset.csv
│   │   ├── olist_products_dataset.csv
│   │   ├── olist_sellers_dataset.csv
│   │   ├── olist_geolocation_dataset.csv
│   │   ├── olist_order_payments_dataset.csv
│   │   ├── olist_order_reviews_dataset.csv
│   │   └── product_category_name_translation.csv
│   │
│   └── claend/                    
│       └── olist_clean.csv
├── notebooks/
│   ├── 01_Problem_Definition.ipynb
│   ├── 02_Data_Understanding.ipynb
│   ├── 03_Data_Cleaning.ipynb
│   ├── 04_SQL_Analysis.ipynb
│   └── 05_EDA.ipynb
|
└── README.md

## Giải thích cấu trúc dự án

| Thành phần | Nội dung thực hiện | Kết quả mong đợi |
|---|---|---|
| **01. Problem Definition** | Xác định bài toán, mục tiêu, người dùng cuối, phạm vi, câu hỏi kinh doanh và metric đánh giá. | Bài toán được định nghĩa rõ ràng. |
| **02. Data Understanding** | Khám phá 9 bảng, kiểm tra khóa, thiếu, trùng, giá trị bất thường và tính hợp lệ. Ghi nhận bằng chứng và đề xuất hướng xử lý. | Data Quality Report + Decision Log. |
| **03. Data Cleaning** | Chọn dữ liệu, chuẩn hóa, xử lý lỗi, merge, kiểm tra sau merge và review. Ghi lại các quyết định xử lý. | Dataset sạch + Cleaning Audit Log. |
| **04. SQL Analysis** | Truy vấn, JOIN, GROUP BY, tổng hợp dữ liệu và phân tích các câu hỏi kinh doanh bằng SQL. | Kết quả truy vấn và bảng thống kê. |
| **05. EDA** | Phân tích phân phối `freight_value`, outliers, tương quan, các yếu tố ảnh hưởng và kiểm tra giả thuyết. | Biểu đồ + Insights + đề xuất đặc trưng cho ML. |


## Workflow

**Problem Definition → Data Understanding → Data Cleaning → SQL Analysis → EDA**

### Nguyên tắc chung

1. Không chỉnh sửa trực tiếp dữ liệu gốc.
2. Mọi quyết định loại bỏ hoặc thay đổi dữ liệu phải có bằng chứng và lý do.
3. Kiểm tra tính toàn vẹn dữ liệu trước và sau khi merge.
4. Phân biệt rõ dữ liệu dùng để phân tích và dữ liệu có thể sử dụng tại thời điểm dự đoán.
5. Mỗi notebook cần có kết quả và kết luận rõ ràng, tránh lặp lại trách nhiệm giữa các bước.
