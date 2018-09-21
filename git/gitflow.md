# Mô hình git sử dụng

## Mô hình lý thuyết 
Mô hình áp dụng với sản phẩm có thiết kế chuẩn chỉnh ban đầu, các tính năng rõ ràng dự trù sẵn, có từng giai đoạn phát triển
## Mô hình thực tế sử dụng
Áp dụng với mô hình sản phẩm phát triển liên tục
Những branh chính:

* Master
* Develop
* Deploy

Trong đó 
* Master : Được coi là nhánh chính với `HEAD` ở trạng thái `production-ready` (sẵn sàng cho sản phẩm)
* Develop: Được coi là nhánh chính với `HEAD` phản ánh thay đổi mới nhất trong quá trình phát triển, chuẩn bị cho release tiếp theo 
* Deploy: Nhánh được coi là giống code đang chạy trên server


Những nhánh phụ:
Mục đích: 
* Các thành viên trong team phát triển song song 
* Dễ dàng tracking theo feature
* Chuẩn bị cho release 
* Sẵn sàng fix nhanh các vấn đề trong production
=> Các nhánh này chỉ tồn tại trong thời gian ngắn, xoá đi sau khi xong nhiệm vụ
