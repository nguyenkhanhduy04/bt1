# C. Cấu hình docker compose:
Tạo thư mục: ~/myapp
<img width="808" height="44" alt="image" src="https://github.com/user-attachments/assets/948fa082-97b2-4d6c-8561-db3fea1b21cc" />

Chuyển vào trong thư mục ~/myapp
<img width="310" height="45" alt="image" src="https://github.com/user-attachments/assets/0858d119-3205-43c0-b6cc-9904fcd0188f" />

Tạo file ./myweb/index.html (với nội dung là thông tin cá nhân của em)
<img width="536" height="21" alt="image" src="https://github.com/user-attachments/assets/c6931f49-f1b6-4e10-822a-109bc71b3688" />
<img width="1446" height="756" alt="image" src="https://github.com/user-attachments/assets/17d73776-2481-48f4-916a-66d437b84492" />

Tạo file docker-compose.yml để nó sẽ có các dịch vụ sau:
Khai báo sử dụng nodered/node-red, cổng 1880, dữ liệu nằm tại thư mục ./nodered
Khai báo sử dụng nginx, cổng 80, cấu hình trong file ./nginx/nginx.conf
<img width="643" height="27" alt="image" src="https://github.com/user-attachments/assets/622a8163-9c0c-426e-a8f8-95d2798c1661" />
<img width="1482" height="753" alt="image" src="https://github.com/user-attachments/assets/d9e1721a-164e-42a0-bb7d-8ffb29aa6d68" />

Mount thư mục ./myweb thành thư mục /myweb trong nginx
Mount file ./nginx/nginx.conf vào file /etc/nginx/nginx.conf trong nginx
Edit file ./nginx/nginx.conf để:
Cấu hình web server cổng 80
server_name là sub-domain (sub-domain tuỳ ý của em)
location / trỏ tới root là thư mục /myweb
location /api dùng proxy_pass trỏ tới 1 (hoặc nhiều) node http_in của nodered
<img width="608" height="29" alt="image" src="https://github.com/user-attachments/assets/e4787f34-29ca-42d7-a7cd-19f0d0d39682" />
<img width="1426" height="742" alt="image" src="https://github.com/user-attachments/assets/53a05cc6-ed40-424c-8dd0-40ad36f9cd5b" />
Chạy docker-compose lần đầu để Node-RED tự sinh file cấu hình trong thư mục ./nodered, sau đó mới tiến hành sửa settings.js và restart lại container
<img width="1458" height="235" alt="image" src="https://github.com/user-attachments/assets/70524195-5cbd-4e6d-b121-42ea5ab8b86e" />
Edit file ./nodered/settings.js để nodered bắt buộc đăng nhập
<img width="648" height="22" alt="image" src="https://github.com/user-attachments/assets/32749fd4-8a1e-4795-9ed7-26d48a82a626" />
  <img width="1459" height="747" alt="image" src="https://github.com/user-attachments/assets/be7d2d04-b256-4ea4-bde5-85aac182196e" />
# Kiểm thử truy cập
<img width="1464" height="322" alt="image" src="https://github.com/user-attachments/assets/969c5a55-d86a-44a3-bb44-6eb12c0ab545" />
<img width="1549" height="784" alt="image" src="https://github.com/user-attachments/assets/3d5c58e2-00fb-4ceb-b5a9-9ab22faeecd9" />
<img width="1842" height="873" alt="image" src="https://github.com/user-attachments/assets/1456bc40-630d-45ae-b036-d71fe187501e" />

