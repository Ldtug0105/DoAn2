# Dự Đoán Doanh Số Bán Hàng Từ Dữ Liệu Lịch Sử Giao Dịch

**Học phần:** Đồ án 2  
**Trường:** Đại học Kinh tế - Kỹ thuật Công nghiệp (UNETI) - Khoa Khoa học Ứng dụng  
**Giảng viên hướng dẫn:** Lê Hằng Anh  
**Nhóm thực hiện:** TTV3

---

## Giới thiệu (Overview)

Dự án này tập trung vào việc xây dựng các mô hình dự báo doanh số bán hàng trong tương lai dựa trên bộ dữ liệu thực tế **Online Retail II**. Mục tiêu là giúp doanh nghiệp tối ưu hóa quản lý hàng tồn kho, lập kế hoạch tiếp thị và đưa ra các quyết định chiến lược dựa trên dữ liệu.

Dự án áp dụng quy trình Khoa học dữ liệu trọn vẹn từ Tiền xử lý, Phân tích khám phá (EDA) đến Xây dựng và Đánh giá các mô hình Máy học (Machine Learning) và Học sâu (Deep Learning).

## Thành viên nhóm (Team Members)

| STT | Họ và tên | Mã sinh viên | Vai trò |
|-----|-----------------------|--------------|-----------------------------------------|
| 1 | **Lê Đình Tùng** | 22174600004 | Nhóm trưởng, Tiền xử lý, Prophet |
| 2 | **Nguyễn Thị Thuyên** | 22174600032 | EDA, Feature Engineering, Random Forest |
| 3 | **Huỳnh Ngọc Tường Vi** | 22174600005 | Chuẩn hóa dữ liệu, LSTM |

## Dữ liệu (Dataset)

* **Nguồn dữ liệu:** Bộ dữ liệu [Online Retail II](https://archive.ics.uci.edu/ml/datasets/Online+Retail+II) từ UCI Machine Learning Repository.
* **Mô tả:** Chứa các giao dịch từ ngày 01/12/2009 đến 09/12/2011 của một nhà bán lẻ trực tuyến tại Anh.
* **Kích thước:** Khoảng 1,067,371 dòng dữ liệu ban đầu.
* **Các thuộc tính chính:** `Invoice`, `StockCode`, `Description`, `Quantity`, `InvoiceDate`, `Price`, `Customer ID`, `Country`.

## Công nghệ sử dụng (Tech Stack)

Dự án được thực hiện bằng ngôn ngữ **Python** trên môi trường **Google Colab/Jupyter Notebook**.

**Các thư viện chính:**
* **Xử lý dữ liệu:** `Pandas`, `NumPy`
* **Trực quan hóa:** `Matplotlib`, `Seaborn`, `Plotly`
* **Machine Learning:** `Scikit-learn` (Random Forest, Linear Regression, Metrics)
* **Deep Learning:** `TensorFlow`, `Keras` (LSTM)
* **Time Series:** `Prophet` (Facebook), `pmdarima`
* **Khác:** `Shap` (Model Explainability), `Imbalanced-learn`

## Quy trình thực hiện (Methodology)

1.  **Thu thập & Làm sạch dữ liệu:**
    * Xử lý giá trị thiếu (Missing values).
    * Loại bỏ dữ liệu nhiễu (Số lượng âm, đơn giá <= 0, đơn hàng bị hủy 'C').
    * Xử lý ngoại lệ (Outliers) bằng phương pháp IQR.
2.  **Feature Engineering (Tạo đặc trưng):**
    * Trích xuất đặc trưng thời gian: Ngày, Tháng, Năm, Quý, Thứ, Giờ.
    * Tính tổng doanh thu (`TotalAmount = Quantity * Price`).
3.  **Phân tích khám phá (EDA):**
    * Phân tích xu hướng doanh số theo thời gian (Ngày, Tháng).
    * Phân tích theo Quốc gia và Sản phẩm bán chạy.
4.  **Mô hình hóa (Modeling):**
    * **Prophet:** Mô hình chuyên biệt cho chuỗi thời gian, xử lý tốt tính mùa vụ.
    * **Random Forest:** Thuật toán học máy mạnh mẽ, nắm bắt các mối quan hệ phi tuyến.
    * **LSTM (Long Short-Term Memory):** Mạng nơ-ron hồi quy, tối ưu cho việc ghi nhớ các phụ thuộc dài hạn trong chuỗi thời gian.
5.  **Đánh giá (Evaluation):**
    * Sử dụng các chỉ số: RMSE, MAE, R-squared ($R^2$).

## Kết quả (Results)

Dựa trên quá trình thực nghiệm và so sánh:

* **LSTM:** Cho kết quả tốt nhất trong việc bám sát biến động thực tế và dự báo ngắn hạn, đặc biệt trong giai đoạn biến động mạnh.
* **Prophet:** Phù hợp cho các bài toán cần tính ổn định cao và dễ giải thích về xu hướng/mùa vụ.
* **Random Forest:** Có khả năng chịu nhiễu tốt nhưng gặp hạn chế với chuỗi thời gian có tính liên tục cao và xu hướng phức tạp.

## Cài đặt & Hướng dẫn chạy (Installation & Usage)

Để chạy dự án này trên máy cục bộ:

1.  **Clone repository:**
    ```bash
    git clone [https://github.com/username/project-name.git](https://github.com/username/project-name.git)
    cd project-name
    ```

2.  **Cài đặt các thư viện cần thiết:**
    ```bash
    pip install pandas numpy matplotlib seaborn scikit-learn tensorflow prophet plotly pmdarima
    ```

3.  **Chạy Notebook:**
    * Mở file `BÁO CÁO ĐỒ ÁN 2 (NHÓM TTV3).ipynb` bằng Jupyter Notebook hoặc Visual Studio Code.
    * Đảm bảo file dữ liệu `online_retail_II.xlsx` nằm cùng thư mục hoặc cập nhật đường dẫn trong code.
    * Chạy lần lượt các cell (Run All).

## Cấu trúc thư mục

```text
├── data/
│   └── online_retail_II.xlsx    # File dữ liệu gốc
├── notebooks/
│   └── BÁO CÁO ĐỒ ÁN 2 (NHÓM TTV3).ipynb # Source code chính
├── reports/
│   ├── Báo cáo môn đồ án_Nhóm_TTV3.pdf   # Báo cáo chi tiết
│   └── PP Nhóm TTV3.pptx                 # Slide thuyết trình
└── README.md
```
