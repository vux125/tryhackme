- Sử dụng nmap để quét các cổng và dịch vụ sử dụng

<img width="879" height="506" alt="image" src="https://github.com/user-attachments/assets/9b6508a8-8cd3-4bca-9849-da7b2b5b8cd1" />

- Truy cập 10.10.244.249:4000 và truy cập tài khoản, mật khẩu guest/guest:

<img width="1112" height="699" alt="image" src="https://github.com/user-attachments/assets/69530d4a-d08b-4561-a8f1-b72af0a26df2" />

<img width="1202" height="708" alt="image" src="https://github.com/user-attachments/assets/8d712be6-ab41-4e8a-aec0-042afecfa896" />

- Truy cập view profile của guest ta thấy được thông tin chú ý đến isAdmin là false:

<img width="817" height="765" alt="image" src="https://github.com/user-attachments/assets/8b9ef87f-18c4-4083-91e7-eabc9ac2e11c" />

- Ta đổi isAdmin thành true hoặc ta cũng có thể đổi isAdmin thành true đối với người dùng khác bằng ác tháy đổi tham số 1 trên url:

<img width="937" height="339" alt="image" src="https://github.com/user-attachments/assets/131749c2-4859-4edf-a352-16b657e0f57c" />

- Khi thay thành true t có thêm mục api, các api này chỉ cho phép local truy cập:

<img width="937" height="339" alt="image" src="https://github.com/user-attachments/assets/94030132-cba5-4b65-b20a-453de2ee98e9" />

- Ở mục Setting có một chức năng bị ssrf cho ta nhập vào url, ta sẽ dùng nó để gọi api:

<img width="1282" height="649" alt="image" src="https://github.com/user-attachments/assets/c66a45d6-0fb3-44d8-9f71-989248b51c59" />

 - Giải mã base64 ta được thông tin xác thực rất có ích:

<img width="1431" height="149" alt="image" src="https://github.com/user-attachments/assets/c6c464eb-00c8-43ac-901b-58c92845bc8c" />

- Trong thông tin có được ta có được thông tin tài khoản, mật khẩu của System Monitoring, truy cập 10.10.244.249:50000 để đang nhập và lấy cờ:

<img width="1321" height="626" alt="image" src="https://github.com/user-attachments/assets/b78449ea-b76b-4c19-9cc8-76cbfb518c29" />

- Mở view-source của dashboard.php ta thấy có img tag là nơi đáng nghi nhất với tham số img truyền vào 1 file khả năng xảy ra path travesal hoặc include:

<img width="842" height="713" alt="image" src="https://github.com/user-attachments/assets/5dd6d003-631c-4e99-966c-3a0db29f124a" />

- Ta thử payload với img sử dụng gobuster fuzz và lưu kết quả vào result.txt:

<img width="1286" height="105" alt="image" src="https://github.com/user-attachments/assets/4dde1ee1-de74-4af5-a7f6-15d45ccc1160" />

- Lọc bỏ các kết quả có Length=0:

<img width="1268" height="494" alt="image" src="https://github.com/user-attachments/assets/bf74252a-bc37-4955-abb4-114dc0e11840" />

- Test các payload đã lọc được ta thấy rằng có thể được file /etc/passwd:

<img width="989" height="707" alt="image" src="https://github.com/user-attachments/assets/c27b25e8-f15a-4fbf-9da6-93fbae112ca1" />

- Tôi thử đọc 1 số file log của hệ thống:

<img width="1429" height="356" alt="image" src="https://github.com/user-attachments/assets/eebd3ec2-5286-484f-8655-db50e69d2e6d" />

<img width="1452" height="235" alt="image" src="https://github.com/user-attachments/assets/ce374482-3039-4857-8d47-b08c3608ee33" />

- Ban đầu ta quét nmap thấy được rằng trên hệ thống đang mở dịch vụ ssh ta có thể lợi dụng việc này để ghi log vào file auth.log để thực hiện include:

<img width="1608" height="480" alt="image" src="https://github.com/user-attachments/assets/3db5f1a4-1c02-42a9-8559-e60f9ecfbddd" />

- Chèn đoạn reverse php làm tên user để ghi vào log:

<img width="1335" height="614" alt="image" src="https://github.com/user-attachments/assets/ffe2b15b-a8a8-4c5e-adb8-dc1d218e082d" />

<img width="1320" height="883" alt="image" src="https://github.com/user-attachments/assets/acb0ba4f-1f86-4684-b09f-5e7b9498633f" />

- Dùng system("ls") để liệt kê các mục trong /var/www/html:

<img width="1301" height="861" alt="image" src="https://github.com/user-attachments/assets/6de39fbc-d69f-4f31-b6c9-5c051b7f3967" />

- Dùng ***<?php system("cat 505eb0fb8a9f32853b4d955e1f9123ea.txt"); ?>*** để lấy flag:

<img width="716" height="551" alt="image" src="https://github.com/user-attachments/assets/0d49f9fb-a741-40de-a424-3f87e71eb7ee" />

<img width="1831" height="239" alt="image" src="https://github.com/user-attachments/assets/08d807b2-9e8f-47f9-affb-cd61076a684e" />

- Flag: **THM{505eb0fb8a9f32853b4d955e1f9123ea}**

