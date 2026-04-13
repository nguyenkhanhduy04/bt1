# F. Gỡ lỗi:
- Nếu có lỗi xẩy ra trong quá trình triển khai docker compose up -d
- Kiểm tra nhanh: docker compose ps giúp biết container nào đang chạy xem log, ví dụ: docker logs mynginx docker logs myapi
<img width="1459" height="233" alt="image" src="https://github.com/user-attachments/assets/8e6b4363-2dcd-4dd5-8a84-6fe6eca8ca0f" />

- Thêm healthcheck cho myapi trong file docker-compose.yml và Giới hạn resource cho một service: (tránh việc 1 service chiếm quá nhiều ram)
<img width="1467" height="751" alt="image" src="https://github.com/user-attachments/assets/a2e26753-ac92-47ac-aa18-e68d4c606cb5" />

sử dụng lệnh: docker compose stats để quan sát lượng ram sử dụng bởi mỗi service
<img width="1469" height="197" alt="image" src="https://github.com/user-attachments/assets/092a8749-5914-45c2-b911-d13b1ed2bcdc" />
