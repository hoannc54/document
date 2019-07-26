# Cách làm việc với GIT trong dự án

## Các kiến thức cần nắm vững

Các khái niệm phải nắm vững trước : 

* [commit](https://git-scm.com/docs/git-commit)
* [branch](https://backlog.com/git-tutorial/vn/stepup/stepup1_1.html)
* [merge](https://git-scm.com/docs/git-merge)

## Thông tin

### Branch

Trên remote : 
* `master` : Nhánh chính của dự án, chứa code chuẩn dự án 
* `deploy` : Nhánh tương ứng với code trên server
* `develop` : Nhánh được cập nhật liên tục trong quá trình phát triển  tính năng hoặc fix lỗi
* `cá nhân`: Mỗi thành  viên có một nhánh cá nhân trên remote

**Cách làm việc dưới local**

Mọi nhánh con để thực hiện công việc  đều phải được checkout từ nhánh develop (để có cập nhật code mới nhất)

`(develop) git checkout -b branch`

### Git flow dự án

Trường hợp mới join cần tạo một nhánh cá nhân riêng trên remote để lưu code (vì chưa đảm bảo để đẩy trực tiếp lên nhánh develop)
* Checkout từ nhánh `develop` ra nhánh cá nhân để sử dụng
* Thực hiện code trên nhánh cá nhân
* Trước khi push lên remote cần merge từ nhánh `develop` để đảm bảo code mới nhất và đồng bộ
* Push code lên nhánh cá nhân trên remote

Bắt đầu một tính năng mới : 
* Checkout từ `develop` ra nhánh `feature_tinhnang` trên local
* Thực hiện coding trên nhán `feature_tinhnang` (được phép commit nhiều lần tại nhánh local này)
* Sau khi hoàn thành đứng ở nhánh `develop` thực hiện `merge --squash` và viết lại với duy nhất 1 commit để push lên nhánh `develop`
* Leader thực hiện pull từ nhánh `develop` để kiểm tra code nếu ok thì merge vào nhánh `master` hoặc `deploy`

Sửa đổi nóng (hot fix)
* Pull code mới nhất từ nhánh `develop`
* Checkout từ `develop` ra nhánh mới với tênn `hotfix_problem`
* Thực hiện code fix
* Quay lại `develop` và `merge --squash` 
 
#### Khi merge



#### Commit

Quy định khi commit:
Với commit đơn giản
Tiêu đề commit = `Verb` + `content` (Tóm tắt nội dung thay đổi trong commit)

`Verbs`: 

* `Add` : Thêm mới một tính năng
* `Update`: Cập nhật các thành phần của tính năng
* `Improve`: Cải thiện 1 tính năng nhất định hoặc thành phần của tính năng
* `Remove`: Xoá file, xoá code, ...
* `Fix`: Sửa lỗi cho một vấn đề
* `Change`
* ......
* 
Khuyến khích sử dụng Tiếng Anh khi viết message commit

Viết message commit : 

Với nội dung dài hoặc commit phức tạp cần giải thích 
```
Dòng thứ 1: Tiêu đề commit (Tóm tắt nội dung thay đổi trong commit)
Dòng thứ 2: Dòng trống
Dòng thứ 3 trở đi: Lý do đã thay đổi
```

Chú ý: Những thay đổi mang ý nghĩa khác nhau chẳng hạn như thêm chức năng hay sửa lỗi thì hãy cố gắng chia ra rồi commit. Để sau này khi xem lịch sử và tìm kiếm một nội dung thay đổi định sẵn sẽ dễ dàng hơn.

## Tài liệu tham khảo
* Tài liệu gốc : https://git-scm.com/
* https://learngitbranching.js.org/
* Đóng issue trên git : https://docs.gitlab.com/ee/user/project/issues/closing_issues.html



