---
layout: post
title:  "Deploy React App Với Nginx"
date:   2020-07-06 09:25:07 +0700
categories: react
---
Trong bài viết này mình xin chia sẻ phương pháp để deploy dự án Reactjs trên server Ubuntu

#### Ubuntu Server
Đầu tiên, dĩ nhiên rồi, chúng ta cần một Linux server, mình sẽ sử dụng OS phổ biến là Ubuntu 18.04, yêu cầu về cấu hình như sau:

- Bộ nhớ 25GB trở lên
- Ram 2GB trở lên
- CPU: 1core hoặc nhiều hơn 😄
#### Login vào server
```  
$ ssh username@SERVER_IP
```
Tiếp đến ta sẽ cài đặt các công cụ cần thiết để chạy được ứng dụng reactjs là nodejs và npm (nếu bạn đã phát triển được ứng dụng web với react thì chắc chắn bạn biết chúng là gì rồi).
Cài đặt Node và npm trên Ubuntu server với curl bằng các lệnh sau: Cài đặt curl
```
$ sudo apt-get install curl
```
Cài đặt node và npm
```
$ curl -sL https://deb.nodesource.com/setup_13.x | sudo -E bash -
$ sudo apt-get install nodejs
```
Kiểm tra kết quả
```
$ nodejs -V
v13.3.0
$ npm --v
6.13.1
```
#### Cài đặt nginx
Webserver mình sẽ sử dụng là nginx, cài đặt nginx trên Ubuntu server như sau:
```
$ sudo apt update
$ sudo apt upgrade
$ sudo apt install nginx
```
#### Tiến hành deploy  

OK cài đặt môi trường như vậy là đủ tiếp theo chúng ta sẽ tiến hành công đoạn deploy.
Đầu tiên ta clone project về
```
$ git clone {project_link} react_app
```
Cài đặt các package cần thiết cho project
```
$ cd react_app
$ npm install
```
Lưu ý nếu project của bạn dùng một công cụ khác để quản lý package như yarn thì bạn cần cài đặt nó trước.
Sau khi cài đặt xong các package hãy thử start ứng dụng để kiểm tra ở môi trường dev:
```
$ npm start
```
Mở trình duyệt và kiểm tra ở đường dẫn http://SERVER_IP:PORT.
Nếu mọi thứ ok, dừng terminal lại bằng tổ hợp phím ctrl + c và tới bước tiếp theo.

#### Thiết lập nginx
Tạo một file config cho ứng dụng của bạn
```
$ sudo vim /etc/nginx/sites-available/react_app
```
Sau đó thêm đoạn code thiết lập dưới đây vào file vừa được tạo và lưu lại. (ở bước này giả định bạn đã chạy lệnh build ứng dụng tại thư mục build trong thư mục dự án).
```
server {
   server_name _;
   root /home/{username}/react_app/build;
   index index.html index.htm;
   location / {
   try_files $uri /index.html =404;
   }
}
```
Tiếp theo cần enable file config mà bạn vừa tạo:
```
$ sudo ln -s /etc/nginx/sites-available/react_app /etc/nginx/sites-enabled
```
Khởi động lại nginx:
```
$ sudo systemctl restart nginx
```
OK đã xong, nếu mọi thứ đều trơn tru thì ứng dụng của bạn đã sẵn sàng rồi nhé, kiểm tra trên đường dẫn: http://your_ip_address
