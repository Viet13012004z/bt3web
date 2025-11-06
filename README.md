# bt3web Bài tập 3   : môn Phát triển ứng dụng trên nền web # Nguyễn Hoàng Việt 
Giảng viên  : Đỗ Duy Cốp
Lớp học phần: 58KTPM
Ngày giao   : 2025-10-24 13:50
Hạn nộp     : 2025-11-05 00:00
--------------------------------------------------
Yêu cầu     : LẬP TRÌNH ỨNG DỤNG WEB trên nền linux
1. Cài đặt môi trường linux: SV chọn 1 trong các phương án
 - enable wsl: cài đặt docker desktop
 - enable wsl: cài đặt ubuntu
 - sử dụng Hyper-V: cài đặt ubuntu
 - sử dụng VMware : cài đặt ubuntu
 - sử dụng Virtual Box: cài đặt ubuntu
2. Cài đặt Docker (nếu dùng docker desktop trên windows thì nó có ngay)
3. Sử dụng 1 file docker-compose.yml để cài đặt các docker container sau: 
   mariadb (3306), phpmyadmin (8080), nodered/node-red (1880), influxdb (8086), grafana/grafana (3000), nginx (80,443)
4. Lập trình web frontend+backend:
 SV chọn 1 trong các web sau:
 4.1 Web thương mại điện tử
 - Tạo web dạng Single Page Application (SPA), chỉ gồm 1 file index.html, toàn bộ giao diện do javascript sinh động.
 - Có tính năng login, lưu phiên đăng nhập vào cookie và session
   Thông tin login lưu trong cơ sở dữ liệu của mariadb, được dev quản trị bằng phpmyadmin, yêu cầu sử dụng mã hoá khi gửi login.
   Chỉ cần login 1 lần, bao giờ logout thì mới phải login lại.
 - Có tính năng liệt kê các sản phẩm bán chạy ra trang chủ
 - Có tính năng liệt kê các nhóm sản phẩm
 - Có tính năng liệt kê sản phẩm theo nhóm
 - Có tính năng tìm kiếm sản phẩm
 - Có tính năng chọn sản phẩm (đưa sản phẩm vào giỏ hàng, thay đổi số lượng sản phẩm trong giỏ, cập nhật tổng tiền)
 - Có tính năng đặt hàng, nhập thông tin giao hàng => được 1 đơn hàng.
 - Có tính năng dành cho admin: Thống kê xem có bao nhiêu đơn hàng, call để xác nhận và cập nhật thông tin đơn hàng. chuyển cho bộ phận đóng gói, gửi bưu điện, cập nhật mã COD, tình trạng giao hàng, huỷ hàng,...
 - Có tính năng dành cho admin: biểu đồ thống kê số lượng mặt hàng bán được trong từng ngày. (sử dụng grafana)
 - backend: sử dụng nodered xử lý request gửi lên từ javascript, phản hồi về json.
 4.2 Web IOT: Giám sát dữ liệu IOT.
 - Tạo web dạng Single Page Application (SPA), chỉ gồm 1 file index.html, toàn bộ giao diện do javascript sinh động.
 - Có tính năng login, lưu phiên đăng nhập vào cookie và session
   Thông tin login lưu trong cơ sở dữ liệu của mariadb, được dev quản trị bằng phpmyadmin, yêu cầu sử dụng mã hoá khi gửi login.
   Chỉ cần login 1 lần, bao giờ logout thì mới phải login lại.
 - hiển thị giá trị mới nhất của các thông số đang giám sát, khi click vào thì hiển thị đồ thị lịch sử quá trình thay đổi (gọi grafana iframe để hiển thị)
 - backend: Sử dụng nodered để đọc dữ liệu từ các cảm biến (có thể dùng api online để lấy dữ liệu theo giời gian thực), 
   nodered sẽ lưu dữ liệu mới nhất (dạng update) vào cơ sở dữ liệu mariadb (sử dụng phpmyadmin để tạp table và quản trị lần đầu)
   nodered sẽ lưu dữ liệu (insert) vào influxdb để lưu giá trị lịch sử, để cho grafana dùng để hiển thị biểu đồ.
5. Nginx làm web-server
 - Cấu hình nginx để chạy được website qua url http://fullname.com  (thay fullname bằng chuỗi ko dấu viết liền tên của bạn)
 - Cấu hình nginx để http://fullname.com/nodered truy cập vào nodered qua cổng 80, (dù nodered đang chạy ở port 1880)
 - Cấu hình nginx để http://fullname.com/grafana truy cập vào grafana qua cổng 80, (dù grafana đang chạy ở port 3000)

Yêu cầu sinh viên lưu code trên github
có file readme.md có hình ảnh + text: ghi lại nhật ký quá trình làm bài.


# CÀI ĐẶT MÔI TRƯỜNG LINUX
# Cài đặt Ubuntu.
- Bật wsl
- Mở CMD (Admin) -> dán wsl --install.

<img width="972" height="536" alt="image" src="https://github.com/user-attachments/assets/ed2d757b-feb3-4a60-b4ac-dc4214c08f53" />

# Các folder cần thiết khi tạo 
- docker-compose.yml sử dụng docker-compose up có 6 container 

<img width="284" height="999" alt="image" src="https://github.com/user-attachments/assets/8b4960c1-6fb3-49df-9dfe-66f3b026f924" />

# Docker desktop giao diện khi cài thành công 

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/2120726a-90db-4b1f-a4e0-5a66f262d932" />


<img width="1917" height="1079" alt="image" src="https://github.com/user-attachments/assets/efe190b7-38bf-4a25-a791-5a8eb64afaaa" />

sau khi ấn vào localhost sẽ hiện ra giao diện và bắt đăng nhập khi ta cấu hình docker-compose.yml

- Phpmyadmin

<img width="1919" height="999" alt="image" src="https://github.com/user-attachments/assets/8cee2f65-579f-4745-9e63-fda1fef37ec2" />

- nodered

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/607897c4-fdc8-4daf-af49-102e272df52d" />

# Cấu hình node 

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/1206ec40-8de5-4132-a750-6e71a6c9bdac" />

# các flow với tính năng của trang web: mua bán hàng, sản phẩm bán chạy, tìm kiếm sản phẩm , đăng nhập tài khoản 

<img width="1329" height="623" alt="image" src="https://github.com/user-attachments/assets/7b3ad505-7380-421e-9a36-74c331e8c544" />

<img width="1457" height="629" alt="image" src="https://github.com/user-attachments/assets/eb395095-1cb3-4935-960b-fba7129925d3" />

<img width="1465" height="536" alt="image" src="https://github.com/user-attachments/assets/dc366e10-1d48-432d-9b0d-b3bc1ef2e519" />

# giao diện trang web

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/78f78a01-7174-4270-8d2f-5d58c2c9a781" />

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/88552b75-b058-48db-a9dc-6ce87c2b2453" />

<img width="1917" height="1079" alt="image" src="https://github.com/user-attachments/assets/341135ef-0c2a-4d24-9ef2-816657e23624" />

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/9fd4beff-16a9-4f0f-9fb3-9f0cfdadd053" />

# dùng nginx làm websever 

- Đầu tiên mở notepad sau đó vào đường dẫn như ảnh 

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/8385946a-ae76-4f79-a675-26be81460b40" />

mở host lên xong cấu hình bên trong

<img width="1285" height="946" alt="image" src="https://github.com/user-attachments/assets/5edff62c-24b0-4c24-84ea-3a53a9589fa7" />

sửa lại ở cấu hình nginx thay server name

<img width="1918" height="1079" alt="image" src="https://github.com/user-attachments/assets/5683ab87-0d5c-41ae-a2ab-baebcb41ea5b" />

sửa cả ở docker-compose.yml

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/62ef42c0-7801-4cb4-8e1d-a81fd03c9037" />

sau khi cấu hình xong ta nhập nguyenhoangviet.com là tên server mới thay thế localhost

<img width="1526" height="224" alt="image" src="https://github.com/user-attachments/assets/805d0da1-f879-4244-ba09-e397161677c4" />

