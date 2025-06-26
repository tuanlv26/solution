# 1. Rủi ro
## - 2 web-server chưa rõ đã chạy load-balance chưa
## - 1 server DB thiếu tính sẵn sàng khi có vấn đề và cũng như khi lượng khách hàng tăng, 1 server không chia tải sẽ khó đáp ứng nhu cầu.
## - Việc backup thủ công hàng tuần sẽ có rủi ro quên do chủ quan và khi cần restore thì dữ liệu đó so với dữ liệu đang chạy sẽ chênh lệch khá nhiều
# 2. Đề xuất cải tiến
## - Thêm 1 server chỉ để chạy Haproxy phục vụ việc load-balance cho cả web-server và DB. Việc thêm server chạy Haproxy không cần tốn quá nhiều resource do Haproxy cũng không đòi hỏi quá nhiều tài nguyên. Viếc dùng 1 server chạy Haproxy cũng dễ dàng cho việc sau này scale thêm instance web-server hay của DB thì thay đổi config tại Haproxy cũng rất nhanh.
## - Thêm 2 server mysql nữa, cài galera để tạo thành một cụm mysql-server, vừa đảm bảo tính sẵn sàng khi có server bị lỗi cũng như setup galera cũng đơn dễ dàng.
## - Việc NAS-server đã dùng 70% thì cần thực hiện các việc:
#### + Xóa các snapshot quá cũ hoặc không dùng tới
#### + Thực hiện đặt job chạy backup tự động(chạy ban đêm là thời điểm ít khách hàng nhất), để tiết kiệm thì ưu tiên backup 1 server mysql là đủ, webserver có thể cân nhắc. Viết thêm script xóa các bản backup cũ quá 1 ngày đi để tiết kiệm không gian lưu trữ.
#### + Nếu có thể thì có thể triển khai cache cho NAS server nếu muốn tăng tốc độ đọc/ghi(không quá ưu tiên).
