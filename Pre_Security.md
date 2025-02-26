# *<p align="center"><b>Pre Security</b></p>*
Để bắt đầu với nghành Cyber Security, điều đầu tiên chúng ta cần phải có hiểu biết về ngành mà mình theo đuổi, học kiến thức nền tảng về Network, cách thức hoạt động của thế giới Web, hiểu biết cơ bản các hệ điều hành phổ biến như Windows, Linux.

## **Giới thiệu về Cyber Security**
Ngành Cyber Security là ngành nghề rất có triển vọng trong tương lai, với các lĩnh vực đáng chú ý như:

-- Chuyên viên phân tích an ninh (Security Analyst)

-- Kỹ sư an ninh (Security Enginneer)

-- Phân tích mã độc (Malware Analyst)

-- Kiểm thử xâm nhâp (Penetration Testing)

-- Red Team

-- Blue Team...


## Network
Mạng gồm các thiết bị điện tử được kết nối với nhau.

Internet giống như tập hợp của rất nhiều mạng lại. Các mạng này gọi là mạng riêng, Các mạng kết nối với các mạng nhỏ gọi là mạng công cộng.

Để xác định, định tuyến các thiết bị trên mạng ta cần có địa chỉ IP và MAC. IP có giá trị global còn MAC chỉ có giá trị trong các mạng local thôi.

Trong phần này chúng ta sẽ được tìm hiểu về mạng LAN, cách định tuyén trên mạng, và cách cấp phat địa chỉ IP động.

Quan trọng hơn cả là chúng ta sẽ tiếp cận với mô hình OSI.

Mô hình OSI có 7 lớp:

-- Layer 1: Physical (Lớp vật lý) đây là lớp thấp nhất chịu trách nghiệm truyền dữ liệu giữa các thiết bị phần cúng dưới dạng các bit 0 và 1.

-- Layer 2: Data Link (Lớp liên kêt) dữ liệu tập trung vào việc xác định địa chỉ vật lý của quá trình truyền. Nó nhận một gói tin từ lớp mạng (bao gồm địa chỉ IP cho máy tính từ xa) và thêm vào địa chỉ MAC (Media Access Control) vật lý của điểm cuối nhận.

-- Layer 3: Network (Lớp mạng) trách nghiệm chính là định tuyến dữ liệu.

-- Layer 4: Transport (Lớp vận chuyển) khi dữ liệu gửi giữa hai thiết bị nó sẽ tuân theo 2 giao thứ là TCP và UDP.

-- Layer 5: Session (Lớp phiên) tạo và duy trì kết nối với máy tính khác mà dữ liệu được gửi đến,đóng kết nối nếu nó không được sử dụng trong một thời gian hoặc nếu nó bị mất, các phiên là duy nhất — nghĩa là dữ liệu không thể di chuyển qua các phiên khác nhau mà chỉ có thể di chuyển qua từng phiên.

-- Layer 6: Presentation (Lớp trình diễn) là lớp mà quá trình chuẩn hóa bắt đầu diễn ra. 

-- Layer 7: Application (Lớp ứng dụng) là tầng mà các giao thức và quy tắc được áp dụng để xác định cách người dùng tương tác với dữ liệu được gửi hoặc nhận.

Packets(gói) và frames(khung): là những phần dữ liệu nhỏ, khi kết hợp lại với nhau, tạo thành một phần thông tin hoặc tin nhắn lớn hơn. Tuy nhiên, chúng là hai thứ khác nhau trong mô hình OSI. Khung nằm ở lớp 2 - lớp liên kết dữ liệu, nghĩa là không có thông tin nào như địa chỉ IP. Còn packets là đơn vị nằm ở lớp 3 (Network)

Một số trường tiêu đề đáng chú ý trong gói tin: Time-to-live (Thời gian để sống), Checksum (Kiểm tra), địa chỉ IP nguồn, địa chỉ IP đích.

Quá tình bắt tay 3 bước giả sử với Alice(Client) và Bob(Server):

-- SYN: Client gửi yêu cầu kết nối tới Server

-- SYN/ACK: Server phản hồi ACK và gửi SYN để hỏi client sẵn sàng kết nối không.

-- ACK: client gửi ACK nếu sẵn sàng kết nối


![image](https://github.com/user-attachments/assets/3f8cf448-c3e0-4903-bf6a-1bb35d18bf15)

Để kết thúc thì client sẽ gửi gói tin có cờ FIN tới Server và Server sẽ xác nhận rồi gửi lại gói tin ACK và FIN, sau đó client xác nhận phẩn hồi bằng gói tin chứa cờ ACK.

![image](https://github.com/user-attachments/assets/1484279b-c7ab-44da-b360-828ea3a6cce4)

Không giống như giao thức TCP, UDP là  giao thức không trạng thái, không yêu cầu kết nối liên tục giữa hai thiết bị để dữ liệu được gửi. Ví dụ, bắt tay ba chiều không xảy ra, cũng không có bất kỳ sự đồng bộ hóa nào giữa hai thiết bị. Mô hình giao tiếp ta có thể hình dung như hình bên dưới:

![image](https://github.com/user-attachments/assets/da911f94-11f1-4af1-bc89-258fd28d62aa)

Tường lửa là một thiết bị trong mạng có trách nhiệm xác định lưu lượng nào được phép vào và ra. Hãy nghĩ về tường lửa như là bảo mật biên giới cho mạng. Người quản trị có thể cấu hình tường lửa để  cho phép  hoặc  từ chối  lưu lượng vào hoặc ra khỏi mạng dựa trên nhiều yếu tố:

-- Lưu lượng truy cập đến từ đâu? ( tường lửa có được yêu cầu chấp nhận/từ chối lưu lượng truy cập từ một mạng cụ thể không?)

-- Lưu lượng truy cập sẽ đi đến đâu? ( tường lửa có được yêu cầu chấp nhận/từ chối lưu lượng truy cập đến một mạng cụ thể không?)

-- Lưu lượng truy cập đến cổng nào? ( tường lửa có được yêu cầu chấp nhận/từ chối lưu lượng truy cập đến cổng 80 không?)

-- Lưu lượng truy cập đang sử dụng giao thức nào? ( tường lửa đã được yêu cầu chấp nhận/từ chối lưu lượng truy cập UDP , TCP hay cả hai chưa?)

Mạng  riêng ảo  (hay  gọi tắt là VPN ) là công nghệ cho phép các thiết bị trên các mạng riêng biệt giao tiếp an toàn bằng cách tạo ra một đường dẫn chuyên dụng giữa các thiết  bị  với nhau qua Internet (gọi là đường hầm). Các thiết bị được kết nối trong đường hầm này tạo thành mạng riêng của chúng.

![image](https://github.com/user-attachments/assets/4dbfc01b-c0db-4ad3-8d08-53dea36eb6e6)

## **Cách thức hoạt động của thế giới Web**
***DNS***

***HTTP***

***Cách thức hoạt động***

## **Cơ bản về Linux**

## **Cơ bản về Windows**
