# BÀI LÀM – ÔN TẬP NGÀY 2

- **Họ tên:Nguyễn Đức Hiếu**
- **Lớp:CNTT02**
- **Link repository:**
- **Hệ điều hành (Windows/macOS):Windows**

## Bài 1. Lọc log thủ công

###  Các dòng lệnh đã chạy 

```
PS C:\Users\ACER\Documents\Downloads\starter-kit(1)\starter-kit\trung-tam-tieng-anh> Get-Content .\logs\access.log | Select-String "ERROR" > .\logs\error_report.txt
PS C:\Users\ACER\Documents\Downloads\starter-kit(1)\starter-kit\trung-tam-tieng-anh> Get-Content .\logs\error_report.txt
PS C:\Users\ACER\Documents\Downloads\starter-kit(1)\starter-kit\trung-tam-tieng-anh> Get-Content .\logs\error_report.txt | Select-Object -First 2
```

### 2 dòng lỗi đầu tiên trong error_report.txt

```
2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)
```

## Bài 2. Đếm bằng pipeline

### Lệnh

```
PS C:\Users\ACER\Documents\Downloads\starter-kit(1)\starter-kit\trung-tam-tieng-anh> \Get-Content .\logs\access.log | Select-String "WARNING" | Measure-Object | Select-Object -ExpandProperty Count
PS C:\Users\ACER\Documents\Downloads\starter-kit(1)\starter-kit\trung-tam-tieng-anh> Get-Content .\logs\payment.log | Select-String "ERROR" | Measure-Object | Select-Object -ExpandProperty Count
```

### Kết quả đếm (Windows: giá trị Count; macOS: con số in ra)

```text
WARNING trong access.log: 4
ERROR trong payment.log: 3 
```

## Bài 3. Chạy script auto_warning (.ps1 hoặc .sh)

### Dòng lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```
./auto_warning.ps1
```

### Nội dung file logs/warning_report.txt

```
2025-10-18 09:19:13 [WARNING] Cong thanh toan phan hoi cham
2025-10-18 09:28:16 [WARNING] Nhieu lan nhap sai ma OTP
2025-10-18 09:43:01 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:46:22 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:49:43 [WARNING] So du vi gan bang hoc phi
```

## Bài 4. Báo cáo tổng hợp

### Các dòng lệnh đã chạy

```
"=== TONG HOP ACCESS LOG ===" | set-content  -Path ./logs/tong_hop_ngay2.txt 
 sls "error" logs/access.log | foreach-object { $_.Line } | add-content logs/tong_hop_ngay2.txt
(sls "warning" logs/payment.log | Measure-Object -Line).lines | add-content logs/tong_hop_ngay2.txt

```

### Nội dung file logs/tong_hop_ngay2.txt

```
=== TONG HOP ACCESS LOG ===
2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:33:51 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:37:19 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:49:43 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:53:11 [ERROR] Het thoi gian cho (timeout)
```

## Bài 5. Câu hỏi ngắn

- **a) > ghi đè nội dung cũ, còn >> ghi nối tiếp vào cuối tệp.**
- **b) Thay >> bằng > sẽ làm mất nội dung cũ và tiêu đề. Nếu vẫn dùng >> ở lệnh thứ ba, kết quả WARNING sẽ được nối vào cuối tệp.**
- **c) Nên dùng đường dẫn tương đối như .\logs\Payment.log để dễ di chuyển dự án giữa các máy. Đường dẫn tuyệt đối phụ thuộc vào vị trí lưu trữ và tài khoản máy tính.**

## Tự chấm (điền sau khi có đáp án)

- **Điểm tự chấm:** ..../100
- **Lỗi mình đã mắc và cách sửa:**
