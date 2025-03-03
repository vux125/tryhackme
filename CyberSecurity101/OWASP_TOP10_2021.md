# TOP 10 OWASP 2021

## 1. Broken Access Control

- Trên các trang web có những trang dduowcjbaor vệ khỏi những người truy cập thường xuyên. Ví dụ, chỉ người dùng quản trị của trang web mới có thể truy cập vào trang quản lý những người dùng khác. Nhưng nếu một người bình thường truy cập trang web và có thể truy cập vào trang được bảo vệ mà họ không được phép xem thì ta có thể nói đây là một lỗi broken access control.

- Broken access control cho phép kẻ tấn công bỏ qua quyền hạn cho phép chúng xem dữ liệu nhạy cảm và thực hiện các nghiệm vụ mà chúng không được phép làm.

- Ví dụ về lỗ hổng của YouTube năm 2019 về việc một người dùng khác có thể lấy được video private của bạn (từng khung hình một). Kẻ tân công có thể sử dụng dịch vụ Google Ads, đây là sản phẩm mà các nhà quảng cáo sử dụng để tạo quảng cáo trên tất cả các dịch vụ của Google, bao gồm cả YouTube. Các quảng cáo sẽ được các nhàn quảng cáo thiết lập tại đây trên nền tảng Google Ads.

  - Có một trang tên là Video, nơi có thể xem các video được quảng cá sử dụng. Nhấp vào sẽ mở ra danh sách các mục chọn mục Analytics, đây là nơi dành cho các phần video cụ thể. Có một tính năng thú vị là Moments cho phép các nhà quảng cáo đánh dấu các khoảnh khác cụ thể của video. Khi đánh dấu một khoảnh khắc thì trên Burp Suite ghi nhận một request POST được gửi tới một endpoin là /GetThumbnails:
 
  ![image](https://github.com/user-attachments/assets/af84e189-4530-4acb-9e0e-715f2086d720)
  - Ta có thể thấy được trong tham số _ar, 1 là ID của video, 2 là thời gian khoảnh khắc được tính bằng mili giây. Response nhận được là hình ảnh được mã hóa bằng base64, là hình thu nhỏ được hiển thị bởi quảng cáo.
 
  - Thực hiện thay ID bằng ID của một video private và response nhận về là hình ảnh mã hóa base64 của video private đó. Nếu video ở chế độ 24FPS thì một khung hình sẽ ở trên màn hình trong 33 mili giây vì vậy kẻ tân công có thể viết một đoạn mã python để tải lần lượt từng bức ảnh xuống bắt đầu từ 0 mỗi bức ảnh cách nhau 33 mili giây. Thế là kẻ tấn công sẽ lấy được video private tuy chất lượng hình ảnh không cao nhưng đủ để nhìn thấy mọi thứ diễn ra.

- IDOR  hay Insecure Direct Object Reference đề cập đến lỗ hổng kiểm soát truy cập, nơi bạn có thể truy cập vào các tài nguyên mà thông thường bạn không thể nhìn thấy. Điều này xảy ra khi lập trình viên để lộ Direct Object Reference, đây chỉ là một mã định danh tham chiếu đến các đối tượng cụ thể trong máy chủ.

- Ví dụ chúng ta đăng nhập vào một tài khoản ngân hàng và chúng ta được đưa đến một url `https://bank.thm/account?id=111111`

![image](https://github.com/user-attachments/assets/76ed41ac-e07e-4512-9396-b78f32f0c3a2)

- Mọi thứ nhìn trông khá bình thường nhưng chúng ta để ý đến tham số id nếu thay đổi id đo thành 22222 thì sao, nếu trang wweb không được cài đặt đúng cách thì người đó sẽ có thể truy cập vào thông tin ngân hàng của người khác:

![image](https://github.com/user-attachments/assets/5debb8e1-749b-49ad-bb81-4bd94752efeb)


## 2. Cryptographic Failures

- Lỗi mật mã đề cập đến bất kỳ lỗ hổng nào phát sinh do việc sử dụng sai (hoặc không sử dụng) các thuật toán mật mã để bảo vệ thông tin nhạy cảm. Các ứng dụng web yêu cầu mật mã để cung cấp tính bảo mật cho người dùng ở nhiều cấp độ.

- Ví dụ, hãy lấy một ứng dụng email an toàn:

  - Khi bạn truy cập tài khoản email của mình bằng trình duyệt, bạn muốn chắc chắn rằng thông tin liên lạc giữa bạn và máy chủ được mã hóa. Theo cách đó, bất kỳ kẻ nghe lén nào cố gắng bắt các gói tin mạng của bạn sẽ không thể khôi phục nội dung địa chỉ email của bạn. Khi chúng tôi mã hóa lưu lượng mạng giữa máy khách và máy chủ, chúng tôi thường gọi đây là ***mã hóa dữ liệu khi truyền*** .

  - Vì email của bạn được lưu trữ trên một số máy chủ do nhà cung cấp của bạn quản lý, nên nhà cung cấp email cũng mong muốn không thể đọc email của khách hàng. Vì mục đích này, email của bạn cũng có thể được mã hóa khi lưu trữ trên máy chủ. Điều này được gọi là ***mã hóa dữ liệu khi lưu trữ*** .

### Supporting Material 1

- Cơ sở dữ liệu được thiết lập trên các máy chủ chuyên dụng chạy dịch vụ cơ sở dữ liệu như MySQL hoặc MariaDB; tuy nhiên, cơ sở dữ liệu cũng có thể được lưu trữ dưới dạng tệp. Chúng được gọi là cơ sở dữ liệu "flat-file" vì chúng được lưu trữ dưới dạng một tệp duy nhất trên máy tính.

- Định dạng phổ biến nhất (và đơn giản nhất) của cơ sở dữ liệu tệp phẳng là cơ sở dữ liệu SQLite. Chúng có thể được tương tác với hầu hết các ngôn ngữ lập trình và có một máy khách chuyên dụng để truy vấn chúng trên dòng lệnh. Máy khách này được gọi sqlite3và được cài đặt trên nhiều bản phân phối Linux theo mặc định.

- Để truy cập vào nó, chúng ta sử dụng  sqlite3 <database-name>:

![image](https://github.com/user-attachments/assets/bbec9e30-fc7a-4695-8049-18c909227d8c)

- Từ đây, chúng ta có thể xem các bảng trong cơ sở dữ liệu bằng cách sử dụng  .tables:

![image](https://github.com/user-attachments/assets/b4d2ee26-66cd-4e2a-97ef-576ddd1885ee)

- Tại thời điểm này ta có thể dùng các câu lenhj sql để xem thông tin từ bảng:

![image](https://github.com/user-attachments/assets/32f14fdb-e96d-43c0-839b-abd12066d8eb)


### Supporting Material 2

- Các mật khẩu thường được hash trước khi lưu vào cơ sở dữ liệu nhưng nếu thuật toán hash được sủ dụng yếu hoặc mật khẩu quá dễ thì kẻ tấn công hoàn toàn có thể crack được mật khẩu đã lưu ở dạng hash về dạng plain text

## 3. Injection

- Injection rất phổ biến trong các ứng dụng ngày nay. Những lỗi này xảy ra vì ứng dụng diễn giải dữ liệu đầu vào do người dùng kiểm soát thành lệnh hoặc tham số. Các cuộc tấn công tiêm phụ thuộc vào công nghệ được sử dụng và cách các công nghệ này diễn giải dữ liệu đầu vào. Một số ví dụ phổ biến bao gồm:
  
  - SQL Injection
 
  - Command Injection
 
  - Cross Site Scripting (XSS) ...

- Ví dụ về một lỗ hổng Cammand Injection:

![image](https://github.com/user-attachments/assets/f30babb8-c19d-46d2-8d10-a324dffe743f)

- Ta thấy được các dữ liệu đầu vào không được lọc mà đưa thảng vào hàm thực thi của php `pasthru()` điều này dẫn đến việc kẻ tấn công có thể thực hiện các câu lệnh nguy hiển trên hệ thống và RCE hệ thống.

## 4. Insecure Design

- Insecure Design đề cập đến các lỗ hổng vốn có trong kiến ​​trúc của ứng dụng. Chúng không phải là lỗ hổng liên quan đến việc triển khai hoặc cấu hình kém, nhưng ý tưởng đằng sau toàn bộ ứng dụng (hoặc một phần của ứng dụng) bị lỗi ngay từ đầu. Hầu hết thời gian, các lỗ hổng này xảy ra khi mô hình hóa mối đe dọa không phù hợp được thực hiện trong giai đoạn lập kế hoạch của ứng dụng và lan truyền cho đến tận ứng dụng cuối cùng của bạn. Đôi khi, các lỗ hổng thiết kế không an toàn cũng có thể được các nhà phát triển đưa vào khi thêm một số "phím tắt" xung quanh mã để giúp việc thử nghiệm của họ dễ dàng hơn. 



## 5. Security Misconfiguration




## 6. Vulnerable and Outdated Components





## 7. Indentification and Authentication Failures 




## 8. Software and Data Integrity Failures





## 9. Security Logging and Monitoring Failures





## 10. Server-Side Request Forgery





