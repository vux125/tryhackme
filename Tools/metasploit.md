*Metasploit*

***Metasploit là một framework khai thác được sử được sử dụng rộng rãi. Metasploit là công cụ hữu ích hỗ trợ mọi giai đoạn của quá trình thử nghiệm thâm nhập, từ thu nhập thông tin đến sau khi khai thác.***
# Main Components of Metasploit

## Auxiliary

- Các module hỗ trợ như: Scanners, crawlers và fuzzers.

![image](https://github.com/user-attachments/assets/e6d41a7d-4805-499d-91e7-57cb84b81c73)

## Encoders

- Cho phép mã hóa phần khai thác và payload với hi vong nó sẽ vượt qua các giải pháp chống vi rút dựa trên chữ ký số.

![image](https://github.com/user-attachments/assets/e747c305-2220-45c9-bbe8-44b6769903c5)

## Evasion

- Khác encoder mã hóa payload không được coi là một nỗ lực trưc tiếp để trốn tránh phần mêm diệt virut. Các module evasion sẽ cố gắng trốn tránh khỏi phân mềm diệt virut

![image](https://github.com/user-attachments/assets/b7ab7ba7-1ff7-4851-8ca7-ac9b33de07e2)

## Exploits

- Chứa các module khai thác mục tiêu

![image](https://github.com/user-attachments/assets/dd96998b-dfbc-4ccb-8476-757509f2c20d)

## NOP 

- NOP không làm gì cả theo đúng nghĩa đen. Chúng thừong được sử dụng nhự một bộ đệm để đạt được kích thước tải trọng nhất quán.

![image](https://github.com/user-attachments/assets/399ae273-5ca0-4787-8fd8-b6f04a296b3d)

## Payloads

- Payload là các mã sẽ chạy trên hệ thống mục tiêu.

![image](https://github.com/user-attachments/assets/ccc127a2-b7d6-4804-bd41-8c6b7c4a31e8)

- Có bốn thư mục khác nhau trong phần tải trọng:

  - `adapters`: Bộ điều hợp gói các payload đơn lẻ để chuyển đổi chúng thành các định dạng khác nhau. Ví dụ, một payload đơn lẻ bình thường có thể được gói bên trong bộ điều hợp Powershell , bộ điều hợp này sẽ tạo ra một lệnh powershell duy nhất để thực thi payload.

  - `Singles`: Tải trọng độc lập (thêm người dùng, khởi chạy notepad.exe, v.v.) không cần tải xuống thành phần bổ sung để chạy.
 
  - `Stagers`: Chịu trách nhiệm thiết lập kênh kết nối giữa Metasploit và hệ thống mục tiêu. Hữu ích khi làm việc với các payload được dàn dựng. “Staged payload” trước tiên sẽ tải một stager lên hệ thống mục tiêu rồi tải phần còn lại của payload (stage) xuống. Điều này mang lại một số lợi thế vì kích thước ban đầu của payload sẽ tương đối nhỏ so với payload đầy đủ được gửi cùng một lúc.
 
  - `Stages`: Được tải xuống bởi stager. Điều này cho phép sử dụng payload lớn hơn

## POST

- Các mô-đun Post sẽ hữu ích ở giai đoạn cuối cùng của quy trình kiểm tra thâm nhập được liệt kê ở trên, sau khi khai thác.

![image](https://github.com/user-attachments/assets/6c86d2ee-2baa-4fd1-9ad9-df88902c554a)

# Msfconsole

- Khởi chạy bằng câu lệnh `msfconsole`

- Hỗ trợ hầu hết các lệnh Linux

- Sử dụng lệnh help đơn lẻ hoặc cho một lệnh cụ thể để xem hướng dẫn

- Lệnh `history` để xem các câu lệnh đã xem trước đó.

- Lệnh `use` để sử dụng một module nào đấy.

- Lệnh `show` có thể được sử dụng trong bất kỳ ngữ cảnh nào theo sau là một loại mô-đun (phụ trợ, tải trọng, khai thác, v.v.) để liệt kê các mô-đun khả dụng.

- Lệnh `info` để biết thêm thông tin về module

- Lệnh `search` sẽ tìm kiếm cơ sở dữ liệu Metasploit Framework cho các mô-đun có liên quan đến tham số tìm kiếm đã cho.

## Scanning

- Port Scanning: Metasploit có một số mô-đun để quét các cổng mở trên hệ thống và mạng đích. Có thể liệt kê các mô-đun quét cổng tiềm năng có sẵn bằng lệnh `search portscan`.

- Nhận dạng dịch vụ UDP: Mô-đun này scanner/discovery/udp_sweep sẽ cho phép bạn nhanh chóng xác định các dịch vụ chạy qua UDP (Giao thức dữ liệu người dùng). Như bạn có thể thấy bên dưới, mô-đun này sẽ không thực hiện quét toàn diện tất cả các dịch vụ UDP có thể có nhưng cung cấp một cách nhanh chóng để xác định các dịch vụ như DNS hoặc NetBIOS .

![image](https://github.com/user-attachments/assets/0b73d218-3298-4f2d-af2d-6ed8d8d73a27)

- Quét SMB: Metasploit cung cấp một số mô-đun phụ trợ hữu ích cho phép chúng ta quét các dịch vụ cụ thể. Đặc biệt hữu ích trong mạng công ty sẽ là `smb_enumshares` và `smb_version`

## Metasploit Database

- Metasploit có chức năng cơ sở dữ liệu giúp đơn giản hóa việc quản lý dự án và tránh nhầm lẫn có thể xảy ra khi thiết lập giá trị tham số.

- Để sử dụng csdl ta thực hieenjc ác bước sau:

  - Khởi dộng csdl bằng lệnh `systemctl start postgresql`
 
  - Khởi tạo csdl Metasploit bằng lệnh `msfdb init`
 
  - Khởi chạy `msfconsole` và sau khi khởi chạy msfconsole thì kiểm tra trạng thái csdl bằng lệnh `db_status`
 
  - Liệt kê không gian lam việc bằng lệnh `workspace`
 
  - Thêm không gian làm việc bằng tham số -a hoặc xóa không gian lam việc bằng -d. Ví dụ: `workspace -a mywork`, `workspace -d mywork`

 - Ví dụ chạy nmap với lệnh `db-nmap` tất cả kết quả sẽ được lưu vào csdl

## Quét lỗ hổng

- Metasploit cho phép bạn nhanh chóng xác định một số lỗ hổng quan trọng có thể được coi là "low hanging fruit". Thuật ngữ "low hanging fruit" thường ám chỉ các lỗ hổng dễ nhận biết và dễ khai thác có khả năng cho phép bạn có được chỗ đứng trên hệ thống và trong một số trường hợp, có được các đặc quyền cấp cao như root hoặc quản trị viên.

- Việc tìm lỗ hổng bằng Metasploit sẽ phụ thuộc rất nhiều vào khả năng quét và dấu vết mục tiêu của bạn. Bạn càng giỏi ở những giai đoạn này, Metasploit càng cung cấp cho bạn nhiều tùy chọn hơn. Ví dụ, nếu bạn xác định được một dịch vụ VNC đang chạy trên mục tiêu, bạn có thể sử dụng searchchức năng trên Metasploit để liệt kê các mô-đun hữu ích. Kết quả sẽ chứa các mô-đun payload và post. Ở giai đoạn này, những kết quả này không hữu ích lắm vì chúng tôi vẫn chưa phát hiện ra một khai thác tiềm năng nào để sử dụng. Tuy nhiên, trong trường hợp của VNC, có một số mô-đun máy quét mà chúng tôi có thể sử dụng.

## Exploit

- Bạn có thể tìm kiếm các khai thác bằng `search`, lấy thêm thông tin về khai thác bằng `info` và khởi chạy khai thác bằng `exploit` . Mặc dù bản thân quá trình này rất đơn giản, hãy nhớ rằng kết quả thành công phụ thuộc vào sự hiểu biết sâu sắc về các dịch vụ đang chạy trên hệ thống mục tiêu.
 
- Hầu hết các khai thác sẽ có một tải trọng mặc định được cài đặt trước. Tuy nhiên, bạn luôn có thể sử dụng `show payloads` để liệt kê các lệnh khác mà bạn có thể sử dụng với khai thác cụ thể đó.

![image](https://github.com/user-attachments/assets/6e048a1d-d10d-4e1d-9e07-19a11b492b6e)

- Lệnh `set payloads` để thiết lập payload cho module khai thác.

- Lệnh `show options` sẽ show ra những tham số, chúng ta có thể thiết lập các tham số này trước khi thực hiện khai thác.

- Sử dụng `run` hoặc `exploit` để thực hiện quá trình khai thác.

- Chạy nền bằng `Ctrl + Z` hoặc hủy bằng `Ctrl + C`

- Lệnh `sessions` sẽ liệt kê tất cả các phiên đang chạy

- Để tương tác với 1 phiên sử dụng lênh `sessions -i <id phiên>`

## msfvenom

- Msfvenom, thay thế Msfpayload và Msfencode, cho phép bạn tạo payload.

- Msfvenom sẽ cho phép bạn truy cập tất cả các payload có sẵn trong  khuôn khổ Metasploit . Msfvenom cho phép bạn tạo payload ở nhiều định dạng khác nhau ( PHP , exe, dll , elf, v.v.) và cho nhiều hệ thống mục tiêu khác nhau (Apple, Windows, Android, Linux , v.v.).

![image](https://github.com/user-attachments/assets/69842c19-0920-481f-8977-994b9bd00c04)

- Bạn có thể tạo các payload độc lập (ví dụ: tệp thực thi Windows cho Meterpreter ) hoặc nhận định dạng thô có thể sử dụng (ví dụ: python). `msfvenom --list formats` có thể được sử dụng để liệt kê các định dạng đầu ra được hỗ trợ

- Các bộ mã hóa không nhằm mục đích bỏ qua phần mềm diệt vi-rút được cài đặt trên hệ thống mục tiêu. Như tên gọi của chúng, chúng mã hóa tải trọng. Mặc dù có thể hiệu quả đối với một số phần mềm diệt vi-rút, nhưng sử dụng các kỹ thuật che giấu hiện đại hoặc các phương pháp học để đưa shellcode vào là giải pháp tốt hơn cho vấn đề này. Ví dụ bên dưới cho thấy cách sử dụng mã hóa với -etham số. Phiên bản PHP của Meterpreter được mã hóa ở dạng Base64 và định dạng đầu ra là raw.

![image](https://github.com/user-attachments/assets/96da5bce-22fd-4b02-a312-940dcd1e8289)

- Handler:

  - Tương tự như khai thác sử dụng shell ngược, bạn sẽ cần có khả năng chấp nhận các kết nối đến được tạo ra bởi tải trọng MSFvenom. Khi sử dụng mô-đun khai thác, phần này được xử lý tự động bởi mô-đun khai thác, bạn sẽ nhớ cách payload optionstiêu đề xuất hiện khi thiết lập shell ngược. Thuật ngữ thường được sử dụng để nhận kết nối từ mục tiêu là 'catching a shell'. Shell ngược hoặc lệnh gọi lại Meterpreter được tạo ra trong tải trọng MSFvenom của bạn có thể dễ dàng bị bắt bằng trình xử lý.

  - Kịch bản sau đây có thể quen thuộc; chúng ta sẽ khai thác lỗ hổng tải tệp lên có trong DVWA (Ứng dụng web dễ bị tấn công). Các bước khai thác là:

    1. Tạo shell PHP bằng MSFvenom
      
    2. Bắt đầu trình xử lý Metasploit

    3.  Thực hiện shell PHP


- MSFvenom sẽ yêu cầu một payload, địa chỉ IP của máy cục bộ và cổng cục bộ mà payload sẽ kết nối.

![image](https://github.com/user-attachments/assets/e23292a7-4e83-4406-83de-b568494822a5)

- Chúng ta sẽ sử dụng Multi Handler để nhận kết nối đến. Module có thể được sử dụng với lệnh `use exploit/multi/handler`.

- Trình xử lý đa năng hỗ trợ tất cả các tải trọng Metasploit và có thể được sử dụng cho cả Meterpreter cũng như các shell thông thường.

- Để sử dụng mô-đun, chúng ta sẽ cần thiết lập giá trị tải trọng ( php/reverse_phptrong trường hợp này), giá trị LHOST và LPORT.

![image](https://github.com/user-attachments/assets/2100fb9c-7ab2-4f53-a041-81856b24753a)

- Khi mọi thứ đã được thiết lập, chúng ta sẽ run xử lý và chờ kết nối đến.

# Meterpreter

- Meterpreter là một payload Metasploit hỗ trợ quá trình kiểm tra thâm nhập với nhiều thành phần có giá trị. Meterpreter sẽ chạy trên hệ thống mục tiêu và hoạt động như một tác nhân trong kiến ​​trúc lệnh và điều khiển. Bạn sẽ tương tác với hệ điều hành và tệp mục tiêu và sử dụng các lệnh chuyên biệt của Meterpreter .

- Meterpreter chạy trên hệ thống đích nhưng không được cài đặt trên đó. Nó chạy trong bộ nhớ và không tự ghi vào đĩa trên mục tiêu. Tính năng này nhằm mục đích tránh bị phát hiện trong quá trình quét vi-rút. Theo mặc định, hầu hết các phần mềm diệt vi-rút sẽ quét các tệp mới trên đĩa (ví dụ: khi bạn tải xuống tệp từ internet) Meterpreter chạy trong bộ nhớ ( RAM - Bộ nhớ truy cập ngẫu nhiên) để tránh phải ghi tệp vào đĩa trên hệ thống đích (ví dụ: meterpreter .exe). Theo cách này, Meterpreter sẽ được coi là một quy trình và không có tệp trên hệ thống đích.

-  Meterpreter cũng hướng đến mục tiêu tránh bị phát hiện bởi các giải pháp IPS (Hệ thống phòng ngừa xâm nhập) và IDS (Hệ thống phát hiện xâm nhập) dựa trên mạng bằng cách sử dụng giao tiếp được mã hóa với máy chủ nơi Metasploit chạy (thường là máy tấn công của bạn). Nếu tổ chức mục tiêu không giải mã và kiểm tra lưu lượng được mã hóa (ví dụ: HTTPS) đến và đi khỏi mạng cục bộ, các giải pháp IPS và IDS sẽ không thể phát hiện các hoạt động của tổ chức đó.

-  Cách dễ nhất để biết về các phiên bản Meterpreter khả dụng là liệt kê chúng bằng msfvenom, như minh họa bên dưới. 

![image](https://github.com/user-attachments/assets/fdab8121-82a3-4e3d-a00e-7e118734512b)

- Danh sách sẽ hiển thị các phiên bản Meterpreter có sẵn cho các nền tảng sau:

  1. Android
  
  2. Apple iOS
  
  3. Java
  
  4. Linux
  
  5. OSX
  
  6. PHP
  
  7.Python
  
  8. Windows

- Quyết định của bạn về việc sử dụng phiên bản Meterpreter nào sẽ chủ yếu dựa trên ba yếu tố;

  - Hệ điều hành mục tiêu (Hệ điều hành mục tiêu là Linux hay Windows? Có phải là thiết bị Mac không? Có phải là điện thoại Android không? v.v.)

  - Các thành phần có sẵn trên hệ thống mục tiêu (Python đã được cài đặt chưa? Đây có phải là trang web PHP không ? v.v.)

  - Các loại kết nối mạng bạn có thể có với hệ thống mục tiêu (Chúng có cho phép kết nối TCP thô không ? Bạn chỉ có thể có kết nối ngược HTTPS? Địa chỉ IPv6 không được giám sát chặt chẽ như địa chỉ IPv4? v.v.) 

## Lệnh trong Meterpreter

- Khi gõ help vào bất kỳ phiên Meterpreter nào (hiển thị tại meterpreter>dấu nhắc) sẽ liệt kê tất cả các lệnh có sẵn.

![image](https://github.com/user-attachments/assets/f2250f1f-4cab-47ab-a230-b9adbad7220e)

- Mỗi phiên bản Meterpreter sẽ có các tùy chọn lệnh khác nhau, vì vậy chạy lệnh `help` luôn là một ý tưởng hay. Lệnh là các công cụ tích hợp có sẵn trên Meterpreter . Chúng sẽ chạy trên hệ thống đích mà không cần tải bất kỳ tập lệnh hoặc tệp thực thi bổ sung nào.

- Meterpreter sẽ cung cấp cho bạn ba loại công cụ chính;

  - Các lệnh tích hợp

  - Công cụ Meterpreter

  - Viết kịch bản Meterpreter

- Các lệnh cốt lõi sẽ hữu ích để điều hướng và tương tác với hệ thống mục tiêu. Sau đây là một số lệnh thường dùng nhất. Hãy nhớ kiểm tra tất cả các lệnh có sẵn khi chạy lệnh help sau khi phiên Meterpreter bắt đầu.

  - Các lệnh cốt lõi

    + background: Bối cảnh phiên hiện tại
  
    + exit: Kết thúc phiên Meterpreter
  
    + guid: Lấy GUID phiên (Mã định danh duy nhất toàn cầu)
  
    + help: Hiển thị menu trợ giúp
  
    + info: Hiển thị thông tin về mô-đun Post
  
    + irb: Mở một shell Ruby tương tác trên phiên hiện tại
  
    + load: Tải một hoặc nhiều tiện ích mở rộng Meterpreter
  
    + migrate: Cho phép bạn di chuyển Meterpreter sang một tiến trình khác
  
    + run: Thực thi một tập lệnh Meterpreter hoặc mô-đun Post
  
    + sessions: Nhanh chóng chuyển sang phiên khác

  - Lệnh hệ thống tập tin
  
    + cd: Sẽ thay đổi thư mục

    + ls: Sẽ liệt kê các tập tin trong thư mục hiện tại (dir cũng sẽ hoạt động)

    + pwd: In thư mục làm việc hiện tại

    + edit: sẽ cho phép bạn chỉnh sửa một tập tin

    + cat: Sẽ hiển thị nội dung của một tập tin trên màn hình

    + rm: Sẽ xóa tập tin đã chỉ định

    + search: Sẽ tìm kiếm các tập tin

    + upload: Sẽ tải lên một tập tin hoặc thư mục

    + download: Sẽ tải xuống một tập tin hoặc thư mục
    
  - Lệnh mạng
  
    + arp: Hiển thị bộ nhớ đệm ARP (Giao thức phân giải địa chỉ) của máy chủ

    + ifconfig: Hiển thị các giao diện mạng có sẵn trên hệ thống mục tiêu

    + netstat: Hiển thị các kết nối mạng

    + portfwd: Chuyển tiếp một cổng cục bộ đến một dịch vụ từ xa

    + route: Cho phép bạn xem và sửa đổi bảng định tuyến

  Lệnh hệ thống
  
    + clearev: Xóa nhật ký sự kiện
    
    + execute: Thực hiện một lệnh
    
    + getpid: Hiển thị mã định danh quy trình hiện tại

    + getuid: Hiển thị cho người dùng biết Meterpreter đang chạy như

    + kill: Kết thúc một tiến trình

    + pkill: Kết thúc các tiến trình theo tên

    + ps: Liệt kê các tiến trình đang chạy

    + reboot: Khởi động lại máy tính từ xa

    + shell: Thả vào một shell lệnh hệ thống

    + shutdown: Tắt máy tính từ xa

    + sysinfo: Nhận thông tin về hệ thống từ xa, chẳng hạn như hệ điều hành

  Các lệnh khác (các lệnh này sẽ được liệt kê trong các danh mục menu khác nhau trong menu trợ giúp)
  
    + idletime: Trả về số giây người dùng từ xa không hoạt động
  
    + keyscan_dump: Xóa bộ đệm phím tắt
  
    + keyscan_start: Bắt đầu ghi lại các lần nhấn phím
  
    + keyscan_stop: Dừng ghi lại các lần nhấn phím
  
    + screenshare: Cho phép bạn xem màn hình máy tính của người dùng từ xa theo thời gian thực
  
    + screenshot: Chụp ảnh màn hình máy tính tương tác
  
    + record_mic: Ghi âm thanh từ micrô mặc định trong X giây
  
    + webcam_chat: Bắt đầu trò chuyện video
  
    + webcam_list: Danh sách webcam
  
    + webcam_snap: Chụp ảnh nhanh từ webcam được chỉ định
  
    + webcam_stream: Phát luồng video từ webcam đã chỉ định
  
    + getsystem: Cố gắng nâng cao đặc quyền của bạn lên ngang bằng với hệ thống địa phương
  
    + hashdump: Đổ nội dung của cơ sở dữ liệu SAM

- Meterpreter cung cấp cho bạn nhiều lệnh hữu ích giúp tạo điều kiện thuận lợi cho giai đoạn khai thác sau.

  - Lệnh getuid sẽ hiển thị người dùng mà Meterpreter hiện đang chạy. Điều này sẽ cho bạn biết mức đặc quyền có thể có của bạn trên hệ thống mục tiêu
 
  - Lệnh  pssẽ liệt kê các tiến trình đang chạy. Cột PID cũng sẽ cung cấp cho bạn thông tin PID mà bạn cần để di chuyển Meterpreter sang một tiến trình khác.
 
  - Lệnh migrate để di chuyển sang tiến trình kahcsgiups Meterpreter tương tác với nó
 
  - Lệnh hashdump sẽ liệt kê nội dung của cơ sở dữ liệu SAM. Cơ sở dữ liệu SAM (Security Account Manager) lưu trữ mật khẩu của người dùng trên hệ thống Windows. Những mật khẩu này được lưu trữ theo định dạng NTLM ( New Technology LAN Manager) .
 
  - Lệnh search hữu ích để định vị các tệp có thông tin có khả năng hấp dẫn. Trong ngữ cảnh CTF, lệnh này có thể được sử dụng để nhanh chóng tìm thấy tệp cờ hoặc tệp bằng chứng, trong khi trong các hoạt động kiểm tra thâm nhập thực tế, bạn có thể cần tìm kiếm các tệp do người dùng tạo hoặc tệp cấu hình có thể chứa thông tin mật khẩu hoặc tài khoản.
 
  - Lệnh shell sẽ khởi chạy shell dòng lệnh thông thường trên hệ thống đích. Nhấn CTRL+Z sẽ giúp bạn quay lại shell Meterpreter .
 
  - Lệnh load để tận dụng các công cụ bổ sung như Kiwi hoặc thậm chí toàn bộ ngôn ngữ Python.
 
  ![image](https://github.com/user-attachments/assets/e079c1cb-b663-4a0a-b835-9ba6acf60974)






