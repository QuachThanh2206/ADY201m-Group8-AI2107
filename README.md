# ADY201m - Olist Freight Prediction

Đây là project ADY201m của nhóm mình, sử dụng dữ liệu Olist để tìm hiểu các yếu tố ảnh hưởng đến phí vận chuyển (`freight_value`) và hướng tới xây dựng mô hình dự đoán.

Hiện tại nhóm đang làm **bản cơ bản (v0)** để cả 3 cùng chạy được code, hiểu cách xử lý dữ liệu rồi mới làm sâu hơn. Đây chưa phải bản final.

## Thành viên

| Họ và tên | MSSV | Phụ trách chính |
| --- | --- | --- |
| Kiều Đại Dương | HE201928 | SQL |
| Trần Chí Kiên | HE200774 | Data Cleaning |
| Quách Xuân Thành | HE204852 | EDA |

## Trong project có gì?

- `data/raw/`: 9 bảng dữ liệu Olist ban đầu.
- `data/processed/`: nơi lưu dữ liệu sau khi chạy Cleaning.
- `notebooks/01_cleaning.ipynb`: kiểm tra dữ liệu, ghép bảng và tạo CSV cơ bản.
- `notebooks/02_sql.ipynb` và `sql/queries.sql`: thực hành JOIN, GROUP BY và kiểm tra kết quả bằng SQL.
- `notebooks/03_eda.ipynb`: thống kê, vẽ biểu đồ và nhận xét về phí vận chuyển.
- `reports/meeting_checklist.md`: các mục nhóm cần check cùng nhau.

## Cách chạy

Cài Python, mở Terminal trong thư mục project rồi chạy:

```bash
pip install -r requirements.txt
python -m notebook
```

Mở các notebook và chạy theo thứ tự: **01_cleaning → 02_sql → 03_eda**.

Sau bước Cleaning, file `data/processed/olist_freight_v0.csv` sẽ được tạo tự động. Mọi người không cần tự sửa CSV này bằng tay.

## Cách nhóm mình làm

Trước mắt mỗi người hoàn thành phần cơ bản của mình, code rõ ràng và có thể giải thích được. Sau đó cả nhóm cùng xem, chạy lại code của nhau (đặc biệt là Cleaning) rồi mới bổ sung những phần nâng cao.

**Lưu ý:** File geolocation gốc đang có vấn đề về định dạng tọa độ nên bản v0 chưa dùng để tính khoảng cách. Nhóm sẽ kiểm tra lại trước khi sử dụng.
