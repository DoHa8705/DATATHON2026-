# DATATHON2026

## 1. Giới thiệu

Trong bối cảnh cạnh tranh ngày càng gia tăng, doanh nghiệp không chỉ cần tăng trưởng mà còn phải đảm bảo tính bền vững trong dài hạn. Tuy nhiên, một câu hỏi quan trọng được đặt ra:  
**Điều gì đang thực sự giới hạn tăng trưởng doanh thu, và doanh nghiệp cần làm gì để tối ưu hiệu quả kinh doanh?**

Dự án này tiếp cận bài toán dưới góc nhìn khoa học dữ liệu, triển khai theo pipeline phân tích toàn diện gồm:

- **Descriptive**: Doanh nghiệp đang vận hành như thế nào?
- **Diagnostic**: Vì sao các vấn đề xảy ra?
- **Predictive**: Xu hướng tương lai sẽ ra sao?
- **Prescriptive**: Doanh nghiệp nên hành động như thế nào?

Mục tiêu không chỉ dừng lại ở dự báo, mà còn hướng tới **giải thích và hỗ trợ ra quyết định kinh doanh dựa trên dữ liệu**.
## 2. Phần 1. Tính toán và trả lời câu hỏi trắc nghiệm
## 3. Phần 2+3 Pipeline phân tích và mô hình

### 3.1. Phân tích dữ liệu (EDA)

Phân tích được triển khai theo 3 lớp:

- **Hiệu suất kinh doanh (Performance)**: xu hướng doanh thu, số đơn hàng, AOV  
- **Cấu trúc doanh thu (Structure)**: theo ngành hàng, khu vực, sản phẩm  
- **Rủi ro vận hành (Quality & Risk)**: tỷ lệ hủy, trả hàng  

---

### 3.2. Mô hình dự báo

Mô hình sử dụng kiến trúc **Stacked Hybrid Forecasting**:

- **Base Model (XGBoost)**: học xu hướng chính của doanh thu  
- **Residual Model**: học sai số để hiệu chỉnh dự báo  
- **Ratio Model**: dự báo tỷ lệ COGS/Revenue  

#### Feature Engineering:
- Cyclical features (month, day of week)
- Lag features (1, 7, 364)
- Rolling features (mean, std)

#### Chiến lược:
- Walk-forward validation  
- Recursive forecasting  
- Anchoring theo chu kỳ năm trước  

---

### 3.3. Giải thích mô hình

Sử dụng **SHAP** để:

- Xác định đặc trưng quan trọng (rev_lag_1, rev_lag_364)
- Giải thích đóng góp của từng biến vào dự báo
- Tăng tính minh bạch của mô hình
