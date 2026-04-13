
**1. Tại sao dùng Nginx làm Reverse Proxy?**
Quản lý tập trung: Một cổng 80 duy nhất có thể điều hướng cho nhiều dịch vụ (Node-RED, MyAPI, Web tĩnh).

Bảo mật: Nginx đóng vai trò là "lá chắn", che giấu cổng thực (1880) của Node-RED.

Tối ưu: Nginx xử lý các file tĩnh (HTML, CSS, ảnh) cực nhanh, giúp giảm tải cho Node-RED.

**2. Mount File vs Mount Thư mục**
Mount Thư mục: Toàn bộ nội dung bên trong thư mục máy thật và container đồng bộ với nhau. Nếu bạn tạo file mới ở ngoài, bên trong sẽ có ngay.

Mount File: Chỉ đồng bộ duy nhất 1 file đó. Thường dùng cho các file cấu hình như nginx.conf hoặc settings.js.

**3. Thay đổi index.html có cập nhật ngay không?**
Có. Vì chúng ta dùng Volume (Mount). Container không copy file mà nó "nhìn" trực tiếp vào file trên ổ cứng Ubuntu. Khi bạn sửa file ở Ubuntu, container thấy sự thay đổi đó ngay lập tức.

**4. Ý nghĩa của restart: always và unless-stopped**
Always: Container luôn tự khởi động lại nếu bị lỗi hoặc khi bạn khởi động lại máy Ubuntu.

Unless-stopped: Tương tự như always, nhưng nếu bạn chủ động dùng lệnh docker stop để dừng nó, nó sẽ không tự bật lại khi máy boot.

**5. Dùng chung 1 Network và File cập nhật**
Lợi ích: Các container có thể gọi nhau bằng tên service (ví dụ: http://nodered:1880) thay vì dùng IP ảo. Điều này giúp hệ thống ổn định vì IP của container có thể thay đổi sau mỗi lần restart.
<p>
Sửa Docker Compose:
services:
  nodered:
    networks: [myapp_net]
  nginx:
    networks: [myapp_net]
  tunnel:
    networks: [myapp_net]

networks:
  myapp_net:
    driver: bridge
</p>
**6. Bảo mật với .env và .gitignore**
Cách làm: Tạo file .env chứa CF_TOKEN=your_token_here. Trong compose dùng ${CF_TOKEN}. Thêm .env vào .gitignore.

Tầm quan trọng: Ngăn chặn việc lộ "chìa khóa" (Token) lên GitHub. Nếu lộ, kẻ xấu có thể chiếm quyền điều khiển Tunnel và xâm nhập vào mạng nội bộ của Duy.

**7. Tại sao dùng hậu tố :ro (Read-Only)?**
Bảo mật: Đảm bảo container Nginx chỉ có quyền "đọc" file cấu hình mà không thể "sửa" hoặc xóa nó. Nếu container bị hack, kẻ tấn công cũng không thể đổi cấu hình hệ thống từ bên trong.

**8. Dùng Cloudflare Tunnel có cần mở cổng (UFW) không?**
Không cần. Tunnel tạo kết nối từ trong Ubuntu đi ra ngoài (Outbound). Cloudflare sẽ đón dữ liệu và đẩy ngược lại qua "đường hầm" này. Bạn có thể đóng hết các cổng 80, 1880 trên Firewall của Ubuntu mà web vẫn chạy bình thường, giúp máy chủ cực kỳ an toàn.
