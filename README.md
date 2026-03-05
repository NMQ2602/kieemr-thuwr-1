# JMeter Performance Test - vnexpress.net
<img width="1511" height="853" alt="image" src="https://github.com/user-attachments/assets/2ac64101-6c6d-4656-8a73-69f15fb62c6a" />

## Thread Group 1: Kịch bản cơ bản

**Số lượng người dùng (Threads):** ~10  
**Loop Count:** 5 lần lặp  
**Hành vi:** Gửi yêu cầu HTTP GET đến trang chủ của website.
<img width="1518" height="851" alt="image" src="https://github.com/user-attachments/assets/b02b85ae-569b-4796-89f7-70911f89a356" />
<img width="1516" height="848" alt="image" src="https://github.com/user-attachments/assets/e5fb5e4f-1806-463d-b5a7-3164384a185a" />

### Kết quả
- **Average Response Time:** 90 ms  
- **Throughput:** 3.6 request/sec  
- **Error Rate:** 0%
<img width="1382" height="784" alt="image" src="https://github.com/user-attachments/assets/ca68b8cd-3827-44f2-b87a-34762aab41ef" />
<img width="1384" height="774" alt="image" src="https://github.com/user-attachments/assets/8dcee7a1-0817-475f-9ea0-e57d2ee5ab82" />

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
<img width="1386" height="778" alt="image" src="https://github.com/user-attachments/assets/940fae45-dc80-439a-aa50-5296554631d9" />

### Kết quả
- **Average Response Time:** 100 ms  
- **Throughput:** 6.1 request/sec  
- **Error Rate:** 0%
<img width="1383" height="769" alt="image" src="https://github.com/user-attachments/assets/bfff7e70-b2fa-4aca-848b-760ab3fbba2a" />
<img width="1378" height="775" alt="image" src="https://github.com/user-attachments/assets/53deb34f-0ad9-481f-93d8-c8fd010ed27a" />

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
<img width="1511" height="846" alt="image" src="https://github.com/user-attachments/assets/b6ae71b4-f3e7-483b-bcb5-1ac5a690a883" />


### Kết quả
- **Average Response Time:** 74 ms  
- **Throughput:** 4.2 request/sec  
- **Error Rate:** 0%
<img width="1386" height="819" alt="image" src="https://github.com/user-attachments/assets/8e8eab12-3444-41ff-a40a-d46b8ac75f60" />

### Nhận xét
- Thời gian phản hồi trung bình đạt 74 ms, thấp hơn cả Thread Group 1 và 2.
- Hệ thống xử lý rất tốt trong kịch bản tải trung bình kéo dài.
- Throughput đạt 4.2 request/giây.
- Không xuất hiện lỗi HTTP trong suốt quá trình kiểm thử.

