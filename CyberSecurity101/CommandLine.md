# Windows PowerShell

## Command line

- ***set*** để cho chúng ta thấy đường dẫn nơi mà các câu lệnh sẽ được tìm kiếm để thực hiện(sau Path=):

![image](https://github.com/user-attachments/assets/bf69e0c9-e7a3-45ec-8a78-5977f0023b1e)

- ***ver***  để xác định phiên bản hệ điều hành (OS)

- ***ipconfig*** kiểm tra thông tin mạng.

- ***ping*** gửi gói tin ICMP đi vời đợi phản hồi lại. Nếu nhận được phản hồi lại thì mục tiêu có thể được tiếp cận.

- ***tracert*** theo dõi tuyến mạng đã đi qua để đến được mục tiêu.

- ***nslookup*** tra cứu máy chủ hoặc tên miền và trả về địa chỉ IP của máy chủ đó.

- ***netstat*** hiển thị các kết nối mạng hiện tại và các cổng lắng nghe.

- ***tasklist*** liệt kê các tiến trình đang chạy.

- ***chkdsk*** kiểm tra hệ thống tập tin và ổ đĩa để tìm lỗi và các sector bị lỗi.

- ***driverquery*** hiển thị danh sách các trình điều khiển thiết bị đã cài đặt.

- ***sfc /scannow*** quét các tập tin hệ thống để tìm lỗi và sửa chữa chúng nếu có thể.

- ***more*** hiển thị tập tin văn bản. Hoặc ***command | more***

## PowerShell

PowerShell là chương trình quản lý cấu hình và tự động hóa tác vụ của Microsoft, bao gồm một shell dòng lệnh và ngôn ngữ lập trình liên quan.

lệnh PowerShell được gọi là cmdlets. Cmdlet tuân theo một quy ước đặt tên nhất quán ***Verb-Nounquy***. Cấu trúc này giúp dễ hiểu chức năng của từng cmdlet. Cmdlet Verb mô tả hành động và cmdlet Noun chỉ định đối tượng mà hành động được thực hiện. Ví dụ:

- Get-Content: Truy xuất (lấy) nội dung của một tệp và hiển thị nó trong bảng điều khiển.

- Set-Location: Thay đổi (đặt) thư mục làm việc hiện tại.

### Basic Cmdlets

Để liệt kê tất cả các lệnh cmdlet, hàm, bí danh và tập lệnh có thể được thực thi trong phiên PowerShell hiện tại , chúng ta có thể sử dụng Get-Command:

![image](https://github.com/user-attachments/assets/e6b7695f-fb61-492f-99dd-ba9a0f1052a3)

Lọc danh sách lệnh dựa trên các giá trị thuộc tính được hiển thị. Sử dụng tùy chọn -CommandType, -Name,..:

![image](https://github.com/user-attachments/assets/e4773e89-a9b8-4186-9bb0-7ab31c0aa057)

- Get-Help rât hữu ích để biết hướng dẫn chi tiết của một cmdlet nào đó, ví dụ:

![image](https://github.com/user-attachments/assets/f25d202f-d500-4537-9f9c-794d00d7ecc0)

- PowerShell cung cấp alias (bí danh- phím tắt) ví dụ: ***Get-Command -CommandType "Alias"*** ==> ***Get-Alias***, ***Get-ChildItem*** ==> ***dir***, ***Set-Location*** ==> ***cd***,...

![image](https://github.com/user-attachments/assets/a6586fa7-dd99-421c-a741-3fea8a7569be)

- Để tìm kiếm các mô-đun trong các kho lưu trữ trực tuyến như PowerShell Gallery, chúng ta có thể sử dụng ***Find-Module***: ***Cmdlet -property "pattern"***, ví dụ:

![image](https://github.com/user-attachments/assets/ebf64f19-abaf-4c7d-b609-28fa785cf2fd)

- ***Install-Module -Name "Name_Module"*** để tải module.

### Điều hướng Hệ thống tệp và làm việc với tệp

- ***Get-ChildItem*** tương tự dir trên cmd hay ls trên Unix nó sẽ liệt kê các thư mục và tệp trong thư mục được chỉ định bằng tham số -Path

![image](https://github.com/user-attachments/assets/1dadebbe-e84f-4032-b31a-d4fbabf4a2c1)

- ***Set-Location*** tương tự lệnh cd để điều hướng đến đường dẫn chỉ định sau -Path

![image](https://github.com/user-attachments/assets/7d050484-dcbb-418a-a369-16e214cf4fe8)

- ***New-Item*** được sử dụng để tạo một file hoặc một thư mục mới với tùy chọn -ItemType: ***New-Item -Path "./Documents/file.txt" -ItemType "File"*** hoặc "Directory" với thư mục

- ***Remove-Item -Path "Path"*** xóa tệp hoặc thư mục được chỉ định

- ***Move-Item -Path "Path1" -Destination "Path2"*** di chuyển từ path1 sang path2

- ***Copy-Item -Path "Path1" -Destination "Path2"*** copy từ path1 sang path2

- ***Get-Content -Path "path"*** tương tự lệnh type trên Windows hay lệnh cat trên Linux

### Kỹ thuật đường ống và sắp xếp

- Piping là kỹ thuật được sử dụng trong môi trường dòng lệnh cho phép đầu ra của một lệnh được sử dụng làm đầu vào cho lệnh khác. Được biểu thị bằng ký hiệu |

- ***Sort-Object property*** sắp xếp theo thuộc tính được chỉ định. Câu lệnh dưới sẽ lấy các thư mục và file ở đường dẫn hiện tại sau đó sắp xếp theo thuộc tính Length

![image](https://github.com/user-attachments/assets/23b2f0a6-8c19-491e-bdf8-2e330325ef32)

- ***Where-Object -property "X" [[operation: -eq | -ne | -gt | -ge | -lt | -le ] | -like] "Y"*** lọc các đối tượng theo điều kiện được chỉ định.

![image](https://github.com/user-attachments/assets/6df6dc9e-d25b-4cc6-9439-e6ff5b051d86)

![image](https://github.com/user-attachments/assets/e1584c24-7d06-4e5d-9fc1-a3419e40b17e)

- ***Select-Object -Path "path" property1,property2,...*** lấy ra các trường thông tin được chỉ định. 

- ***Select-String -Path "path" -Pattern "pattern"*** tương tự như grep

![image](https://github.com/user-attachments/assets/dd16a6cb-f9df-4aab-b427-4ed3b71f22de)


### Thông tin hệ thống và mạng

- ***Get-ComputerInfo*** lấy thông tin toàn diện về hệ thống, bao gồm thông tin hệ điều hành, thông số kỹ thuật phần cứng, chi tiết BIOS, ...

![image](https://github.com/user-attachments/assets/8c620fbc-d632-4bfb-855f-b65a8137063c)

- ***Get-LocalUser*** liệt kê các tài khoản cục bộ.

- ***Get-NetIPConfiguration*** tương tự ipconfig, ***Get-NetIPAddress*** lấy thông tin chi tiết

### Phân tích hệ thống thời gian thực

- ***Get-Process*** cung cấp chế độ xem chi tiết về tất cả các tiến trình đang chạy, bao gồm cả mức sử dụng CPU và bộ nhớ, khiến nó trở thành công cụ mạnh mẽ để theo dõi và khắc phục sự cố.

![image](https://github.com/user-attachments/assets/ed3ce291-aee0-4009-9bd9-d5cef06e18a7)

- ***Get-Servicecho*** phép truy xuất thông tin về trạng thái của các dịch vụ trên máy, chẳng hạn như dịch vụ nào đang chạy, dừng hoặc tạm dừng.

- ***Get-NetTCPConnection*** hiển thị các kết nối TCP hiện tại , cung cấp thông tin chi tiết về cả điểm cuối cục bộ và từ xa. Cmdlet này đặc biệt hữu ích trong quá trình phản hồi sự cố hoặc phân tích phần mềm độc hại, vì nó có thể phát hiện ra các cửa hậu ẩn hoặc các kết nối đã thiết lập đối với máy chủ do kẻ tấn công kiểm soát.

- ***Get-FileHash*** đến lệnh cmdlet hữu ích để tạo băm tệp, đặc biệt có giá trị trong ứng phó sự cố, săn tìm mối đe dọa và phân tích phần mềm độc hại vì lệnh này giúp xác minh tính toàn vẹn của tệp và phát hiện hành vi giả mạo tiềm ẩn.

## Script

- ***Invoke-Command*** là điều cần thiết để thực hiện các lệnh trên các hệ thống từ xa, khiến nó trở nên cơ bản đối với các quản trị viên hệ thống, kỹ sư bảo mật và người kiểm tra thâm nhập.

![image](https://github.com/user-attachments/assets/9e83b6a3-0a23-4ceb-9c0f-1d44b34863af)

- Ví dụ đầu tiên cho thấy lệnh cmdlet có thể dễ dàng kết hợp với bất kỳ tập lệnh tùy chỉnh nào để tự động hóa các tác vụ trên máy tính từ xa.

- Ví dụ thứ hai chứng minh rằng chúng ta không cần biết cách viết kịch bản để tận dụng sức mạnh của Invoke-Command. Trên thực tế, bằng cách thêm tham số -ScriptBlock { ... } vào cú pháp của cmdlet, chúng ta có thể thực thi bất kỳ lệnh nào (hoặc chuỗi lệnh) trên máy tính từ xa. Kết quả sẽ giống như khi chúng ta nhập lệnh trong phiên PowerShell cục bộ trên chính máy tính từ xa.

`Invoke-Command` → Thực thi lệnh từ xa.

`ComputerName Server01` → Chỉ định máy tính từ xa (tên máy chủ là Server01).

`Credential Domain01\User01` → Chạy lệnh với thông tin đăng nhập User01 thuộc miền Domain01. Hệ thống sẽ yêu cầu nhập mật khẩu.

`ScriptBlock { Get-Culture }` → Chạy lệnh Get-Culture trên máy từ xa để lấy thông tin về ngôn ngữ và định dạng văn hóa của hệ thống (en-US, fr-FR, v.v.).

--- 

# Linux Shell

- Trong Linux có nhiều loại shell được cài đặt và chúng ta có thể thấy nó trong /etc/shells:

![image](https://github.com/user-attachments/assets/7d07e78a-e553-44a9-b6ba-c8df961ec4c8)

- Để chuyển đổi các loại shell ta chỉ cần gọi tên của shell đó:

![image](https://github.com/user-attachments/assets/271a5dad-aba5-41a4-bfdc-6a3d0543f1fe)

- `chsh -s /usr/bin/zsh` lệnh này sẽ cài đặt shell mặc định cho terminal.

## Các Shell phổ biến

### Bash 

- Nó cung cấp tính năng hoàn thành tab, nghĩa là nếu bạn đang hoàn thành một lệnh, bạn có thể nhấn phím tab trên bàn phím. Nó sẽ tự động hoàn thành lệnh dựa trên kết quả khớp có thể hoặc đưa ra cho bạn nhiều gợi ý để hoàn thành lệnh.

- Bash lưu trữ một tệp lịch sử và ghi lại tất cả các lệnh của bạn. Bạn có thể sử dụng các phím mũi tên lên và xuống để sử dụng các lệnh trước đó mà không cần nhập lại chúng. Bạn cũng có thể nhập historyđể hiển thị tất cả các lệnh trước đó của mình.

### Friendly Interactive Shell (Fish) 

- Nó cung cấp cú pháp rất đơn giản, phù hợp với cả người dùng mới bắt đầu.

- Không giống như bash, nó có chức năng tự động sửa lỗi chính tả cho các lệnh bạn viết.

- Bạn có thể tùy chỉnh dấu nhắc lệnh bằng một số chủ đề thú vị bằng cách sử dụng fish.

- Tính năng tô sáng cú pháp của fish tô màu các phần khác nhau của lệnh dựa trên vai trò của chúng, có thể cải thiện khả năng đọc lệnh. Nó cũng giúp chúng ta phát hiện lỗi bằng màu sắc riêng của chúng.
  
- Fish cũng cung cấp chức năng tạo tập lệnh, hoàn thành tab và lịch sử lệnh giống như các shell được đề cập trong nhiệm vụ này.

### Zsh

- Zsh cung cấp tính năng hoàn thành tab nâng cao và cũng có khả năng viết tập lệnh.

- Giống như cá, nó cũng cung cấp tính năng tự động sửa lỗi chính tả cho các lệnh.
  
- Nó cung cấp khả năng tùy chỉnh mở rộng, có thể khiến nó chậm hơn các shell khác.

- Nó cũng cung cấp chức năng hoàn thành tab, lịch sử lệnh và một số tính năng khác.

## Script

- Chúng ta sẽ sử dụng bash shell, với tên tệp có phần mở rộng `.sh`

- `#!<shell>` định nghĩa trình thông dịch trong shebang. Ví dụ với bash: `#!/bin/bash`

### Variables

- Khai bao biến và gán giá trị cho biến `Var=Value`, ví dụ: `NAME="Vu"`: 

![image](https://github.com/user-attachments/assets/a8ca6729-37db-48d0-bf13-e5ba6680fbbe)

- Chúng ta cũng có thể lấy đầu vào từ người dùng thông qua read:

![image](https://github.com/user-attachments/assets/3940c97d-36f9-4df6-8c2b-20c8d08ff1fa)

### Loop

**Nhắc lại một số toán tử so sánh**: `-eq`, `-ne`, `-gt`, `-ge`, `-lt`, `-le`,...

**Cú pháp lệnh for**

`for variable in list`

`do`

  `command`

`done`

- Cũng có thể dùng cú pháp giống với for trong c/c++

- Ví dụ 1:

![image](https://github.com/user-attachments/assets/6edc9658-fcaa-4b1e-bf67-77b423a4abdc)

- Ví dụ 2 dùng dấu {..}

![image](https://github.com/user-attachments/assets/b250326f-abdc-491e-9ea0-dba76f58e24a)

- Ví dụ 3 dùng seq để tạo dãy số:

![image](https://github.com/user-attachments/assets/df4ba10b-2787-4b78-8524-db30df85ac00)

- Ví dụ 4 duyệt file:

![image](https://github.com/user-attachments/assets/2c914994-fbec-4607-8095-5972fcc6d21a)


**Cú pháp lệnh while và until**

- `while`: chạy khi điều kiện đúng
  
`while [ condition ]`

`do`

  `command`
    
`done`

- `until`: chạy khi điều kiện sai

`until [ condition ]`

`do`

  `command`
    
`done`

### Câu lệnh có điều kiện

**Cú pháp**

`if [condition1]; then`

  `command`
    
`elif [condition2]; then`

  `command`
    
`else`

  `command`
    
`fi`

- Toán tử kiểm tra chuỗi: `=`==> bằng; `!=`==> khác; `-z`==> rỗng; `-n`==> không rỗng;

- Cả hai điều kiện đúng `&&`, một trong hai đúng `||`

- Toán tử kiểm tra tệp:

![image](https://github.com/user-attachments/assets/9c7498db-687e-4f20-8f59-af7205ff02b4)

