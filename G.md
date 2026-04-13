G. Triển khai ứng dụng đến End-user
Trong Cloudflare: Tạo tunnel (đường hầm), chọn loại triển khai cho docker
<img width="1565" height="746" alt="image" src="https://github.com/user-attachments/assets/33779203-b15d-431d-877c-0f95bf260e89" />

Convert lệnh docker run ... sang dạng docker compose:
"tunnel --no-autoupdate run --token eyJhIjoiYTZlMjQwNTY4NjA3YTg4NzA0ODE0Y2UyOGVkMzI4YjIiLCJ0IjoiNjI2MTRmYmEtNTFmMS00NzlkLWE0ZGItOWRhYWRhYThhM2FjIiwicyI6Ik5UWTBaak15TVRVdFpUY3lPQzAwTWpNNUxXRTBNR1F0WTJVd05UazVOREJtWVdKbSJ9"
Khai báo kết quả convert vào trong file docker-compose.yml:
<img width="1445" height="600" alt="image" src="https://github.com/user-attachments/assets/7b767c01-3a39-4dd5-8fde-c3fff2ee596a" />

Chạy lại docker compose:
<img width="1453" height="402" alt="image" src="https://github.com/user-attachments/assets/be877083-95de-4581-b6b4-4efb0f043e67" />

Public ứng dụng bằng cách thêm 1 router trỏ tới container đang chạy trong docker, dữ liệu sẽ đi qua tunnel, url dạng sub-domain
<img width="1219" height="728" alt="image" src="https://github.com/user-attachments/assets/11f10843-5345-43b8-b752-15dd79f92a32" />
<img width="932" height="211" alt="image" src="https://github.com/user-attachments/assets/cbbb3d11-e7fc-4c5d-9ba5-c9515583fec9" />

Kiểm tra url sub-domain đã hoạt động public cho mọi end-user
<img width="1732" height="915" alt="image" src="https://github.com/user-attachments/assets/c77b5c53-4ec8-4019-998f-2aaa348f9312" />
