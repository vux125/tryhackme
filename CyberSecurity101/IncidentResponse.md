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


