# 1. Tổng quan:
### - Như đề bài đề ra thì sẽ cần kết nối mạng cho khoảng 500 thiết bị mạng tại văn phòng.
# 2. Đề xuất thiết bị, tài nguyên
### - Ít nhất 2 đường internet của 2 ISP khác nhau
### - 1 router biên được cấu hình BGP để nhận 2 đường internet
### - 1 router VPN(có thể dùng draytek hoặc mikrotik)
### - 2 switch core
### - 2 router(mua thêm 1-2 router để dự phòng)
### - 4 switch access
### - 16 access point
### - 9 wifi mesh
# 3. Triển khai
### - Chia tất cả 4 VLAN với subnet mask /24, 2 VLAN cho mạng dây, 2 VLAN cho riêng hệ thống wifi
### - chia 2 switch core để đi mạng đều cho 2 khu vực của sàn, lấy mốc từ X5 để chia thành 2 khu chính
### - mỗi switch core đi xuống router chính. Từ router chính cắm xuống 4 switch access .
### - 4 switch access chia đều 2 khu vực như ở trên đã nói, 16 access point sẽ cũng chia đều đặt tại các điểm giao của Y2' với X2 tới X9 và Y2 với X2 tới X9. 
### - Với wifi mesh thì root node đặt khu vực trực kỹ thuật, 8 wifi mesh còn lại thì đặt dọc, chia đều trên trục Y2' hoặc Y2.