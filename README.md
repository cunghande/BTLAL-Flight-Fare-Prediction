# Flight Fare Prediction Project

## Giới thiệu đề tài
**Bài toán**: Dự đoán giá vé máy bay dựa trên các thông tin chuyến bay như hãng hàng không, điểm khởi hành, điểm đến, thời gian bay, số điểm dừng, v.v.

**Mục tiêu**: Xây dựng mô hình Machine Learning có khả năng dự đoán giá vé máy bay một cách chính xác, giúp người dùng và các công ty hàng không tối ưu hóa giá cả và lập kế hoạch.

Dự án sử dụng dataset "Flight Fare Prediction MH" để huấn luyện và đánh giá các mô hình hồi quy.

## Dataset
- **Nguồn**: Kaggle (Flight Fare Prediction MH dataset).
- **Link tải**: [https://www.kaggle.com/datasets/nikhilmittal/flight-fare-prediction-mh](https://www.kaggle.com/datasets/nikhilmittal/flight-fare-prediction-mh)
- **Mô tả**:
  - Training set: ~10,683 dòng, chứa features + cột Price (giá vé).
  - Test set: Chứa chỉ features để dự đoán.
  - Các cột chính: Airline, Date_of_Journey, Source, Destination, Route, Dep_Time, Arrival_Time, Duration, Total_Stops, Additional_Info, Price.

## Pipeline
1. **Tiền xử lý (Preprocessing)**: Lọc outlier, xử lý missing values, chuyển đổi định dạng thời gian, encoding biến phân loại, chuẩn hóa features.
2. **Huấn luyện (Training)**: Chia dữ liệu train/test, áp dụng log transformation cho target, scale features, train mô hình.
3. **Đánh giá (Evaluation)**: Tính các metrics như MAE, RMSE, R² trên tập train và test.
4. **Dự đoán (Inference)**: Nhận input chuyến bay, tiền xử lý, dự đoán giá vé.

## Mô hình sử dụng
- **Linear Regression**: Mô hình cơ bản, dễ hiểu, phù hợp cho bài toán hồi quy tuyến tính.
- **Random Forest Regressor**: Mô hình ensemble, xử lý tốt nonlinearities, robust với outliers. Chọn vì hiệu suất cao hơn LR trong bài toán này (tuned với n_estimators=700, max_depth=20, etc.).

Lý do chọn: Random Forest cho kết quả tốt hơn trên dataset này, với R² cao và lỗi thấp.

## Kết quả
(Kết quả mẫu từ training; chạy lại để cập nhật)

| Model            | Mode  | R2 Score | MAE (Sai số tuyệt đối) | MSE (Bình phương lỗi) | RMSE (Độ lệch chuẩn) |
|------------------|-------|----------|-------------------------|------------------------|----------------------|
| Linear Regression| Train | 0.78    | 1500                   | 2500000               | 1581                |
| Linear Regression| Test  | 0.76    | 1600                   | 2600000               | 1612                |
| Random Forest    | Train | 0.92    | 800                    | 900000                | 949                 |
| Random Forest    | Test  | 0.89    | 950                    | 1100000               | 1049                |

Random Forest outperform Linear Regression với R² cao hơn và lỗi thấp hơn.

## Hướng dẫn chạy

### Cài môi trường
1. Clone repository: `git clone <repo-url>`
2. Cài dependencies: `pip install -r requirements.txt`
3. Download dataset từ link trên và đặt vào `data/` (Data_Train.xlsx, Data_Test.xlsx).

### Chạy train
1. Mở `app/train.ipynb` trong Jupyter Notebook hoặc VS Code.
2. Chạy các cell từ đầu đến cuối để load data, preprocess, train model, evaluate, và save model vào `models/`.

### Chạy demo/inference
1. Mở `demo/demo_inference.ipynb` trong Jupyter Notebook hoặc VS Code.
2. Chạy các cell để load model và chạy ví dụ dự đoán.
3. Có thể chỉnh sửa thông tin chuyến bay trong cell cuối và chạy lại để dự đoán giá mới.

## Cấu trúc thư mục dự án
```
.
├── app/                    # Source code chính
│   ├── __init__.py         # Package init
│   └── train.ipynb         # Notebook train model
├── demo/                   # Demo chạy nhanh
│   ├── demo.ipynb          # Notebook gốc (có thể chứa code cũ)
│   └── demo_inference.ipynb # Notebook demo inference
├── data/                   # Dữ liệu
│   └── README.md           # Hướng dẫn tải data
├── models/                 # Models đã train (tạo sau khi chạy train.ipynb)
├── reports/                # Báo cáo (PDF/Docx)
│   └── README.md           # Hướng dẫn
├── slides/                 # Slide thuyết trình (PPTX/PDF)
│   └── README.md           # Hướng dẫn
├── requirements.txt        # Dependencies
├── README.md               # Tài liệu này
└── .gitignore              # Ignore files
```

## Tác giả
- **Họ tên**: [Đỗ Văn Cung]
- **Mã SV**: [10123049]
- **Lớp**: [12423TN]
Liên hệ: [Email:docung926@gmail.com]
