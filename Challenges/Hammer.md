# Recon

- Giao diện:

![image](https://github.com/user-attachments/assets/ac27e222-ca75-421a-8249-ccbee6210328)

- Sử dụng nmap để quét các cổng trên máy mục tiêu:

![image](https://github.com/user-attachments/assets/19f2ac6d-4849-46a9-a499-f871599e4377)

![image](https://github.com/user-attachments/assets/cfc9bed1-0e71-4fa2-ba02-e7f3d9b6d2bc)

- Mục tiêu đang mở 2 cổng là 22 và 1337 với 2 dịch vụ là ssh và http

- Có một số thông tin hưu ích ở source code được comment tận dụng để quét directory:

![image](https://github.com/user-attachments/assets/fe44cd08-0413-48d0-ae81-cab12e8d7942)

- Tạo danh sách directory có tiền tố hmr_ :

![image](https://github.com/user-attachments/assets/9d912a77-e93e-4b24-bd67-cfcb347df5f0)

- Sử dụng gobuster để ra quét directory:

  - Quét khống có tiền tố hmr:

  ![image](https://github.com/user-attachments/assets/363aa2ad-18d1-4d85-98a9-53b236aa26b4)

  - Quét có tiền tố:

  ![image](https://github.com/user-attachments/assets/c4e936ae-02e5-4b6e-814a-aed9af7dfda2)

  - Quét tiếp http://10.10.161.41:1337/hmr_logs/ nơi có khả năng lưu giữ nhật ký của máy chủ web:

  ![image](https://github.com/user-attachments/assets/55ac4160-81b8-4e0b-8993-b75806e3ad7e)

  - Có một file error.logs trả về mã 200:
 
  ![image](https://github.com/user-attachments/assets/00b44867-db95-4a7b-bf54-b4c917386fe2)

  - Phát hiện một email có thể hợp lệ : `tester@hammer.thm`
    
- Sử dụng chức năng quên mật khẩu:

![image](https://github.com/user-attachments/assets/06e94bcf-c31a-4670-8f7b-ae8bbd610a98)

==> Có thể Brute force tìm email hợp lệ

- Thử email tìm được với chức năng quên mật khẩu:

![image](https://github.com/user-attachments/assets/cbc3c9fb-1c7d-4e7f-a207-b4f46fb5b8a0)

- Đây là một email hoàn toàn hợp lệ.

- Mã Digit Code gồm 4 sô ta có thể brute force.

## Khai thác

- Ta nhập thử các mã code quan sat burp suite thấy một điều rằng trong response Rate-Limit-Pending giảm dần khi bằng 0 thì sẽ không cho nhập code nữa, nhưng có trong phần Cookie thằng PHPSESSID luôn không đổi qua các lần nhập sai mã.

![image](https://github.com/user-attachments/assets/c0d83fdd-316c-4f33-a533-8b6a3b35825f)

![image](https://github.com/user-attachments/assets/0afaa057-17d6-4dd0-ae0e-3c8a28a64330)


- Ta sẽ tận dụng điều này để lấy lại PHPSESSID sau khoảng 7 lần nhập mã để không bị block

- Thực hiện khai thác bằng đoạn code python sau:

![image](https://github.com/user-attachments/assets/3a0eec2a-e723-4f1e-a58f-48ecc8293904)

![image](https://github.com/user-attachments/assets/c5c93b29-1f40-4e8a-b1d3-1db23209b9e2)

- Kết quả:

![image](https://github.com/user-attachments/assets/6a5ee100-493a-4e92-bbc5-87b8c5c64b9d)

- Thay PHPSESSID bằng PHPSESSID thu được:

![image](https://github.com/user-attachments/assets/025270fe-172a-4d60-9f3d-2281bda14a62)

- Đăng nhập bằng mật khẩu vừa đổi:

![image](https://github.com/user-attachments/assets/32b2a66d-5cc6-435f-a079-9f4984f86d2a)

## RCE

- Mã JWT của trang

![image](https://github.com/user-attachments/assets/fef57dfa-69da-4f43-b03a-ce7026499750)

- Encode :

![image](https://github.com/user-attachments/assets/7db3402c-7f69-4fcf-9652-6a7ce35f4c1c)

- Ta để ý kid: /var/www/mykey.key

- Thử lệnh ls:

![image](https://github.com/user-attachments/assets/3f4c7e79-33d9-4c4f-85b9-36613e7e46a4)

- Có một file 188ade1.key

![image](https://github.com/user-attachments/assets/d745ddf0-d815-4f11-b506-2dda9c91b248)

- key

![image](https://github.com/user-attachments/assets/65523c81-626f-4fa7-ad57-e22098627145)

- Tạo JWT với role admin
  
![image](https://github.com/user-attachments/assets/bc2e372e-be98-4d32-b58d-6b5f726b5108)

- Thay JWT vừa tạo vào:

![image](https://github.com/user-attachments/assets/9ec53ae7-d51b-424a-837f-b0ede1985cac)

- Mở cổng 4444 lắng nghe :

![image](https://github.com/user-attachments/assets/9afcb8f8-5465-45fe-914b-7653662ed5cb)

- Tạo reverse shell :

![image](https://github.com/user-attachments/assets/98cbb757-49b8-4ebb-b718-c40812d962e3)

- Nâng cấp shell:

![image](https://github.com/user-attachments/assets/86b9f9b2-027d-4dc4-8459-1a9ef38dbf30)

- Đọc flag:

![image](https://github.com/user-attachments/assets/4da56046-055c-4115-8344-f14610494a7a)
