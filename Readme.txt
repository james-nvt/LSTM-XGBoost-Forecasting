Trong file code của nhóm bao gồm 4 file, được chạy bằng ngôn ngữ Python:
1. ARIMA
2. GradientBoosting
3. LSTM
4. RFM
Tất cả đều sử dụng input là file 'TAB_Betting_Data' 
Tổng quan về dữ liệu khá clean nên ở giai đoạn EDA không quá phức tạp,

Về Forecasting chúng em sử dụng 3 phương pháp forecasting: 

ARIMA (Statistical Method)
XGBoost (Machine Learning)
LSTM (Deep Learning)

1. ARIMA
Dựa trên giả thuyết chuỗi dừng và phương sai sai số không đổi. Mô hình sử dụng đầu vào chính là những tín hiệu quá khứ của chuỗi được dự báo để dự báo nó. Các tín hiệu đó bao gồm: chuỗi tự hồi qui AR (auto regression) và chuỗi trung bình trượt MA (moving average). Hầu hết các chuỗi thời gian sẽ có xu hướng tăng hoặc giảm theo thời gian, do đó yếu tố chuỗi dừng thường không đạt được. Trong trường hợp chuỗi không dừng thì ta sẽ cần biến đổi sang chuỗi dừng bằng sai phân (Differencing). Khi đó tham số đặc trưng của mô hình sẽ có thêm thành phần bậc của sai phân d và mô hình được đặc tả bởi 3 tham số ARIMA(p, d, q).
Mô hình ARIMA (SARIMA) dự đoán: ARIMA(0,0,0)(0,1,1)[7] 
Kết quả sau khi chạy Auto-ARIMA: ARIMA(0,0,0)(0,1,1)[7], RMSE = 1173545.3553
Do model ARIMA bị nhiễu trắng khá nặng mặc dù đã differencing nhiều lần seasonal (dữ liệu mang tính random cao), nhóm sử dụng XGBoost và LSTM như một giải pháp thay thế:


2. XGBoost (Machine Learning)
Kết quả chạy (trước tuning): RMSE = 886354.93
Kết quả chạy (sau tuning với Random Search): 732803.88


3. LSTM (Long Short-Term Memory) - Deep Learning
Kết quả chạy LSTM: RMSE = 1011808.56
Mặc dù RMSE cao hơn XGBoost, nhưng tổng quan về chuỗi dữ liệu thì LSTM bám rất tốt các yếu tố về mùa vụ. Do đó, RMSE cao là vì 2 lí do chính:
Do không đủ tài nguyên training với số lượng epoch lớn dẫn đến mô hình vẫn còn underfitting
Trong quá trình backpropagation, gradient được tính toán dựa trên sai số giữa giá trị dự đoán và giá trị thực tế. Outlier lớn có thể gây ra sai số lớn, làm cho gradient lớn tương ứng, dẫn đến bước cập nhật trọng số không ổn định và có thể khiến mô hình khó hội tụ.
Tuy nhiên nếu có nhiều thời gian training và một khối lượng tài nguyên training đủ lớn, LSTM có thể đưa các dự báo rất chính xác so với các mô hình còn lại (trừ việc nhận biết outlier)
