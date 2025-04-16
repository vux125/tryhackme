- Giao diện challenges:

![image](https://github.com/user-attachments/assets/1053ac42-1a57-4436-b1f9-fc34679f6c06)

- Phát hiện một file mail.log ở view-source:
  
![image](https://github.com/user-attachments/assets/aa32e01f-d047-4828-8514-ad77ca3a2064)

- Truy cập file mail.log, ta thấy rằng nếu csdl bị xóa nó sẽ khôi phục với tài khoảng và mật khẩu mặc định như trong mail.log:
  
![image](https://github.com/user-attachments/assets/b666cec9-9147-4986-ae61-8242a2956f87)

- Tiếp tục xem view-source ta thấy file script.js, đây là một file để lọc dữ liệu đầu vào:

![image](https://github.com/user-attachments/assets/92fcc728-d70e-4a2d-a18d-6dc266297660)

![image](https://github.com/user-attachments/assets/99974f91-d892-497b-92fc-a53776e09a54)

![image](https://github.com/user-attachments/assets/6b680489-6861-4bff-93da-a2f5ce8034ef)

- Ta hoàn toàn có thể bypass bộ lọc này bằng cách chặn bắt và thay đổi gói tin bằng burp suite như dưới đây:
  
![image](https://github.com/user-attachments/assets/2ebdfe3c-a4db-41d8-a574-67a1710b9858)

![image](https://github.com/user-attachments/assets/18197ef7-4f50-4d0c-af44-0cfbe2c2c348)

![image](https://github.com/user-attachments/assets/c0d7ec51-0d5f-487d-8278-22d2e90a230c)

- Chúng ta đã login thành công, giờ hãy dùng chức năng edit, đây là nơi có khả năng rất cao có thể chứ lỗ hổng sql injection, từ đó ta có thể xóa bảng users để nó khổi phục lại với tài khoản mật khẩu mặc định trong mail.
  
![image](https://github.com/user-attachments/assets/9ecff86a-61f8-44ef-a30d-31b29d64868f)

![image](https://github.com/user-attachments/assets/413e6090-75fc-4630-8b81-2b2ed50f2a82)

![image](https://github.com/user-attachments/assets/5638fc53-1895-4357-8e2a-a51f830c6387)

- Sau khi đợi 1-2 phút chúng ta hãy đăng nhập vào với tư cách admin bằng tài khoản mật khẩu trong mail.log
  
![image](https://github.com/user-attachments/assets/583b1695-926a-4091-90a8-0beb8fe551a1)

![image](https://github.com/user-attachments/assets/c15c578d-e95f-4947-a8d4-fef9d8403111)

- Ta chú ý chức năng profile, khi ta thay đổi firstname thì tiêu đề `Welcome, ...` thay đổi theo. Website có thể dùng template để chèn firstname vào, sau một thời gian thử các payload thì có payload đã hoạt động:
 
![image](https://github.com/user-attachments/assets/1c0b9a33-121e-42eb-8719-9b0f3e2ba43f)

![image](https://github.com/user-attachments/assets/b619d887-8496-47ae-a151-0d0fea139e85)

![image](https://github.com/user-attachments/assets/32147161-dd65-42d4-80ff-d5f7117daae1)

![image](https://github.com/user-attachments/assets/941f42bc-17db-40bd-8020-2df4fe058ad9)

- Giờ ta sẽ thực hiện tải lên một payload nhằm RCE hệ thống, đồng thời mở một cổng để lắng nghe trên máy:
  
![image](https://github.com/user-attachments/assets/7db9ccc6-70e9-4bd0-af52-9b7f75b1a03b)

![image](https://github.com/user-attachments/assets/f2634ba5-f480-46a3-a2f5-08fdca3c171c)

![image](https://github.com/user-attachments/assets/e87b55fa-eecb-44f7-92fe-85c6c0279041)

![image](https://github.com/user-attachments/assets/520f4f24-9e3d-4f58-bf3e-bd1096576da2)

![image](https://github.com/user-attachments/assets/cef69e52-200a-4293-9c45-2a9e2195ca99)




