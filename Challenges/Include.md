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






