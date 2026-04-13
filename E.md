# E. Triển khai (level test) ứng dụng
Chuyển vào trong thư mục ~/myapp
Gõ lệnh để docker compose chạy: sẽ run tất cả các service khai báo trong file docker-compose.yml
Lợi ích: Chỉ cần docker-compose up -d là toàn bộ hệ thống (Web + Node-RED + Tunnel) tự chạy,
<img width="1462" height="161" alt="image" src="https://github.com/user-attachments/assets/8d449854-69db-43a6-ab8b-36cea643f0aa" />

Kiểm tra các container đang chạy trong docker, nếu có cái nào bị restart cần tìm lỗi rồi edit lại docker-compose.yml
<img width="1467" height="210" alt="image" src="https://github.com/user-attachments/assets/40db76e0-104c-49f3-b679-bd2ed07395f0" />
<img width="1173" height="257" alt="image" src="https://github.com/user-attachments/assets/42b25fde-4342-4675-882e-cc0b3acf89ac" />
Sử dụng nodered: kéo nodered http_in , http_response, function : để tạo api get đơn giản (dùng cho /api proxy_pass của nginx)
<img width="901" height="354" alt="image" src="https://github.com/user-attachments/assets/77dab0d2-99a2-4a80-9452-8a43bc276356" />

Sửa file ./myweb/index.html : thêm code html+js để sử dụng được api đã khai báo proxy_pass (thực ra là sử dụng nodered http_in hoặc sử dụng service myapi)
<img width="1468" height="749" alt="image" src="https://github.com/user-attachments/assets/7c187802-c2d1-4e20-8ca9-afc81b437f49" />
<img width="1587" height="992" alt="image" src="https://github.com/user-attachments/assets/68c11440-66d3-4439-a495-83ee428cb778" />
