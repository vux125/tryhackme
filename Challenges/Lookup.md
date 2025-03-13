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



