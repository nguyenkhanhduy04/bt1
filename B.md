# B. Cài đặt Ubuntu + Docker
**1. Cài đặt hệ điều hành Ubuntu 24.04.4 LTS**
Sử dụng một trong các công cụ để giả lập: HyperV (có sẵn của windows), VirutualBox (Miễn phí), VM_Ware (bản quyền)
Download file iso để cài đặt.
<img width="1909" height="890" alt="image" src="https://github.com/user-attachments/assets/bb087dda-3d0b-4eac-8932-9c0c242ab4af" />
**2. Cấu hình mạng trong Ubuntu (và công cụ giả lập) để cho phép truy cập SSH vào Ubuntu từ cmd của windows**
<img width="1069" height="693" alt="image" src="https://github.com/user-attachments/assets/f333396c-f321-4327-b56c-c40f30ea685b" />

**3. Cài đặt docker**
<img width="1453" height="483" alt="image" src="https://github.com/user-attachments/assets/4064f6c5-0683-4279-a5e4-1db2adbb4082" />

Kiểm tra phiên bản docker vừa cài đặt, kiểm tra phiên bản của docker compose
<img width="464" height="119" alt="image" src="https://github.com/user-attachments/assets/5ebfe9f6-df7d-4492-842c-d2a2e8107f16" />

Cấu hình để docker chạy mà không cần tiền tố sudo
<img width="604" height="117" alt="image" src="https://github.com/user-attachments/assets/e177c47c-4ae5-483a-8787-57f18497d9b9" />

Đảm bảo tường lửa trên Ubuntu đã cho phép các cổng 80, 1880, 9630 (Lệnh: sudo ufw allow ...)
<img width="1352" height="749" alt="image" src="https://github.com/user-attachments/assets/36b234f9-18f5-42ac-9772-6035804633a9" />
