- Truy cập trang lookup.thm:

![image](https://github.com/user-attachments/assets/9759c777-9ba5-4b9c-8e02-89338a3679bb)

- Thử username và password bất kỳ quan sát burpsuite:

![image](https://github.com/user-attachments/assets/326ee2bd-4e0f-4f38-8e68-b17f402c72a2)

- Tôi đã thử nhiều username và mật khẩu khác nhau nhưng kết quả đề trả về là `Wrong username or password` nhưng riêng với username là admin và password bất kỳ ta lại thu được một thông báo kết quả khác:

![image](https://github.com/user-attachments/assets/08a1adc6-5f83-4930-a476-937f3ce46f3b)

- Thông báo trả về chỉ là `Wrong password` có vẻ như admin là người dùng hợp lệ => brute force mật khẩu bằng hydra:

![image](https://github.com/user-attachments/assets/6b1e2a6f-754b-4b10-bb04-ae5079166f16)

![image](https://github.com/user-attachments/assets/c6239658-9a5d-496f-bc1c-59e78799f45e)

- Kết quả brute force ta thu được mật khẩu là password123, thử lại mật khẩu:

![image](https://github.com/user-attachments/assets/d4670fba-fb96-4100-9460-14dd5a56027b)

- Với username `admin` và mật khẩu là `password123` thống báo nhận được lại là `Wrong username or password.`, có vẻ với người dùng hợp lệ nhưng mật khẩu sai thì thông báo là `Wrong password` còn username sai hoặc password và username sai thì thông báo là `Wrong username or password`, bây giờ ta sẽ thử brute force với danh sách username và password là password123 bằng hydra:

![image](https://github.com/user-attachments/assets/98d3c50a-b0e4-4a26-8be1-cc101bd31dd0)

![image](https://github.com/user-attachments/assets/6fae5402-eb09-4f09-a62d-b77c3f4f5ffa)

- Ta thay username=jose vào và thử lại:

![image](https://github.com/user-attachments/assets/8ac17f71-4c73-412e-9715-84aeb3fe34af)

- Sau đăng nhập nó chuyển hướng cho ta đến trang sau:

![image](https://github.com/user-attachments/assets/3945ad68-0720-43c1-8b59-680023b70a72)

- Trang web sử dụng công nghệ elfinder phiên bản 2.1.47 là phiên bản lỗi thời:

![image](https://github.com/user-attachments/assets/5f98bd28-f721-49b9-98ec-9cafe55aed90)

- Sử dụng Searchsploit để tìm kiếm khai thác elfinder và nó cho ra kết quả đây là một phiên bản lỗi thời có lỗ hổng cho phép chúng ta có thể RCE hệ thống:

![image](https://github.com/user-attachments/assets/3327aa48-6382-4630-84d8-a873b0806c26)

- Giờ hãy sử dụng Metasploit để khai thác nó:

<img width="1665" height="1010" alt="image" src="https://github.com/user-attachments/assets/21b2537b-b371-48a2-aad5-52c258a7908f" />

- Tạo một reverce shell mới:

<img width="977" height="498" alt="image" src="https://github.com/user-attachments/assets/f10241e2-7698-4543-b42f-727f02e6d572" />

- Dùng find để tìm các lệnh có setuid:

<img width="833" height="1032" alt="image" src="https://github.com/user-attachments/assets/ac020735-d82f-4604-a30e-a40ee87621ac" />

- Ta thấy /usr/sbin/pwm là lệnh khá lạ trên hệ thống linux, ta thử chạy lệnh và thấy "id" được chạy

<img width="690" height="143" alt="image" src="https://github.com/user-attachments/assets/4d69badc-a9f1-412c-a2c4-79cef700512e" />

- Ta sẽ tạo ra một lệnh id trong /tmp và thêm đường dẫn vào biến môi trường PATH

<img width="985" height="119" alt="image" src="https://github.com/user-attachments/assets/89b40836-c157-431e-9c00-1196cc28e4d3" />

<img width="1007" height="190" alt="image" src="https://github.com/user-attachments/assets/20186cae-991a-4466-b14e-8eec50e5030f" />

- Thực hiện cấp quyenf thực thi cho /tmp/id và chạy usr/sbin/pwm:

<img width="1010" height="425" alt="image" src="https://github.com/user-attachments/assets/4fae7236-b9c0-4319-a449-e2977bd5f9c4" />

- Đây có thể là danh sách mật khẩu của think, tôi sẽ dùng hydra để brute force dịch vụ ssh:

<img width="809" height="380" alt="image" src="https://github.com/user-attachments/assets/8670dc4b-25b2-489e-8400-f0ea15c975ef" />

- Đăng nhập ssh và lấy flag:

<img width="782" height="139" alt="image" src="https://github.com/user-attachments/assets/2a8cf849-a923-453a-94a5-d6fcb796851e" />

- Kiểm tra đặc quyền sudo của think ta thấy người dùng này có thể thực thi lệnh look với quyền sudo:

<img width="815" height="256" alt="image" src="https://github.com/user-attachments/assets/04fc3ebf-83cc-4ed8-90b0-97e87270f508" />

- Lợi dụng điều này ta có thể đọc root.txt bằng lệnh look:

<img width="822" height="107" alt="image" src="https://github.com/user-attachments/assets/e9c7b650-180e-4187-9db1-0c2fe9a59a0c" />
