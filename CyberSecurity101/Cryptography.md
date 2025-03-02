# Cryptography

## Các loại mã hóa

***Mã hóa đối xứng***: còn được gọi là mật mã đối xứng , sử dụng cùng một khóa để mã hóa và giải mã dữ liệu, như thể hiện trong hình bên dưới. Giữ bí mật khóa là điều bắt buộc; nó cũng được gọi là mật mã khóa riêng .

![image](https://github.com/user-attachments/assets/bcd9f26f-9422-4bce-b99f-606810d89c97)

- Các loại mã hóa đối xứng điển hình: DES, 3DES, AES,..

***Mã hóa bất đối xứng***: sử dụng một cặp khóa, một khóa để mã hóa và khóa còn lại để giải mã, như minh họa bên dưới. Để bảo vệ tính bảo mật, mã hóa bất đối xứng hoặc mật mã bất đối xứng mã hóa dữ liệu bằng khóa công khai; do đó, nó cũng được gọi là mật mã khóa công khai .

![image](https://github.com/user-attachments/assets/96f8f3a2-719a-4ed6-af0c-3969377334b0)

## Mật mã khóa công khai

- Trao đổi khóa cho mã hóa đối xứng là cách sử dụng rộng rãi của mật mã bất đối xứng. Mã hóa bất đối xứng tương đối chậm so với mã hóa đối xứng; do đó, chúng ta dựa vào mã hóa bất đối xứng để đàm phán và thống nhất về mật mã và khóa mã hóa đối xứng.

### RSA

- Là phương pháp mã hóa dữ liệu bằng hai khóa: một khóa để khóa (mã hóa) và một khóa để mở khóa (giải mã), dựa vào độ khó của việc phân tích số lớn.

- RSA là thuật toán mã hóa khóa công khai cho phép truyền dữ liệu an toàn qua các kênh không an toàn.

- RSA dựa trên bài toán khó về mặt toán học là phân tích thừa số của một số lớn. Nhân hai số nguyên tố lớn là một phép toán đơn giản; tuy nhiên, việc tìm thừa số của một số lớn đòi hỏi nhiều sức mạnh tính toán hơn.

### Trao đổi khóa Diffie-Hellman

- Hãy xem xét tình huống sau. Alice và Bob muốn nói chuyện một cách an toàn. Họ muốn thiết lập một khóa chung cho mật mã đối xứng nhưng không muốn sử dụng mật mã bất đối xứng để trao đổi khóa. Đây chính là lúc Trao đổi khóa Diffie-Hellman xuất hiện.

- Alice và Bob tạo ra bí mật một cách độc lập; chúng ta hãy gọi những bí mật này là A và B. Họ cũng có một số tài liệu chung công khai; chúng ta hãy gọi là C.

- Chúng ta cần đưa ra một số giả định. Đầu tiên, bất cứ khi nào chúng ta kết hợp các bí mật, chúng thực tế không thể tách rời. Thứ hai, thứ tự chúng được kết hợp không quan trọng. Alice và Bob sẽ kết hợp các bí mật của họ với vật liệu chung để tạo thành AC và BC. Sau đó, họ sẽ gửi chúng cho nhau và kết hợp phần nhận được với bí mật của họ để tạo ra hai khóa giống hệt nhau, cả hai đều là ABC. Bây giờ, họ có thể sử dụng khóa này để giao tiếp.

![image](https://github.com/user-attachments/assets/31b851ec-a4ec-43ca-a9cf-244d0b9c48a8)

### SSH

- Khi tạo một cặp khóa RSA, ECDSA, hoặc Ed25519, thuật toán sẽ đảm bảo rằng mỗi khóa công khai có một khóa riêng duy nhất tương ứng.

- Xác thực SSH bằng khóa công khai là một phương pháp bảo mật cao, thay thế cho việc sử dụng mật khẩu. Hệ thống này hoạt động bằng cách sử dụng cặp khóa: khóa công khai (public key) và khóa riêng (private key).

- Cách hoạt động của xác thực SSH bằng khóa:

  - Máy khách tạo cặp khóa gồm khóa công khai và khóa riêng.

  - Khóa công khai được sao chép lên máy chủ SSH.

  - Khi đăng nhập, máy khách sử dụng khóa riêng để chứng minh danh tính mà không cần nhập mật khẩu.
 
-  Bạn nên coi khóa SSH riêng tư của mình như mật khẩu. Không bao giờ chia sẻ chúng trong bất kỳ trường hợp nào; chúng được gọi là khóa riêng tư vì một lý do. Người nào đó có khóa riêng tư của bạn có thể đăng nhập vào các máy chủ chấp nhận khóa đó, tức là bao gồm khóa đó trong số các khóa được ủy quyền, trừ khi khóa được mã hóa bằng cụm mật khẩu.

- Trong các cuộc CTF, thử nghiệm thâm nhập và các bài tập nhóm đỏ, khóa SSH là một cách tuyệt vời để "nâng cấp" shell ngược, giả sử người dùng đã bật chức năng đăng nhập. Lưu ý rằng www-data thường không cho phép điều này, nhưng người dùng thông thường và root sẽ hoạt động. Để lại khóa SSH trong tệp `authorized_keys` trên máy có thể là một cửa hậu hữu ích và bạn không cần phải giải quyết bất kỳ vấn đề nào của shell ngược không ổn định như Control-C hoặc thiếu hoàn thành tab.


### Chữ ký số và chứng chỉ số

**Chữ ký số**

- Chữ ký số cung cấp một cách để xác minh tính xác thực và toàn vẹn của một thông điệp hoặc tài liệu kỹ thuật số.

- Sử dụng mật mã bất đối xứng, bạn tạo chữ ký bằng khóa riêng của mình, có thể được xác minh bằng khóa công khai của bạn. Chỉ bạn mới có quyền truy cập vào khóa riêng của mình, chứng minh rằng bạn đã ký tệp.

- Hình thức chữ ký số đơn giản nhất là mã hóa tài liệu bằng khóa riêng của bạn. Nếu ai đó muốn xác minh chữ ký này, họ sẽ giải mã bằng khóa công khai của bạn và kiểm tra xem các tệp có khớp nhau không.

***Chứng chỉ số***

- Chứng chỉ là một ứng dụng thiết yếu của mật mã khóa công khai và chúng cũng được liên kết với chữ ký số. Một nơi phổ biến mà chúng được sử dụng là cho HTTPS. Làm thế nào trình duyệt web của bạn biết rằng máy chủ bạn đang nói chuyện là tryhackme.com thực sự?

- Câu trả lời nằm ở chứng chỉ. Máy chủ web có chứng chỉ cho biết đó là tryhackme.com thực sự. Các chứng chỉ có một chuỗi tin cậy, bắt đầu với một CA gốc (Cơ quan cấp chứng chỉ). Từ thời điểm cài đặt, thiết bị, hệ điều hành và trình duyệt web của bạn sẽ tự động tin cậy nhiều CA gốc khác nhau. Chứng chỉ chỉ được tin cậy khi các CA gốc nói rằng chúng tin cậy tổ chức đã ký chúng. Theo một cách nào đó, đó là một chuỗi; ví dụ, chứng chỉ được ký bởi một tổ chức, tổ chức được CA tin cậy và CA được trình duyệt của bạn tin cậy. Do đó, trình duyệt của bạn tin cậy chứng chỉ.

- PGP là viết tắt của Pretty Good Privacy. Đây là phần mềm thực hiện mã hóa để mã hóa tệp, thực hiện ký số, v.v.

- GPG là viết tắt của GNU Privacy Guard. Đây là phần mềm mã hóa miễn phí và mã nguồn mở sử dụng mật mã khóa công khai. GPG có thể được sử dụng để mã hóa các tệp và tin nhắn, và để ký các tệp và tin nhắn. Mã hóa giúp chỉ người nhận dự định mới có thể giải mã tệp hoặc tin nhắn trong khi ký giúp người nhận có thể xác minh rằng tệp hoặc tin nhắn được gửi bởi người mà nó tuyên bố là từ đó.


## Hash

- Hàm băm khác với mã hóa. Không có khóa và không thể (hoặc không thực tế về mặt tính toán) chuyển từ đầu ra trở lại đầu vào.

- Một hàm băm lấy một số dữ liệu đầu vào có bất kỳ kích thước nào và tạo ra một bản tóm tắt hoặc bản tóm tắt của dữ liệu đó. Đầu ra có kích thước cố định. Thật khó để dự đoán đầu ra cho bất kỳ đầu vào nào và ngược lại.

-  Băm giúp bảo vệ tính toàn vẹn của dữ liệu và đảm bảo tính bảo mật của mật khẩu.

- Hash Collision  là khi hai đầu vào khác nhau cho cùng một đầu ra. Các hàm băm được thiết kế để tránh va chạm tốt nhất có thể. Hơn nữa, các hàm băm được thiết kế để ngăn chặn kẻ tấn công có thể tạo ra, tức là, thiết kế, một va chạm cố ý. Tuy nhiên, vì số lượng đầu vào thực tế là không giới hạn và số lượng đầu ra có thể bị giới hạn.


- Lưu mật khẩu dưới dạng hash, để tránh mật bị bẻ khóa nhanh cho các hàm băm không có salt thì salt được thêm vào đầu hoặc cuối mật khẩu trước khi băm, điều này có nghĩa là mỗi người dùng sẽ có một băm mật khẩu khác nhau ngay cả khi họ có cùng mật khẩu. Các hàm băm như Bcrypt và Scrypt xử lý điều này tự động. Salt không cần phải được giữ riêng tư.

## Nhận dạng Hash

- Bảng tóm tắt một số tiền tố mật khẩu theo kiểu Unix phổ biến nhất mà bạn có thể gặp. Chúng được liệt kê theo thứ tự độ mạnh giảm dần. Bạn có thể đọc thêm về chúng bằng cách kiểm tra trang hướng dẫn với `man 5 crypt`.

![image](https://github.com/user-attachments/assets/8ba61754-893a-42de-a83e-fb65a02af927)

- Ví dụ:

![image](https://github.com/user-attachments/assets/f60faabf-d295-403e-93f6-5447aa7d2cad)

  - Các trường được phân cách bằng dấu hai chấm. Các trường quan trọng là tên người dùng và thuật toán băm, muối và giá trị băm. Trường thứ hai có định dạng `$prefix$options$salt$hash`.
  
  - ychỉ ra thuật toán băm được sử dụng, yescrypt

  - j9Tlà một tham số được truyền cho thuật toán

  - 76UzfgEM5PnymhQ7TlJey1muối được sử dụng

  - /OOSg64dhfF.TigVPdzqiFang6uZA4QA1pzzegKdVm4là giá trị băm

- Mật khẩu MS Windows được băm bằng NTLM , một biến thể của MD4. Về mặt trực quan, chúng giống hệt với băm MD4 và MD5 , vì vậy, điều rất quan trọng là phải sử dụng ngữ cảnh để xác định loại băm.

- Trên MS Windows, các băm mật khẩu được lưu trữ trong SAM (Security Accounts Manager). MS Windows cố gắng ngăn chặn người dùng bình thường xóa chúng, nhưng các công cụ như mimikatz tồn tại để vượt qua bảo mật MS Windows. Đáng chú ý là các băm được tìm thấy ở đó được chia thành băm NT và băm LM.

- Một nơi tuyệt vời để tìm thêm định dạng băm và tiền tố mật khẩu là trang [Hashcat Example Hashes][https://hashcat.net/wiki/doku.php?id=example_hashes]

- Bẻ khóa mật khẩu yếu bằng danh sách từ điển sử dụng hashcat: `hashcat -m <hash_type> -a <attack_mode> hashfile wordlist`

- Ví dụ, `hashcat -m 3200 -a 0 hash.txt /usr/share/wordlists/rockyou.txt` sẽ xử lý hàm băm như Bcrypt và thử các mật khẩu trong rockyou.txt tệp.

## HMAC

- HMAC có thể được sử dụng để đảm bảo rằng người tạo ra HMAC là người mà họ nói, tức là tính xác thực được xác nhận; hơn nữa, nó chứng minh rằng thông điệp không bị sửa đổi hoặc làm hỏng, tức là tính toàn vẹn được duy trì. Điều này đạt được thông qua việc sử dụng khóa bí mật để chứng minh tính xác thực và thuật toán băm để tạo ra băm và chứng minh tính toàn vẹn.

- Các bước sau đây sẽ giúp bạn hiểu rõ hơn về cách thức hoạt động của HMAC.

  - Khóa bí mật được đệm vào kích thước khối của hàm băm.

  - Khóa đệm được XOR với một hằng số (thường là một khối số không hoặc số một).

  - Tin nhắn được băm bằng hàm băm với khóa XOR.

  - Kết quả từ Bước 3 sau đó được băm lại bằng cùng hàm băm nhưng sử dụng khóa được đệm XOR với một hằng số khác.

  - Đầu ra cuối cùng là giá trị HMAC, thường là một chuỗi có kích thước cố định.

![image](https://github.com/user-attachments/assets/48e2a6d6-584a-4d64-b00d-f5fad0765378)

