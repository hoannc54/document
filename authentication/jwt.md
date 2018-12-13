# Khái niệm 

JSON Web Mã (JWT) là một chuẩn mở (RFC 7519) định nghĩa một cách nhỏ gọn và khép kín để truyền một cách an toàn thông tin giữa các bên dưới dạng đối tượng JSON. Thông tin này có thể được xác minh và đáng tin cậy vì nó có chứa chữ ký số. JWTs có thể được ký bằng một thuật toán bí mật (với thuật toán HMAC) hoặc một public / private key sử dụng mã hoá RSA.

Ví dụ: 
`eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOlwvXC8xMTguNzAuMTMuMzY6NjA1MFwvYXBpXC9hdXRoXC9sb2dpbiIsImlhdCI6MTU0NDY4NTk4MiwiZXhwIjoxNTQ0Njg5NTgyLCJuYmYiOjE1NDQ2ODU5ODIsImp0aSI6IndkOG5HQVlZUXZIaUQ3VGoiLCJzdWIiOjEsInBydiI6IjIzYmQ1Yzg5NDlmNjAwYWRiMzllNzAxYzQwMDg3MmRiN2E1OTc2ZjcifQ.JF3rS27mzPY5PumvWEC40sPjcYoJVPw7YspB4LspHzo`

## JWT gồm 3 thành phần 

- Header 
- Payload


### Header
