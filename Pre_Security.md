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

### ***DNS***

Hệ thống tên miền (DNS) là giao thức chịu trách nhiệm phân giải tên máy chủ, chẳng hạn như tryhackme.com, thành địa chỉ IP tương ứng của chúng.

#### ***Hệ thống phân cấp miền***
- ***TLD (Top-Level Domain)***: TLD là phần bên phải nhất của tên miền. Ví dụ, TLD của tryhackme.com là  .com . Có hai loại TLD, gTLD (Generic Top Level) và ccTLD (Country Code Top Level Domain).  gTLD có nghĩa là cho người dùng biết mục đích của tên miền ví dụ .edu dành cho giáo dục, .gov dành cho chính phủ.... ccTLD được sử dụng cho mục đích địa lý, ví dụ, .ca dành cho các trang web có trụ sở tại Canada, .co.uk dành cho các trang web có trụ sở tại Vương quốc Anh, v.v 

- ***Second-Level Domain***: Lấy tryhackme.com làm ví dụ, phần .com là TLD, và tryhackme là Tên miền cấp hai. Khi đăng ký tên miền, tên miền cấp hai bị giới hạn ở 63 ký tự + TLD và chỉ có thể sử dụng az 0-9 và dấu gạch nối

- ***Subdomain***: Tên miền phụ nằm ở phía bên trái của tên miền cấp hai bằng cách sử dụng dấu chấm để phân tách; ví dụ, trong tên admin.tryhackme.com, phần quản trị là tên miền phụ.

#### ***Các loại bản ghi DNS***

- ***A Record***: phân giải thành địa chỉa IPv4

- ***AAAA Record***: phân giải thành địa chỉa IPv6

- ***CNAME Record***: Các bản ghi này giải quyết một tên miền khác, ví dụ, cửa hàng trực tuyến của TryHackMe có tên miền phụ store.tryhackme.com trả về bản ghi CNAME shops.shopify.com . Sau đó, một yêu cầu DNS khác sẽ được thực hiện tới shops.shopify.com để tìm ra địa chỉ IP.

- ***MX Record***: Các bản ghi này giải quyết địa chỉ của các máy chủ xử lý email cho tên miền bạn đang truy vấn, ví dụ phản hồi bản ghi MX cho tryhackme.com sẽ trông giống như  alt1.aspmx.l.google.com

- ***TXT Record***: Bản ghi TXT là các trường văn bản tự do, nơi có thể lưu trữ bất kỳ dữ liệu dạng văn bản nào. Bản ghi TXT có nhiều mục đích sử dụng, nhưng một số mục đích phổ biến có thể là liệt kê các máy chủ có thẩm quyền gửi email thay mặt cho tên miền (điều này có thể giúp chống lại thư rác và email giả mạo). Chúng cũng có thể được sử dụng để xác minh quyền sở hữu tên miền khi đăng ký dịch vụ của bên thứ ba.

#### ***Quy trình***

![image](https://github.com/user-attachments/assets/8e54d510-2f9a-422e-b937-f77bbdc34573)


### ***HTTP***

Giao thức truyền siêu văn bản (HTTP) là giao thức chỉ định cách trình duyệt web và máy chủ web giao tiếp

HTTPS là phiên bản bảo mật của HTTP . Dữ liệu HTTPS được mã hóa nên không chỉ ngăn người khác nhìn thấy dữ liệu bạn đang nhận và gửi mà còn đảm bảo rằng bạn đang trao đổi với đúng máy chủ web chứ không phải thứ gì đó mạo danh.

Format URL: ***scheme://user:password@host:port/path?parameter=value***

Cách thức hoạt động của web có thể hiểu đơn giản thông qua hình sau:

![image](https://github.com/user-attachments/assets/e0c90c63-2aea-4d5f-9a1b-d11ac785b99a)

## **Cơ bản về Linux**

***Các lệnh cơ bản***: echo, ls, whoami, mkdir, touch, head, grep, find, tail, more, which, sudo, cat, pwd, wc, rm, file, mv, chmod, su, chown, ps, top, kill,...

***Các toán tử***: '>', '>>', '&', '&&', '|'

## **Cơ bản về Windows**

***Giới thiệu về giao diện của Windows***

***Các quyền trong Windows***: Full Controll, Read & Execute, Read, Write, Modify, List folder contents

Thư mục Windows ( C:\Windows) theo truyền thống được biết đến là thư mục chứa hệ điều hành Windows. 

Đây là nơi các biến môi trường, cụ thể hơn là các biến môi trường hệ thống, phát huy tác dụng.  Mặc dù chưa được thảo luận, biến môi trường hệ thống cho thư mục Windows là %windir%

Thư mục System32 chứa các tập tin quan trọng có vai trò sống còn đối với hệ điều hành.

Để bảo vệ người dùng cục bộ với các đặc quyền như vậy, Microsoft đã giới thiệu Kiểm soát tài khoản người dùng ( UAC ). Khái niệm này lần đầu tiên được giới thiệu với Windows Vista tồn tại trong thời gian ngắn  và tiếp tục với các phiên bản Windows tiếp theo. Khi người dùng có loại tài khoản là quản trị viên đăng nhập vào hệ thống, phiên hiện tại không chạy với quyền nâng cao. Khi một hoạt động yêu cầu quyền cấp cao hơn cần thực thi, người dùng sẽ được nhắc xác nhận xem họ có cho phép hoạt động đó chạy hay không. Tên người dùng và mật khẩu cho người dùng chuẩn. Nó hiển thị trong lusrmgr.msc.


