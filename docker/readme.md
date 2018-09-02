## Các lệnh cơ bản :

### Build image từ Dockerfile

`docker build -t nginx_image . `

## Docker là gì?
Theo nguồn wikipedia: _"Docker là một dự án mã nguồn mở giúp tự động triển khai các ứng dụng Linux và Windows vào trong các container ảo hóa."_

Theo các trang mạng: _"Docker là một open platform cung cấp cho người sử dụng những công cụ và service để người sử dụng có thể đóng gói và chạy chương trình của mình trên các môi trường khác nhau một cách nhanh nhất."_

Lại có định nghĩa rằng: _"Docker là một phương thức để đóng gói và sắp xếp phần mềm."_

Ví dụ: 
123study.vn yêu cầu chạy trên nginx với module vod (stream video)
=> Để cài đc 1 môi trường có đầy đủ như thế rất khó
=> Hầu hết các beginer tham gia dự án chỉ chạy apache2, ko có module xử lý cho stream video 
=> Môi trường dev khác xa môi trường thực tế

=> Cần tạo ra 1 môi trường giống môi trường server, nhưng ko cần phải cài đặt nhiều, người ko biết gì chỉ cần chạy lệnh là có môi trường

Docker bao gồm 2 thành phần chính: 
* `Docker Engine` :  dùng để tạo ra Docker image và chạy Docker container.
* `Docker Hub` : dịch vụ lưu trữ giúp chứa các Docker image.
* `Docker Machine` : Tạo ra các `Docker Engine` trên máy chủ
* `Docker Compose`: chạy ứng dụng bằng cách định nghĩa cấu hình các Docker container thông qua tệp cấu hình
* `Docker image`: một dạng tập hợp các tệp của ứng dụng, được tạo ra bởi Docker engine. Nội dung của các Docker image sẽ không bị thay đổi khi di chuyển. Docker image được dùng để chạy các Docker container.
* `Docker Container`: một dạng runtime của các Docker image, dùng để làm môi trường chạy ứng dụng.

## Sự khác biệt giữa Docker Image và Docker Container
### Docker Images

Là một template chỉ cho phép đọc, ví dụ một image có thể chứa hệ điều hành Ubuntu và web app. Images được dùng để tạo Docker container. Docker cho phép chúng ta build và cập nhật các image có sẵn một cách cơ bản nhất, hoặc bạn có thể download Docker images của người khác.

### Docker Container

Docker container có nét giống với các directory. Một Docker container giữ mọi thứ chúng ta cần để chạy một app. Mỗi container được tạo từ Docker image. Docker container có thể có các trạng thái run, started, stopped, moved và deleted.

## Làm thế nào để tạo ra một Docker Image bằng Dockerfile ?

### Dockerfile là gì?

Dockerfile là một tập tin dạng text chứa một tập các câu lệnh để tạo mới một Image trong Docker.

Một số lệnh trong Dockerfile:

* FROM <base_image>:<phiên_bản>: đây là câu lệnh bắt buộc phải có trong bất kỳ Dockerfile nào. Nó dùng để khai báo base Image mà chúng ta sẽ build mới Image của chúng ta.
* MAINTAINER <tên_tác_giả>: câu lệnh này dùng để khai báo trên tác giả tạo ra Image, chúng ta có thể khai báo nó hoặc không.
* RUN <câu_lệnh>: chúng ta sử dụng lệnh này để chạy một command cho việc cài đặt các công cụ cần thiết cho Image của chúng ta.
* CMD <câu_lệnh>: trong một Dockerfile thì chúng ta chỉ có duy nhất một câu lệnh CMD, câu lệnh này dùng để xác định quyền thực thi của các câu lệnh khi chúng ta tạo mới Image.
* ADD <src> <dest>: câu lệnh này dùng để copy một tập tin local hoặc remote nào đó (khai báo bằng <src>) vào một vị trí nào đó trên Container (khai báo bằng dest).
* ENV <tên_biến>: định nghĩa biến môi trường trong Container.
* ENTRYPOINT <câu_lệnh>: định nghĩa những command mặc định, cái mà sẽ được chạy khi container running.
* VOLUME <tên_thư_mục>: dùng để truy cập hoặc liên kết một thư mục nào đó trong Container.

Sự khác biệt giữa Docker và Hypervisors
Sự khác biệt giữa Docker Image và Docker Container
Làm thế nào để tạo ra một Docker Image bằng Dockerfile
## Các câu hỏi tự đặt ra: 

Kết nối vào 1 docker container thế nào ? 


## Tham khảo 
* https://viblo.asia/p/docker-nhung-kien-thuc-co-ban-phan-1-bJzKmM1kK9N
* https://www.tutorialspoint.com/docker/docker_overview.htm
* https://docs.docker.com/engine/docker-overview/#the-docker-platform
