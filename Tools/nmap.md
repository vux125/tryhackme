# Nmap Live Host Discovery

- ARP: `nmap -PR -sn Target`

- ICMP: `nmap -PE|-PP|-PM -sn Target`

- TCP SYN: `nmap -PS -sn Target`

- TCP ACK: `nmap -PA -sn Target`

- UDP: `nmap -PU -sn Target`

# Nmpa Host Port Scan

- `-sN`: Null Scan => không cờ nào đực thiết lập

- `-sF`: FIN Scan

- `-sX`: Xmas Scan => FIN, PSH, URG được thiết lập.

- `-sM`: Maimon Scan: Các cờ FIN và ACK sẽ được thiết lập với mục tiêu là sẽ nhập được gói RST.

- `-sA`: ACK được thiết lập

- `-sW`: Window Scan

- `-O`: Phát hiện OS

- `--traceroute`: Theo dõi đường đi


- `--scanflags flags`: Ví dụ bạn muốn quét các cờ ACK, SYN, RST: "nmap --scanflags ACKSYNRST"

- `-e`: Chỉ định giao diện nhận phản hồi

- `-Pn`:  Vô hiệu hóa quét ping

- `--spoof-mac SPOOFED_MAC`: Giả mạo MAC

- `-S SPOOFED_IP`: Giả mạo IP

- `--reason`: Để biết lý do tại sao nmap kết luận như vậy

- `-v`: thêm thông tin chi tiết có thể -vv -vvv...

- `-d` or `-dd` : để gỡ lỗi

- `--script=default` or `-sC`: Chỉ định sử dụng kich bản
  
![image](https://github.com/user-attachments/assets/1fe4ee74-3b49-4629-8113-a10ff388137f)

- `-oN FILENAME`: Normal định dạng bình thường tương tự như kết quả bạn nhận được trên màn hình khi quét mục tiêu.

- `-oG FILENAME`: Lọc đầu ra quét theo các từ khóa hoặc thuật ngữ cụ thể một cách hiệu quả.

- `-oX FILENAME`: Lưu kết quả quét ở định dạng XML
