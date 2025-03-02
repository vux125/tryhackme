# Mô hình OSI và TCP/IP

## Mô hình OSI

- Sơ lược về mô hình OSI qua bảng:

![image](https://github.com/user-attachments/assets/11533210-5c73-4b73-aee2-30f9919912ad)


## Mô hình TCP/IP

- Sơ lược về mô hình TCP/IP qua bảng:

![image](https://github.com/user-attachments/assets/f8863dbd-4fec-4608-8cfe-575435777212)

# Các giao thức mạng

## Networking Essentials

### Dynamic Host Configuration Protocol (DHCP) 

- DHCP là giao thức quản lý mạng được sử dụng trên mạng Internet Protocol(IP) để tự động gán địa chỉ IP và các thông số truyền thông khác cho các thiết bị được kết nối với mạng bằng kiến ​​trúc máy khách-máy chủ.

- DHCP thực hiện theo bốn bước:

  - DHCP Discover : Máy khách sẽ phát đi tin nhắn DHCPDISCOVER để tìm kiếm máy chủ DHCP cục bộ nếu có.

  - DHCP Offer : Máy chủ phản hồi bằng tin nhắn DHCPOFFER với địa chỉ IP có sẵn để máy khách chấp nhận.
    
  - DHCP Request : Máy khách phản hồi bằng tin nhắn DHCPREQUEST để cho biết rằng máy khách đã chấp nhận IP được cung cấp.

  - DHCP Acknowledge : Máy chủ phản hồi bằng tin nhắn DHCPACK để xác nhận rằng địa chỉ IP được cung cấp hiện đã được gán cho máy khách này.

![image](https://github.com/user-attachments/assets/06501a90-effa-4e79-812b-d7dd62a634d7)

### ARP

- Address Resolution Protocol (ARP) chịu trách nhiệm tìm địa chỉ MAC (phần cứng) liên quan đến một địa chỉ IP cụ thể. Giao thức này hoạt động bằng cách phát một truy vấn ARP, "Ai có địa chỉ IP này? Hãy cho tôi biết." Và phản hồi có dạng, "Địa chỉ IP nằm tại địa chỉ MAC này."

- Là cầu nối giữa địa chỉ lớp 3 với địa chỉ lớp 2

- Gói tin gửi đi sẽ có MAC nguồn là chính máy gửi MAC đích sẽ là broadcast ff:ff:ff:ff:ff:ff cùng địa chỉ IP muốn của máy muốn tìm địa chỉ MAC của nó.

### ICMP

- Internet Control Message Protocol (ICMP) chủ yếu được sử dụng để chẩn đoán mạng và báo cáo lỗi. Hai lệnh phổ biến dựa vào ICMP và chúng đóng vai trò quan trọng trong việc khắc phục sự cố mạng và bảo mật mạng. Các lệnh là:

- `ping`: Lệnh này sử dụng ICMP để kiểm tra khả năng kết nối với hệ thống mục tiêu và đo thời gian khứ hồi (RTT). Nói cách khác, nó có thể được sử dụng để biết mục tiêu còn hoạt động và phản hồi của mục tiêu có thể đến được hệ thống của chúng tôi.
- `traceroute` : Lệnh này được gọi `traceroute` trên các hệ thống Linux và UNIX và `tracert` trên các hệ thống MS Windows. Lệnh này sử dụng ICMP để khám phá tuyến đường từ máy chủ của bạn đến mục tiêu.

![image](https://github.com/user-attachments/assets/b1f401fe-1877-4e58-a835-cffd3298396f)

### NAT

- Network Address Translation (NAT) giống như người một biên dịch, nó sẽ giúp chuyển địa chỉ IP private sang IP public và ngược lại.

![image](https://github.com/user-attachments/assets/1dfa25f9-af7e-45d8-92a5-13f0b6534135)


## Networking Core Protocols

### WHOIS

- Sử dụng WHOIS để tra cứu thông tin của bất cứ tên miền nào đã đăng ký bằng một trong các dịch vụ trực tuyến.

![image](https://github.com/user-attachments/assets/007dd1f4-3a24-4d18-b075-5ef043775459)

### HTTPS

- HTTP là viết tắt của Hypertext Transfer Protocol; chữ S trong HTTPS là viết tắt của Secure. Giao thức này dựa trên TCP và xác định cách trình duyệt web của bạn giao tiếp với máy chủ web.

- Một số phương thức:

  - GET lấy dữ liệu từ máy chủ, chẳng hạn như tệp HTML hoặc hình ảnh.
    
  - POST cho phép chúng ta gửi dữ liệu mới tới máy chủ, chẳng hạn như gửi biểu mẫu hoặc tải tệp lên.
    
  - PUT được sử dụng để tạo tài nguyên mới trên máy chủ và cập nhật và ghi đè thông tin hiện có.
    
  - DELETE, như tên gọi của nó, được sử dụng để xóa một tệp hoặc tài nguyên được chỉ định trên máy chủ.

- HTTP và HTTPS thường sử dụng cổng TCP 80 và 443, ít phổ biến hơn là các cổng khác như 8080 và 8443.


### FTP

- Giao thức truyền tệp ( FTP ) được thiết kế để truyền tệp. Do đó, FTP rất hiệu quả để truyền tệp và khi tất cả các điều kiện đều như nhau, nó có thể đạt tốc độ cao hơn HTTP .

- Các lệnh ví dụ được định nghĩa bởi giao thức FTP là:
  
  - USER is used to input the username
  
  - PASS is used to enter the password
  
  - RETR (retrieve) is used to download a file from the FTP server to the client.
  
  - STOR (store) is used to upload a file from the client to the FTP server.

- FTP server listens on TCP port 21 by default; data transfer is conducted via another connection from the client to the server.


### SMTP

- Giao thức truyền thư đơn giản ( SMTP ) xác định cách máy khách thư giao tiếp với máy chủ thư và cách máy chủ thư giao tiếp với máy chủ thư khác.

- Một số lệnh mà máy khách thư của bạn sử dụng khi chuyển email đến máy chủ SMTP :

  - `HELO` hoặc `EHLO` khởi tạo một phiên SMTP
    
  - `MAIL FROM` chỉ định địa chỉ email của người gửi
    
  - `RCPT TO` chỉ định địa chỉ email của người nhận
    
  - `DATA` chỉ ra rằng máy khách sẽ bắt đầu gửi nội dung của tin nhắn email
 
  - `.`được gửi trên một dòng riêng để chỉ ra sự kết thúc của tin nhắn email

![image](https://github.com/user-attachments/assets/026d24d7-2c5d-41a5-9f51-2897f019a907)


### POP3

- Post Office Protocol Version 3 (POP3) là một giao thức thay thế để nhận email tải email từ máy chủ xuống thiết bị cục bộ. Sử dụng POP3, người nhận không thể truy cập lại email của họ từ một thiết bị khác vì chúng được lưu trữ cục bộ và sau đó bị xóa khỏi máy chủ email.

- Một số lệnh POP3 phổ biến là:

  - `USER <username>` xác định người dùng

  - `PASS <password>` cung cấp mật khẩu của người dùng

  - `STAT` yêu cầu số lượng tin nhắn và tổng kích thước

  - `LIST` liệt kê tất cả các tin nhắn và kích thước của chúng

  - `RETR <message_number>` lấy lại tin nhắn đã chỉ định

  - `DELE <message_number>` đánh dấu một tin nhắn để xóa

  - `QUIT` kết thúc phiên POP3 bằng cách áp dụng các thay đổi, chẳng hạn như xóa

![image](https://github.com/user-attachments/assets/6f1ad427-60aa-4faa-9fc2-2b23ed549b03)


### IMAP

- Giao thức truy cập tin nhắn Internet (IMAP) là một giao thức để nhận email. Các giao thức chuẩn hóa các quy trình kỹ thuật để máy tính và máy chủ có thể kết nối với nhau bất kể chúng có sử dụng cùng phần cứng hoặc phần mềm hay không.

- IMAP cho phép đồng bộ hóa các tin nhắn đã đọc, đã di chuyển và đã xóa. IMAP khá tiện lợi khi bạn kiểm tra email của mình qua nhiều máy khách. Không giống như POP3 , có xu hướng giảm thiểu dung lượng lưu trữ máy chủ khi email được tải xuống và xóa khỏi máy chủ từ xa, IMAP có xu hướng sử dụng nhiều dung lượng lưu trữ hơn vì email được lưu trên máy chủ và được đồng bộ hóa trên các máy khách email.

- Một số lệnh:

  - `LOGIN <username> <password>` xác thực người dùng

  - `SELECT <mailbox>` chọn thư mục hộp thư để làm việc

  - `FETCH <mail_number> <data_item_name>` Ví dụ fetch 3 body[]để lấy tin nhắn số 3, tiêu đề và nội dung.

  - `MOVE <sequence_set> <mailbox>` di chuyển các tin nhắn đã chỉ định đến hộp thư khác

  - `COPY <sequence_set> <data_item_name>` sao chép các tin nhắn đã chỉ định vào hộp thư khác

  - `LOGOUT` đăng xuất

![image](https://github.com/user-attachments/assets/2cfcef07-6248-434d-8ccd-68e889fc3a66)

## Network Secure Protocols

### TLS

- TLS là một giao thức mật mã hoạt động ở lớp vận chuyển của mô hình OSI. Nó cho phép giao tiếp an toàn giữa máy khách và máy chủ qua mạng không an toàn. Khi nói đến an toàn, chúng tôi muốn nói đến tính bảo mật và tính toàn vẹn; TLS đảm bảo rằng không ai có thể đọc hoặc sửa đổi dữ liệu được trao đổi.

- Bước đầu tiên đối với mọi máy chủ (hoặc máy khách) cần xác định chính nó là lấy chứng chỉ TLS đã ký. Nói chung, quản trị viên máy chủ tạo Yêu cầu ký chứng chỉ (CSR) và gửi đến Cơ quan cấp chứng chỉ (CA); CA xác minh CSR và cấp chứng chỉ kỹ thuật số. Sau khi nhận được chứng chỉ (đã ký), chứng chỉ này có thể được sử dụng để xác định máy chủ (hoặc máy khách) với những người khác, những người có thể xác nhận tính hợp lệ của chữ ký. Để máy chủ xác nhận tính hợp lệ của chứng chỉ đã ký, các chứng chỉ của cơ quan ký cần được cài đặt trên máy chủ. Trong thế giới phi kỹ thuật số, điều này tương tự như việc nhận dạng dấu của nhiều cơ quan khác nhau.

- Các đặc điểm chính của TLS:

  - Mã hóa dữ liệu để ngăn chặn nghe lén.

  - Xác thực máy chủ bằng chứng chỉ số (SSL/TLS Certificate).

  - Đảm bảo toàn vẹn dữ liệu bằng thuật toán băm như SHA-256.

  - Phiên bản mới nhất: TLS 1.3 (Nhanh hơn và bảo mật hơn).

### HTTPS

- HTTPS là viết tắt của Hypertext Transfer Protocol Secure. Về cơ bản, nó là HTTP qua TLS. Do đó, yêu cầu một trang qua HTTPS sẽ yêu cầu ba bước sau (sau khi giải quyết tên miền):

  - Thiết lập bắt tay ba chiều TCP với máy chủ mục tiêu

  - Thiết lập phiên TLS

  - Giao tiếp bằng giao thức HTTP 

### SMTPS,POP3S, IMAPS

- Thêm TLS vào SMTP , POP3 và IMAP không khác gì thêm TLS vào HTTP . Tương tự như cách HTTP có thêm chữ S cho Secure và trở thành HTTPS, SMTP , POP3 và IMAP lần lượt trở thành SMTPS, POP3S và IMAPS. Sử dụng các giao thức này qua TLS không khác gì sử dụng HTTP qua TLS; do đó, hầu hết các điểm từ cuộc thảo luận về HTTPS đều áp dụng cho các giao thức này.

### SSH

- Secure Shell (SSH) là giao thức mạng mã hóa được sử dụng trong giao tiếp an toàn giữa các thiết bị. SSH mã hóa dữ liệu bằng các thuật toán mã hóa, chẳng hạn như Advanced Encryption System (AES) và thường được sử dụng khi đăng nhập từ xa vào máy tính hoặc máy chủ.

- Secure authentication:  Bên cạnh xác thực bằng mật khẩu, SSH hỗ trợ khóa công khai và xác thực hai yếu tố.

- Confidentiality: OpenSSH cung cấp mã hóa đầu cuối, bảo vệ chống lại việc nghe lén. Hơn nữa, nó thông báo cho bạn về các khóa máy chủ mới để bảo vệ chống lại các cuộc tấn công trung gian.

- Integrity: Ngoài việc bảo vệ tính bảo mật của dữ liệu trao đổi, mật mã còn bảo vệ tính toàn vẹn của lưu lượng truy cập.

- Tunneling: SSH có thể tạo một “đường hầm” an toàn để định tuyến các giao thức khác thông qua SSH . Thiết lập này dẫn đến kết nối giống như VPN .

- X11 Forwarding: Nếu bạn kết nối với hệ thống giống Unix có giao diện người dùng đồ họa, SSH cho phép bạn sử dụng ứng dụng đồ họa qua mạng.

### VPN

- Mạng riêng ảo là một cách tạo ra một "đường hầm" an toàn giữa hai mạng. Ví dụ, bạn sử dụng VPN trên TryHackMe để truy cập vào mạng riêng mà các máy hoạt động. VPN cũng thường được sử dụng để nhân viên đăng nhập vào nơi làm việc của họ khi họ không có mặt tại chỗ (chẳng hạn như làm việc tại nhà hoặc đi công tác). VPN cũng được sử dụng khi mạng (chẳng hạn như quán cà phê) không cung cấp mã hóa và là một cách tuyệt vời để ngăn người khác đọc lưu lượng mạng của bạn.

- Trong sơ đồ mạng bên dưới, chúng ta thấy hai người dùng từ xa sử dụng máy khách VPN để kết nối với máy chủ VPN trong nhánh chính. Trong trường hợp này, máy khách VPN kết nối một thiết bị duy nhất.

![image](https://github.com/user-attachments/assets/79c45d50-1ecb-432c-9f7f-be1bb6b19b13)
