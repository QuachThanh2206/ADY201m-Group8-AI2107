# Phân tích các yếu tố quyết định và dự đoán phí vận chuyển đơn hàng thương mại điện tử
 
**Nghiên cứu trên dữ liệu Olist (Brazil)** · Môn AI2107 / ADY201M · Nhóm 2
 
| Thành viên | Mã sinh viên |
|---|---|
| Kiều Đại Dương | HE201928 |
| Trần Chí Kiên | HE200774 |
| Quách Xuân Thành | HE204852 |
 
## 1. Giới thiệu
 
Phí vận chuyển là một phần của tổng chi phí mua hàng và có thể ảnh hưởng đến việc khách có hoàn tất đơn hay không. Bộ dữ liệu công khai của Olist có phí vận chuyển của từng món hàng nhưng không có biểu phí của đơn vị vận chuyển. Dự án dùng dữ liệu này để:
 
1. **Mô tả:** phí vận chuyển phân bố thế nào và thay đổi ra sao theo cân nặng, thể tích, khoảng cách và giá bán.
2. **Giải thích:** khi xét các đặc điểm cùng nhau, đặc điểm nào đóng góp nhiều nhất vào phí.
3. **Dự đoán:** dự đoán `freight_value` (BRL) bằng mô hình hồi quy và so sánh các mô hình.
Dữ liệu gốc: [Brazilian E-Commerce Public Dataset by Olist (Kaggle)](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce/data).
 
## 2. Kết quả chính
 
- Sau làm sạch: **108.937 dòng × 10 cột** (từ 112.650 dòng món hàng ban đầu).
- Phí lệch phải: trung bình ≈ 20,01 BRL, trung vị ≈ 16,28 BRL; một nửa số dòng nằm trong khoảng 13,08 – 21,15 BRL.
- Tương quan Pearson với phí: cân nặng 0,61 · thể tích 0,58 · giá 0,41 · khoảng cách 0,39.
- Mô hình **Random Forest**: MAE ≈ **3,60 BRL**, R² ≈ **0,751** trên tập kiểm tra (80/20, `random_state = 42`); Linear Regression (so sánh): MAE ≈ 5,22 BRL.
- Độ quan trọng đặc trưng (Random Forest): thể tích 0,348 · khoảng cách 0,310 · cân nặng 0,214 · giá 0,129.
> Đây là quan hệ quan sát được trong dữ liệu lịch sử 2016–2018, **không khẳng định quan hệ nhân quả** và không thay thế biểu phí chính thức của đơn vị vận chuyển. Cách chia ngẫu nhiên theo dòng có thể làm điểm đánh giá lạc quan hơn.
 
## 3. Cấu trúc thư mục
 
```
.
├── data/
│   ├── raw/        # 9 file CSV gốc của Olist
│   └── cleaned/    # olist_clean.csv (kết quả của notebook 3)
├── notebooks/
│   ├── 1. Business Understanding and Analysis.ipynb
│   ├── 2. Data Exploration and Quality Assessment.ipynb
│   ├── 3. Clean data.ipynb
│   ├── 4. Data Analysis with SQL.ipynb
│   ├── 5. Exploratory Data Analysis.ipynb
│   └── 6. Regression Analysis.ipynb
├── report/         # Báo cáo dự án (Project_Report_Olist_Shipping_Fee_EN.docx)
├── slide/          # Olist_16_Slide.pptx
└── README.md
```
 
## 4. Các notebook (chạy theo thứ tự)
 
| # | Notebook | Nội dung | Đọc | Ghi |
|---|---|---|---|---|
| 1 | Business Understanding and Analysis | Bối cảnh, câu hỏi kinh doanh, bài toán DS | — | — |
| 2 | Data Exploration and Quality Assessment | Kiểm tra kích thước, kiểu dữ liệu, thiếu, trùng, khóa, ngoại lai | `data/raw/` | — |
| 3 | Clean data | Ghép 7 bảng, xử lý thiếu, lọc, tạo `distance_km`, `volume_cm3` | `data/raw/` | `data/cleaned/olist_clean.csv` |
| 4 | Data Analysis with SQL | Thống kê phí bằng SQL (SQLite trong bộ nhớ) | `olist_clean.csv` | — |
| 5 | Exploratory Data Analysis | Phân bố, xu hướng tháng, tương quan, danh mục | `olist_clean.csv` | — |
| 6 | Regression Analysis | Linear Regression và Random Forest, độ quan trọng đặc trưng | `olist_clean.csv` | — |
 
Các notebook dùng **đường dẫn tương đối** (`../data/raw/`, `../data/cleaned/`) nên phải mở và chạy từ thư mục `notebooks/`.
 
## 5. Dữ liệu sau làm sạch (`olist_clean.csv`)
 
| Cột | Ý nghĩa |
|---|---|
| `order_id`, `order_item_id` | Khóa của một món hàng trong đơn |
| `seller_id` | Người bán (chỉ dùng để mô tả, không đưa vào mô hình) |
| `order_purchase_timestamp` | Thời điểm đặt hàng |
| `price` | Giá bán (BRL) |
| `weight_g` | Cân nặng sản phẩm (g) |
| `volume_cm3` | Thể tích = dài × cao × rộng (cm³) |
| `distance_km` | Khoảng cách Haversine giữa người bán và khách (km) |
| `category` | Danh mục sản phẩm (tiếng Anh) |
| `freight_value` | **Biến mục tiêu**: phí vận chuyển (BRL) |
 
Điều kiện lọc chính: đơn `delivered`, thời gian từ 01/2017 đến 08/2018, đủ tọa độ, cân nặng và kích thước hợp lệ, cân nặng > 0 và `freight_value` > 0.
 
## 6. Cài đặt và chạy
 
Yêu cầu Python 3.9 trở lên.
 
```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```
 
`sqlite3` có sẵn trong Python. Mở thư mục dự án bằng VS Code (cài extension Python và Jupyter) hoặc chạy `jupyter notebook`, rồi mở lần lượt các notebook trong `notebooks/`.
 
Nếu chỉ muốn chạy notebook 4, 5, 6, không cần chạy lại notebook 3 vì `data/cleaned/olist_clean.csv` đã có sẵn.
 
## 7. Giới hạn
 
- Dữ liệu thuộc giai đoạn 2016–2018, chưa áp dụng trực tiếp cho mức phí hiện nay.
- Chỉ gồm đơn đã giao và có phí lớn hơn 0; mô hình không dự đoán được trường hợp miễn phí vận chuyển.
- Khoảng cách tính theo đường chim bay từ tọa độ đại diện của mã bưu chính, không phải quãng đường thực tế.
 
