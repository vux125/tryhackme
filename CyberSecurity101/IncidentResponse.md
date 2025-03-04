# Incident Response

## Các loại sự cố

- Malware Infections: Malware là các chương trình độc hại có thể gây hư hại hệ thống, mạng hoặc ứng dụng. Đa số các sự cố có liên quan tới Malware Infection. Có nhiều loại malware khác nhau, mỗi loại lại có tính năng nguy hại riêng. Malware infections chủ yếu gây ra bởi các file có thể là text, documents, executables, etc.

- Security Breaches: Xảy ra khi một người không được phép truy cập vào dữ liệu bí mật (thứ mà chúng tôi không muốn họ nhìn thấy hoặc có). Vi phạm bảo mật có tầm quan trọng tối đa vì nhiều doanh nghiệp dựa vào dữ liệu bí mật của họ, mà chỉ những nhân viên được ủy quyền mới có thể truy cập.

- Data Leaks: Rò rỉ dữ liệu là sự cố trong đó thông tin bí mật của một cá nhân hoặc một tổ chức bị tiết lộ cho các thực thể không được phép. Nhiều kẻ tấn công sử dụng rò rỉ dữ liệu để gây tổn hại đến danh tiếng của nạn nhân hoặc sử dụng kỹ thuật này để đe dọa nạn nhân và lấy những gì chúng cần từ họ.

- Insider Attacks: Các sự cố từ bên trong một tổ chức được gọi là tấn công nội bộ. Hãy nghĩ về một nhân viên bất mãn lây nhiễm toàn bộ mạng thông qua USB vào ngày làm việc cuối cùng của mình. Đây là một ví dụ về tấn công nội bộ. Một người nào đó trong tổ chức của bạn cố tình khởi xướng một cuộc tấn công sẽ thuộc loại này.

- Denial Of Service Attacks: Tính khả dụng là một trong ba trụ cột của an ninh mạng. Các giải pháp bảo mật phòng thủ và con người liên tục tìm cách bảo vệ thông tin; họ đảm bảo rằng dữ liệu có sẵn cho mọi người cùng một lúc. Điều này là do không có ích gì khi bảo vệ thứ mà chúng ta không thể truy cập. Tấn công từ chối dịch vụ, hay tấn công DoS , là những sự cố mà kẻ tấn công làm ngập hệ thống/mạng/ứng dụng bằng các yêu cầu sai, cuối cùng khiến người dùng hợp pháp không thể truy cập. Điều này xảy ra do cạn kiệt tài nguyên có sẵn để giải quyết các yêu cầu.

## Quy trình ứng phó sự cố

- Quy trình SANS và NIST:

![image](https://github.com/user-attachments/assets/9e34132e-2f32-400d-aa8f-10683bb0d688)

- Preparation: Đây là giai đoạn đầu tiên. Giai đoạn chuẩn bị bao gồm xây dựng các nguồn lực cần thiết để xử lý sự cố. Các nguồn lực này bao gồm phát triển các nhóm ứng phó sự cố, có kế hoạch ứng phó sự cố phù hợp và triển khai các giải pháp bảo mật cần thiết để chống lại sự cố. Ví dụ: Tiến hành đào tạo nhận thức cho nhân viên về email lừa đảo . Email lừa đảo là email gian lận do kẻ tấn công độc hại gửi đến, có thể lừa bạn thực hiện các hành động có thể dẫn đến sự cố.

- Identification: Đề cập đến việc tìm kiếm bất kỳ hành vi bất thường nào có thể chỉ ra sự cố. Điều này bao gồm việc sử dụng các giải pháp và kỹ thuật bảo mật khác nhau để theo dõi các sự kiện bất thường. Ví dụ: Nhóm bảo mật nhận thấy một lượng lớn dữ liệu được gửi đi từ một trong các máy chủ. Sau khi phân tích, người ta phát hiện ra rằng dữ liệu này đã bị xâm phạm sau khi một tệp độc hại được tải xuống từ tệp đính kèm email lừa đảo.

- Contaitment: Khi đã xác định được sự cố, bước tiếp theo là phải ngăn chặn sự cố. Điều này có nghĩa là giảm thiểu tác động của cuộc tấn công. Điều này thường được thực hiện bằng cách cô lập máy nạn nhân, vô hiệu hóa các tài khoản người dùng bị xâm phạm, v.v. Ví dụ: Nhóm bảo mật sẽ cô lập máy chủ khỏi mạng để giảm thiểu tác động và không cho phép kẻ tấn công chuyển sang các hệ thống khác, lợi dụng máy chủ bị xâm phạm.

- Eradication: Giai đoạn này, như tên gọi của nó, bao gồm việc loại bỏ mối đe dọa khỏi môi trường bị tấn công. Mối đe dọa có thể là bất kỳ loại nào. Giai đoạn diệt trừ sẽ đảm bảo môi trường của đối tượng được sạch sẽ và bây giờ chúng ta có thể chuyển sang giai đoạn phục hồi. Ví dụ: Đã thực hiện quét phần mềm độc hại sâu trên hệ thống để loại bỏ phần mềm độc hại khỏi máy chủ.

- Recovery: Giai đoạn phục hồi rất quan trọng trong chuỗi này. Nó bao gồm việc khôi phục các hệ thống bị ảnh hưởng từ bản sao lưu hoặc xây dựng lại chúng. Sau đó, các hệ thống được khôi phục sẽ được kiểm tra và sẵn sàng sử dụng. Ví dụ: Máy chủ bị xâm phạm đã được cấu hình lại và dữ liệu bị rò rỉ đã được khôi phục từ bản sao lưu.

- Lessions Learned: Đây cũng là một phần quan trọng của vòng đời ứng phó sự cố. Các khoảng trống trong quá trình phát hiện và phân tích sự cố được xác định và ghi lại, giúp cải thiện toàn bộ quy trình trong các sự cố trong tương lai. Ví dụ: Tiến hành cuộc họp đánh giá sau sự cố để phân tích nguyên nhân gốc rễ của sự cố và cải thiện bảo mật nhằm ngăn chặn các cuộc tấn công trong tương lai.

## Kỹ thuật trong xác định sự cố

- Để thực hiện giai đoạn Identification trong SANS hay Detect and Analyst trong NIST ta sử dụng một sô giải pháp như:

  - SIEM : Giải pháp quản lý sự kiện và thông tin bảo mật ( SIEM ) thu thập tất cả các nhật ký quan trọng tại một vị trí tập trung và đối chiếu chúng để xác định sự cố.
 
  - AV : Phần mềm diệt vi-rút ( AV ) phát hiện các chương trình độc hại đã biết trong hệ thống và thường xuyên quét hệ thống của bạn để tìm các chương trình này.
 
  - EDR : Endpoint Detection and Response ( EDR ) được triển khai trên mọi hệ thống, bảo vệ hệ thống khỏi một số mối đe dọa cấp độ nâng cao. Giải pháp này cũng có thể ngăn chặn và loại bỏ mối đe dọa. 

Sau khi xác định được sự cố, một số quy trình nhất định phải được tuân theo, bao gồm điều tra mức độ tấn công, thực hiện các hành động cần thiết để ngăn ngừa thiệt hại thêm và loại bỏ nó từ gốc rễ. Các bước này có thể khác nhau đối với các loại sự cố khác nhau. Trong trường hợp này, có hướng dẫn từng bước để xử lý từng loại sự cố giúp bạn tiết kiệm rất nhiều thời gian. Các loại hướng dẫn này được gọi là Playbook.

- `NOTE: một số công cụ chúng ta có thể tìm hiểu như: CyberChef, CAPA, REMnux, FlareVM...`

## SIEM

-  Vì tất cả các thiết bị này tạo ra hàng trăm sự kiện mỗi giây, nên việc kiểm tra từng imglog trên từng thiết bị một trong trường hợp có bất kỳ sự cố nào có thể là một nhiệm vụ tẻ nhạt. Đó là một trong những lợi thế của việc có giải pháp SIEM . Nó không chỉ lấy nhật ký từ nhiều nguồn khác nhau theo thời gian thực mà còn cung cấp khả năng tương quan giữa các sự kiện, tìm kiếm qua nhật ký, điều tra sự cố và phản hồi kịp thời. Một số tính năng chính do SIEM cung cấp là:

  - Thu thập nhật ký thời gian thực
  
  - Cảnh báo về các hoạt động bất thường
  
  - Giám sát và khả năng hiển thị 24/7
  
  - Bảo vệ chống lại các mối đe dọa mới nhất thông qua phát hiện sớm

  - Thông tin chi tiết và trực quan hóa dữ liệu
  
  - Khả năng điều tra các sự cố trong quá khứ.

### Log sources and log ingestion

- Máy Windows: Windows ghi lại mọi sự kiện có thể xem qua tiện ích Event Viewer. Nó gán một ID duy nhất cho từng loại hoạt động nhật ký, giúp nhà phân tích dễ dàng kiểm tra và theo dõi. Nhập vào thanh tìm kiếm Event Viewer để đến nơi chứa các loại nhật ký khác nhau.

- Linux: Các file log thường được lưu trong /var/log/ ... được đưa vào hệ thống SIEM để giám sát liên tục

- Máy chủ web: Trong Linux , các vị trí phổ biến để ghi tất cả các nhật ký liên quan đến apache là  /var/log/ apache  hoặc  /var/log/httpd.

- ***Thu thập nhật ký***:

  - Agent/Forwarder:  Các giải pháp SIEM này cung cấp một công cụ nhẹ gọi là agent (forwarder của Splunk ) được cài đặt trong Endpoint. Nó được cấu hình để thu thập tất cả các nhật ký quan trọng và gửi chúng đến máy chủ SIEM.

  - Syslog:  Syslog là một giao thức được sử dụng rộng rãi để thu thập dữ liệu từ nhiều hệ thống khác nhau như máy chủ web, cơ sở dữ liệu, v.v., được gửi dữ liệu thời gian thực đến đích tập trung.
 
  - Tải lên thủ công:  Một số giải pháp SIEM , như Splunk , ELK , v.v., cho phép người dùng nhập dữ liệu ngoại tuyến để phân tích nhanh. Sau khi dữ liệu được nhập, nó được chuẩn hóa và có sẵn để phân tích.
 
  - Chuyển tiếp cổng: Các giải pháp  SIEM cũng có thể được cấu hình để lắng nghe trên một cổng nhất định, sau đó các điểm cuối sẽ chuyển tiếp dữ liệu đến phiên bản SIEM trên cổng lắng nghe.
 
**Phân tích nhật ký và cảnh báo**

- Bảng điều khiển

  - Bảng điều khiển là thành phần quan trọng nhất của bất kỳ SIEM nào . SIEM trình bày dữ liệu để phân tích sau khi được chuẩn hóa và thu thập. Tóm tắt các phân tích này được trình bày dưới dạng thông tin chi tiết có thể hành động được với sự trợ giúp của nhiều bảng điều khiển. Mỗi giải pháp SIEM đều có một số bảng điều khiển mặc định và cung cấp tùy chọn để tạo Bảng điều khiển tùy chỉnh. Một số thông tin có thể tìm thấy trong bảng điều khiển là:

    - Alert Highlights

    - System Notification

    - Health Alert

    - List of Failed Login Attempts

    - Events Ingested Count

    - Rules triggered

    - Top Domains Visited

    ![image](https://github.com/user-attachments/assets/8ebeec02-6754-4eb5-b052-84ff510f9da5)

**Quy tắc tương quan**

- Quy tắc tương quan đóng vai trò quan trọng trong việc phát hiện kịp thời các mối đe dọa, cho phép các nhà phân tích hành động kịp thời. Quy tắc tương quan về cơ bản là các biểu thức logic được thiết lập để kích hoạt. Một số ví dụ về quy tắc tương quan là:

  - Nếu Người dùng có 5 lần Đăng nhập không thành công trong 10 giây - Đưa ra cảnh báoMultiple Failed Login Attempts

  - Nếu đăng nhập thành công sau nhiều lần đăng nhập không thành công - Đưa ra cảnh báo choSuccessful Login After multiple Login Attempts
  
  - Một quy tắc được thiết lập để cảnh báo mỗi khi người dùng cắm USB (Hữu ích nếu USB bị hạn chế theo chính sách của công ty)

  - Nếu lưu lượng truy cập đi > 25 MB - Đưa ra cảnh báo về Nỗ lực đánh cắp dữ liệu tiềm ẩn (Thông thường, điều này phụ thuộc vào chính sách của công ty)

**Quy tắc tương quan được tạo ra như thế nào**

- Để giải thích cách thức hoạt động của quy tắc, hãy xem xét các trường hợp sử dụng Eventlog sau:

- Trường hợp sử dụng 1:

  - Kẻ tấn công có xu hướng xóa nhật ký trong giai đoạn sau khai thác để xóa dấu vết của chúng. Một ID sự kiện duy nhất 104 được ghi lại mỗi khi người dùng cố gắng xóa hoặc xóa nhật ký sự kiện. Để tạo quy tắc dựa trên hoạt động này, chúng ta có thể đặt điều kiện như sau: Nếu nguồn nhật ký là WinEventLog và EventID là 104 - Kích hoạt cảnh báo `Event Log Cleared`

- Trường hợp sử dụng 2: Kẻ thù sử dụng các lệnh như whoami sau giai đoạn khai thác/leo thang đặc quyền. Các trường sau sẽ hữu ích để đưa vào quy tắc.

  - Nguồn nhật ký: Xác định nguồn nhật ký ghi lại nhật ký sự kiện

  - ID sự kiện: ID sự kiện nào được liên kết với hoạt động Thực thi quy trình? Trong trường hợp này, ID sự kiện 4688 sẽ hữu ích.

  - NewProcessName: tên quy trình nào sẽ hữu ích khi đưa vào quy tắc?

- Quy tắc: Nếu Nguồn nhật ký là WinEventLog và EventCode là 4688 và NewProcessName chứa whoami, thì kích hoạt cảnh báo `WHOAMI command Execution DETECTED`

**Cảnh báo điều tra**

- Khi giám sát SIEM , các nhà phân tích dành phần lớn thời gian của họ trên bảng điều khiển vì nó hiển thị nhiều chi tiết quan trọng về mạng theo cách rất tóm tắt. Khi cảnh báo được kích hoạt, các sự kiện/luồng liên quan đến cảnh báo sẽ được kiểm tra và quy tắc sẽ được kiểm tra để xem điều kiện nào được đáp ứng. Dựa trên cuộc điều tra, nhà phân tích xác định xem đó là kết quả True hay False positive. Một số hành động được thực hiện sau khi phân tích là:

  - Cảnh báo là Báo động giả. Có thể cần điều chỉnh quy tắc để tránh các báo động giả tương tự xảy ra lần nữa.

  - Cảnh báo là True Positive. Thực hiện điều tra thêm.

  - Liên hệ với chủ sở hữu tài sản để hỏi về hoạt động này.

  - Hoạt động đáng ngờ được xác nhận. Cô lập vật chủ bị nhiễm bệnh.

  - Chặn IP đáng ngờ.
