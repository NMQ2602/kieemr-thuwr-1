# JMeter Performance Test - vnexpress.net
<img width="1511" height="853" alt="image" src="https://github.com/user-attachments/assets/2ac64101-6c6d-4656-8a73-69f15fb62c6a" />

## Thread Group 1: Kịch bản cơ bản

**Số lượng người dùng (Threads):** ~10  
**Loop Count:** 5 lần lặp  
**Hành vi:** Gửi yêu cầu HTTP GET đến trang chủ của website.

### Kết quả
- **Average Response Time:** 90 ms  
- **Throughput:** 3.6 request/sec  
- **Error Rate:** 0%

### Nhận xét
- Hệ thống phản hồi rất nhanh và ổn định ở mức tải thấp.
- Không phát sinh lỗi HTTP.
- Độ dao động thời gian phản hồi nhỏ, cho thấy server hoạt động ổn định.

---

## Thread Group 2: Kịch bản tải nặng

**Số lượng người dùng:** ~50  
**Ramp-up Period:** 30 giây  

**Hành vi:**  
Gửi yêu cầu HTTP GET đến trang chủ và 1 trang con bất kỳ (ví dụ: bài viết hoặc danh mục).

### Kết quả
- **Average Response Time:** 100 ms  
- **Throughput:** 6.1 request/sec  
- **Error Rate:** 0%

### Nhận xét
- Khi tăng số lượng người dùng từ 10 lên 50, thời gian phản hồi trung bình tăng nhẹ từ 90 ms lên 100 ms.
- Mức tăng này không đáng kể và vẫn nằm trong ngưỡng rất tốt (<200 ms).
- Throughput tăng từ 3.6 lên 6.1 request/giây.
- Không xuất hiện lỗi (Error Rate = 0%), chứng tỏ hệ thống vẫn hoạt động ổn định khi nhiều người dùng truy cập đồng thời.

---

## Thread Group 3: Kịch bản tùy chỉnh

**Số lượng người dùng:** ~20  
**Thời gian chạy:** 60 giây  

**Hành vi**
- Gửi HTTP POST (nếu website hỗ trợ, ví dụ form tìm kiếm) hoặc GET đến 2 trang con khác nhau.
- Sử dụng **HTTP Request Defaults** để cấu hình URL cơ sở.
- Thêm **Listeners** như View Results Tree và Summary Report.

### Kết quả
- **Average Response Time:** 74 ms  
- **Throughput:** 4.2 request/sec  
- **Error Rate:** 0%

### Nhận xét
- Thời gian phản hồi trung bình đạt 74 ms, thấp hơn cả Thread Group 1 và 2.
- Hệ thống xử lý rất tốt trong kịch bản tải trung bình kéo dài.
- Throughput đạt 4.2 request/giây.
- Không xuất hiện lỗi HTTP trong suốt quá trình kiểm thử.

