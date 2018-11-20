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

  _Tại sao_
 
 >Bởi bằng cách này tất cả công việc được thực hiện cô lập trong một branch riêng biệt hơn là branch chính.Nó cho phép bạn gửi nhiều pull requests mà không bị nhầm lẫn.Bạn có thể lặp việc này mà không là ảnh hưởng branch chính với code không ổn định,chưa hoàn thành đọc thêm...
 
- Branch tách khỏi `develop`

 _Tại sao_
 
 >Bằng cách này bạn có thể chắc chắn rằng câu lêệnh trong master sẽ chạy mà không có lỗi trong hầu hết các trường hợp và có thể sử dụng  trực tiếp để phát hành (điều này có thể là quá mức cần thiết đối với một số dự án).
 
_ Không bao giờ đẩy vào `develop` hay branch `master`.Hãy tạo một pull request

 _Tại sao_

 >Nó thông báo cho các thành viên trong nhóm rằng họ đã hoàn thành một tính năng. Nó cũng cho phép dễ dàng đánh giá ngang hàng của câu lệnh và dành cho diễn đàn để thảo luận về tính năng được đề xuất.

- Cập nhật develop branch cục bộ của bạn và thực hiện việc tương tác rebase trước khi đẩy tính năng và thực hiện pull request

 _Tại sao_

 >Rebasing sẽ hợp nhất trong branch được yêu cầu (master hoặc development) và gán các commit mà bạn đã thực hiện cục bộ lên đầu đầu lịch sử mà không cần tạo hợp nhất commit (giả sử không có xung đột). Kết quả là một lịch sử đẹp và sạch sẽ. đọc thêm...
 
- Xử lý các xung đột tiềm năng trong khi đang rebase hay trước khi tạo một pull request

- Xóa các branch tính năng cục bộ và từ bên ngoài sau khi hợp nhất ..

  _Tại sao_
 
 >Nó sẽ trộn danh sách các branch của bạn với các branch chết. Nó đảm bảo bạn chỉ hợp nhất các chi nhánh trở lại vào (master hoặc phát triển) một lần. Các branch tính năng chỉ nên tồn tại trong khi công việc vẫn đang trong quá trình
 
 - Trước khi thực hiện một pull request hãy chắc rằng tiính năng của bạn chạy thành công và qua các bài kiểm tra (bao gồm kiểm tra về phong cách code)
 
   _Tại sao_
   
  >Bạn chuẩn bị cho câu lệnh của bạn vào một branch ổn định .Nếu branch tính năng của bạn kiểm tra lỗi có khả năng cao là branch đích cũng sẽ chạy lỗi.Bên cạnh đó bạn phải kiểm tra phong cách code trước khi tạo một pull request nó hỗ trợ khả năng đọc và giảm khả năng sửa lỗi định dạng được trộn lẫn với các thay đổi thực sự.
  
 - Sử dụng this `ignore` file
 
    _Tại sao_
   
   >Đã có sẵn danh sách các tệp hệ thống không nên gửi cùng với mã của bạn vào một repository bên ngoài. Ngoài ra, nó không bao gồm cài đặt thư mục và tệp cho hầu hết các trình chỉnh sửa được sử dụng, cũng như các thư mục phụ thuộc phổ biến nhất.
   
 - Bảo vệ branch `develop` và branch `master` của bạn
 
  _Tại sao_
  
   >Nó bảo vệ các nhánh sản phẩm sẵn sàng của bạn khỏi những thay đổi bất ngờ và không thể đảo ngược. đọc thêm ... Github, Bitbucket và GitLab
   
### 1.2 Luồng công việc git

Bởi vì hầu hết các lí do bên trên chúng ta sử dụng Feature-branch-workflow với tương tác rebase và một số yếu tố của Gitflow (đặt tên và có một develop branch). Các bước chính như sau:
  
  - Đối với project mới khởi tạo một git repository trong thư mục dự án. Đối với các tính năng / thay đổi tiếp theo, bước này sẽ bị bỏ qua.

  ```
  cd <project directory>
  git init
  ```
  
  - Xem thử branch feature,branch đước sưa lỗi mới
  
  ```
  git checkout -b <branchname>
  ```
  - Sửa đổi
  
  ```
  git add <file1> <file2> ...
  git commit
  ```
  
    _Tại sao_
   
   >`git add <file1> <file2> ... `Bạn chỉ nên thêm những file tạo nên một sự thay đổi nhỏ và mạch lạc.
   
   >`git commit` sẽ tạo một trình soạn thảo cho phép bạn tách nội dung ra khỏi body.
   
   >Đọc thêm trong mục 1.3
   
   Mẹo
   
   >Bạn nên sử dụng `git add -p` thay thế việc mà sẽ cho bạn cơ hội để xem xét tất cả các thay đổi được giới thiệu từng cái một, và quyết định có bao gồm chúng trong commit hay không.
   
  - Đồng bộ hóa với remote để nhận các thay đổi bạn đã bỏ lỡ.
  
  ```
  git checkout develop
  git pull
  ```
    _Tại sao_
   
   >Điều này sẽ cho bạn cơ hội để đối phó với các xung đột trên máy tính của bạn trong khi rebasing (sau này) hơn là tạo một Pull Request có chứa xung đột.
   
   - Cập nhật branch tính năng của bạn với những thay đổi mới nhất từ develop bằng cách tương tác rebase.
   
   ```
   git checkout <branchname>
   git rebase -i --autosquash develop
   ```
   _Tại sao_
   
   >Bạn có thể sử dụng `--autosquash ` để gộp tất cả các commit của bạn thành một commit duy nhất. Không ai muốn nhiều commit cho một tính năng duy nhất trong develop branch.
   
   - Nếu bạn không có xung đột bỏ qua bước này .Nếu bạn có xung đột sủa chữa nó và tiếp tục rebase
   
   ```
   git add <file1> <file2> ...
   git rebase --continue
   ```
   - Đẩy branch của bạn. Rebase sẽ thay đổi lịch sử, vì vậy bạn sẽ phải sử dụng `-f ` để ép buộc các thay đổi vào branhc bên ngoài. Nếu ai đó đang làm việc trên branch của bạn, hãy sử dụng ít phá hoại hơn `--force-with-lease `.
   
     _Tại sao_
    
     >Khi bạn thực hiện rebase, bạn đang thay đổi lịch sử trên branch tính năng của bạn. Kết quả là, Git sẽ từ chối push git bình thường. Thay vào đó, bạn sẽ cần sử dụng cờ `-f` hoặc `--force.` đọc thêm...
     
   - Tạo một pull request
   
   - Pull request sẽ được người đánh giá chấp nhận, hợp nhất và đóng.
   
   - Xóa branch tính năng cục bộ của bạn nếu bạn đã hoàn tất.
   
   ```
   git branch -d <branchname>
   ```
   
   
   để xóa tất cả các nhánh không còn ở trong remote
   
   ```
   git fetch -p && for branch in `git branch -vv --no-color | grep ': gone]' | awk '{print $1}'`; do git branch -D $branch; done
   ```
   
### 1.3 Viết commit message tốt

Có một hướng dẫn tốt cho việc tạo ra các commit và gắn bó với nó làm cho làm việc với Git và cộng tác với người khác dễ dàng hơn rất nhiều. Dưới đây là một số quy tắc chủ chốt (nguồn):

 - Tách nội dung ra khỏi thân bằng một dòng mới giữa hai đối tượng.
 
  _Tại sao_
  
  >Git đủ thông minh để phân biệt dòng đầu tiên của commit message của bạn dưới dạng tóm tắt. Trong thực tế, nếu bạn thử git shortlog, thay vì git log, bạn sẽ thấy một danh sách dài các commit message, bao gồm id của commit, và duy nhất bản tóm tắt.
  
 - Giới hạn dòng chủ đề tới 50 ký tự gộp thân trong 72 ký tự
 
  _Tại sao_
  
  >Các commit phải được tinh chỉnh và tập trung càng tốt, nó không phải là nơi để tiết lộ. đọc thêm...
  
  - Viết hoa dòng chủ đề
  
  - Không kết thúc dòng chủ đề với một dấu chấm.
  
  - Sử dụng tâm trạng bắt buộc trong dòng chủ đề.
  
   _Tại sao_
   
   Thay vì viết thông báo cho biết những gì một người commit đã làm. Tốt hơn là xem xét các thông báo này như là các hướng dẫn cho những gì sẽ được thực hiện sau khi commit được áp dụng trên repository. đọc thêm..
   
   - Sử dụng body để giải thích cái gì và tại sao chứ không phải cách thức.
  
