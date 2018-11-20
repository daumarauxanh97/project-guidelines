# Project-Guidelines

Trong khi việc phát triển dự án mới giống như lăn bánh trên đồng cỏ xanh việc duy trì nó giống như cơn ác mộng tiềm năng đối với người khácĐây là danh sách các hướng dẫn chúng tôi đã tìm,viết và gộp chúng lai(chúng tôi nghĩ) hoạt động rất tốt với hầu hết các dự án javascript tại vầ cacsc chỗ khác.Nếu bạn muốn chia sẻ bài tập hay,hay bạn nghĩ một trong những hướng dẫn này nên được bỏ đi,hãy thoải mải chia sẻ với chúng tôi.

- Git
  - Một vài luật về git
  - Luồng công việc git
  - Viết commit message hay
- Tài liệu
- Môi trường
  - Môi trường dev nhất quán
  - Phụ thuộc nhất quán
- Phụ thuộc
- Kiểm thử
- Cấu trúc và đặt tên
- Phong cách code
  - Một vài hướng dẫn về phong cách code
  - Thực thi phong cách code tiêu chuẩn
- Nhật ký
- API
  - Thiết kế API
  - Bảo mật API
  - Tài liệu API
- Cấp phép

### 1.Git

### 1.1 Một vài luật về git

Có một vài luật về git nên nhớ trong đầu

- Thực hiện công trong một feature branch

 _Why_
 
 >Bởi bằng cách này tất cả công việc được thực hiện cô lập trong một branch riêng biệt hơn là branch chính.Nó cho phép bạn gửi nhiều pull requests mà không bị nhầm lẫn.Bạn có thể lặp việc này mà không là ảnh hưởng branch chính với code không ổn định,chưa hoàn thành đọc thêm...
 
- Branch tách khỏi `develop`

 _Why_
 
 >Bằng cách này bạn có thể chắc chắn rằng câu lêệnh trong master sẽ chạy mà không có lỗi trong hầu hết các trường hợp và có thể sử dụng  trực tiếp để phát hành (điều này có thể là quá mức cần thiết đối với một số dự án).
 
_ Không bao giờ đẩy vào `develop` hay branch `master`.Hãy tạo một pull request

_Why_

 >Nó thông báo cho các thành viên trong nhóm rằng họ đã hoàn thành một tính năng. Nó cũng cho phép dễ dàng đánh giá ngang hàng của câu lệnh và dành cho diễn đàn để thảo luận về tính năng được đề xuất.

- Cập nhật develop branch cục bộ của bạn và thực hiện việc tương tác rebase trước khi đẩy tính năng và thực hiện pull request

_Why_

 >Rebasing sẽ hợp nhất trong branch được yêu cầu (master hoặc development) và gán các commit mà bạn đã thực hiện cục bộ lên đầu đầu lịch sử mà không cần tạo hợp nhất commit (giả sử không có xung đột). Kết quả là một lịch sử đẹp và sạch sẽ. đọc thêm...
 
- Xử lý các xung đột tiềm năng trong khi đang rebase hay trước khi tạo một pull request

- Xóa các branch tính năng cục bộ và từ bên ngoài sau khi hợp nhất ..

 _Why_
 
 >Nó sẽ trộn danh sách các branch của bạn với các branch chết. Nó đảm bảo bạn chỉ hợp nhất các chi nhánh trở lại vào (master hoặc phát triển) một lần. Các branch tính năng chỉ nên tồn tại trong khi công việc vẫn đang trong quá trình
 
 - Trước khi thực hiện một pull request hãy chắc rằng tiính năng của bạn chạy thành công và qua các bài kiểm tra (bao gồm kiểm tra về phong cách code)
 
  _Why_
  
  >Bạn chuẩn bị cho câu lệnh của bạn vào một branch ổn định .Nếu branch tính năng của bạn kiểm tra lỗi có khả năng cao là branch đích cũng sẽ chạy lỗi.Bên cạnh đó bạn phải kiểm tra phong cách code trước khi tạo một pull request nó hỗ trợ khả năng đọc và giảm khả năng sửa lỗi định dạng được trộn lẫn với các thay đổi thực sự.
  
 - Sử dụng this `ignore` file
 
   _Why_
   
   >Đã có sẵn danh sách các tệp hệ thống không nên gửi cùng với mã của bạn vào một repository bên ngoài. Ngoài ra, nó không bao gồm cài đặt thư mục và tệp cho hầu hết các trình chỉnh sửa được sử dụng, cũng như các thư mục phụ thuộc phổ biến nhất.
   
 - Bảo vệ branch `develop` và branch `master` của bạn
 
  _Why_
  
   >Nó bảo vệ các nhánh sản phẩm sẵn sàng của bạn khỏi những thay đổi bất ngờ và không thể đảo ngược. đọc thêm ... Github, Bitbucket và GitLab
   
### 1.2 Luồng công việc git

Bởi vì hầu hết các lí do bên trên chúng ta sử dụng Feature-branch-workflow với tương tác rebase và một số yếu tố của Gitflow (đặt tên và có một develop branch). Các bước chính như sau:
  
