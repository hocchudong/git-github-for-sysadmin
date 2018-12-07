
## Git và Github cho sysadmin

### Mục lục

[I. Mở đầu](#Modau)

[II. Ngôn ngữ Markdown](#ngonngumarkdown)
- [1. Thẻ tiêu đề](#thetieude)
- [2. Chèn link, chèn ảnh](#chenlinkchenanh)
- [3. Ký tự in đậm, in nghiêng](#kytuindaminnghieng)
- [4. Trích dẫn, bo chữ](#trichdanbochu)
- [5. Gạch đầu dòng](#gachdaudong)
- [6. Tạo bảng](#taobang)
- [Mẹo](#meo)
	
[III. Các thao tác với git và github](#cacthaotacvoigitvagithub)
- [0. Repo](#repo)
- [1. Cài đặt](#caidat)

  - [1.1. Linux](#linux)
  - [1.2. Windows](#windows)

- [2. Thao tác với Repo](#thaotacvoirepo)

  - [2.1. Trên Linux](#21trenlinux)
    - [2.1.1. Tạo mới](#211taomoi)
    - [2.1.2. Clone](#212clone)
    - [2.1.3. Add, commit, push](#213addcommitpush)
    - [2.1.4. Pull](#214pull)
  - [2.2. Trên Windows](#22trenwindows)
    - [2.2.1. Tạo một repo mới](#221taomotrepomoi)
    - [2.2.2. Clone](#222clone)
    - [2.2.3. Add, commit, push, pull ](#223)

- [3. Thao tác với tổ chức trong Github](#3)
- [4. Thao tác với nhánh (branch)](#4)
- [5. Issues](#5)
	
[Tổng kết](#Tongket)

===========================

<a name="Modau"></a>
## I. Mở đầu

`Git` là một phần mềm dùng để quản lý phiên bản của mã nguồn tương tự như `SVN` nhưng có nhiều ưu điểm hơn, `Git` đang được sủ dụng rộng rãi hiện nay.
Tuy nhiên trong bài viết này, tôi sẽ nói về git một cách "cá nhân" hơn, mang tính chia sẻ những cái tôi hay làm và hướng tới những người là sysadmin. Mong nhận được ý kiến đóng góp của các bạn.

#### Một số khái niệm cần làm rõ

**`Git` và `Github` khác nhau như thế nào?**

Lấy ví dụ, bạn có một đoạn script dài 20 dòng, hôm sau bạn tối ưu nó đi, chỉ còn 15 dòng, một ngày khác bạn sửa ở script đó một vài chỗ. Git ghi lại những thời điểm thay đổi đó của bạn và source code của bạn tại thời điểm đó.

Github là một trang web, cho phép bạn lưu source code của mình lên đó. Sự kết hợp hoàn hảo giữa Git và Github mang lại một sự thuận tiện không hề nhỏ cho người dùng. Bạn có thể thay đổi đoạn code của mình mọi lúc mọi nơi mà không sợ bị ghi đè lên hay bị mất dữ liệu do hỏng hóc vì dữ liệu của bạn được lưu cả trên trang web Github và máy cá nhân. Bạn cũng có thể khôi phục được code của mình về một thời điểm bất kỳ nào đó.

Github có bản free và mất phí. Với Github free thì source code của bạn sẽ công khai, có nghĩa là ai cũng có thể xem code của bạn. Nó phù hợp với các phần mềm nguồn mở, và cũng có thể trở thành một blog cá nhân của chính các bạn như các trang blogspot, wordpress,...

Muốn có thể tạo một kho code bí mật của riêng mình thì bạn phải trả phí.

Đối với cá nhân tôi thì github free là quá đủ cho mục đích lưu trữ và chia sẻ thông tin.

**Cần phải làm gì để có thể sử dụng `Github`?**

- B1: Đăng ký một tài khoản tại [github](https://github.com) và đăng nhập

Tôi chắc chắn rằng một khi bạn đã đọc đến đây thì bạn đã biết thực hiện bước trên như thế nào :)

- B2: Học cách sử dụng ngôn ngữ `Markdown`

Bạn có thể bỏ qua bước này nếu bạn đã biết hoặc các bạn xác định không sử dụng nó để viết.

Theo cá nhân tôi thì các bạn nên viết bằng Markdown trong Github vì nó sẽ mang lại sự tường minh cho bài viết của bạn.

Bạn chỉ cần bỏ ra khoảng 2h là đã có thể sử dụng ngôn ngữ này như ý muốn.

- B3: Tạo một repo đầu tiên và gõ Hello world bằng Markdown

Sau đó tạo các repo tùy mục đích, clone nó về client và code.

Bước này tôi sẽ hướng dẫn chi tiết hơn ở phần sau.

<a name="ngonngumarkdown"></a>
## II. Ngôn ngữ Markdown

Ngôn ngữ này khá đơn giản, bạn có thể đọc tại [đây](http://daringfireball.net/projects/markdown/syntax) để biết cách sử dụng.

Nhưng với tôi, tôi không dùng hết từng ấy thứ cho nên tôi chỉ nhớ một số cái tôi hay dùng, cách tôi dùng như sau:

Tạo một file có tên bất kỳ với đuôi .md. Có thể dùng `notepad`, `notepad++`, `vi`, `nano`,... hay bất cứ thứ gì mà bạn muốn.

Một số phương pháp tôi hay sử dụng để viết:

<a name="thetieude"></a>
### 1. Thẻ tiêu đề

Markdown sử dụng kí tự # để bắt đầu cho các thẻ tiêu đề, có thể dùng từ 1 đến 6 ký tự # liên tiếp. Mức độ riêu đề giảm dần từ 1 đến 6

Tùy mục đích và ý thích bạn có thể sử dụng cách này để thể hiện các chỉ mục khác nhau.

Ví dụ:

```
# 1.Tiêu đề cấp 1
```

# 1.Tiêu đề cấp 1

```
## 2.Tiêu đề cấp 2
```

## 2.Tiêu đề cấp 2

```
###### 6.Tiêu đề cấp 6
```

###### 6.Tiêu đề cấp 6

<a name="chenlinkchenanh"></a>
### 2. Chèn link, chèn ảnh

Để chèn hyperlink bạn chỉ cần paste luôn linh đó vào file .md

```
https://github.com
```

https://github.com

Hoặc bạn cũng có thể sử dụng cú pháp sau để thu ngắn đường dẫn của link

```
[Github](https://github.com)
```

Kết quả là:

[Github](https://github.com)

Để chèn ảnh thì bạn hãy sử dụng cú pháp sau:

```
<img src="link_anh_cua_ban">
```

Tôi thường sử dụng công cụ [Lightshot](https://app.prntscr.com/en/index.html) để chụp ảnh màn hình và up hình đó lên trang http://i.imgur.com/ để lấy đường dẫn ảnh đưa vào Github

Hai công cụ này khá dễ sử dụng, bạn chỉ cần chụp màn hình bằng Lightshot ấn Ctrl + C để copy và Ctrl + V để paste vào trình duyệt tại trang web http://i.imgur.com/

<a name=kytuindaminnghieng></a>
### 3. Ký tự in đậm, in nghiêng

- Để in đậm một đoạn text  bạn chỉ cần làm như sau:

```
**từ cần in đậm**
```

**từ cần in đậm**

- Để in nghiên một đoạn text  bạn chỉ cần làm như sau:

```
*từ cần in nghiêng*
```

*từ cần in nghiêng*

<a name="trichdanbochu"></a>
### 4. Trích dẫn, bo chữ

Để bo một đoạn text thì bạn chỉ cần sử dụng cú pháp sau:

```
`đoạn cần bo`
```

Kết quả là: `đoạn cần bo`

Để làm nổi bật một đoạn, chẳng hạn như một đoạn shell hay file cấu hình bạn có thể sử dụng cú pháp như ví dụ sau:

    ```sh
    auto eth0
    iface eth0 inet static
    ipaddress 10.10.10.10
	netmask 255.255.255.0
	gateway 10.10.10.1
	dns-nameservers 8.8.8.8
    ```

Kết quả như sau:

```sh
auto eth0
iface eth0 inet static
ipaddress 10.10.10.10
netmask 255.255.255.0
gateway 10.10.10.1
dns-nameservers 8.8.8.8
```

<a name="gachdaudong"></a>
### 5. Gạch đầu dòng

Để sử dụng gạch đầu dòng bạn chỉ cần sử dụng cú pháp sau:

```
- Gạch đầu dòng thứ nhất
  
  - Thụt với đầu dòng 1
  
  - Thụt với đầu dòng 1
 
- Gạch đầu dòng thứ hai
  
  - Thụt với đầu dòng 2
  
  - Thụt với đầu dòng 2
  
```

- Gạch đầu dòng thứ nhất
  
  - Thụt với đầu dòng 1
  
  - Thụt với đầu dòng 1
  
- Gạch đầu dòng thứ hai
  
  - Thụt với đầu dòng 2
  
  - Thụt với đầu dòng 2
  

<a name="taobang"></a>
### 6. Tạo bảng

Bạn có thể sử dụng cú pháp sau để tạo bảng:

```
| Cột 1 Hàng 1 | Cột 2 | Cột 3| Cột 4 |
|--------------|-------|------|-------|
| Hàng 2 | 2 x 1 | 2 x 2 | 2 x 3 | 2 x 4 |
| Hàng 3 | 3 x 1 | 3 x 2 | 3 x 3 | 3 x 4 |
| Hàng 4 | 4 x 1 | 4 x 2 | 4 x 3 | 4 x 4 |
```

Kết quả:

| Cột 1 Hàng 1 | Cột 2 | Cột 3| Cột 4 |
|--------------|-------|------|-------|
| Hàng 2 | 2 x 1 | 2 x 2 | 2 x 3 | 2 x 4 |
| Hàng 3 | 3 x 1 | 3 x 2 | 3 x 3 | 3 x 4 |
| Hàng 4 | 4 x 1 | 4 x 2 | 4 x 3 | 4 x 4 |

<a name="meo"></a>
###*Mẹo:*

- Sử dụng trang http://markdownlivepreview.com/ paste vào đó đoạn markdown bạn viết và xem trước để chỉnh sửa cho phù hợp.

- Bạn cũng có thể sử dụng những đoạn markdown của người khác đã viết trước để tham khảo.

Như vậy bạn đã có thể trình bày github của mình một cách sáng sủa bằng markdown.

<a name="cacthaotacvoigitvagithub"></a>
## III. Các thao tác với Git và Github

<a name="repo"></a>
### 0. Repo

Git là một công cụ để quản lý mã nguồn, nhưng tôi không phải là một coder nên tôi sẽ không sử dụng Git theo cách mà các coder hay sử dụng.
Tôi sử dụng git và github để lưu trữ các file cấu hình của mình, các script, viết các bài hướng dẫn, các bản nháp,...
Các repo là những nơi tôi phân loại, lưu trữ những thứ bên trên và nó được lưu cả ở máy trạm và ở server github.
Để làm việc với repo thì bạn phải hiểu về nó. Một số điều bạn cần biết là: 

**Ba trạng thái của một repo:**

<img src=http://i.imgur.com/qkmdJSR.png>

Như hình trên bạn có thể thấy có 3 điểm cần lưu ý:

- Working dir: đây là nơi bạn thực hiện các thao tác chỉnh sửa với file mã nguồn của mình, nó có thể là eclipse, netbean, notepad++,...

- Stagging area: những sự thay đổi của bạn với file mã nguồn được lưu lại, giống như bạn ấn Save trong một file notepad.

- Git directory: nơi lưu trữ mã nguồn của bạn (ở đây là github)

Tương ứng với 3 vị trí này ta có các hành động:

- Add: lưu file thay đổi (mang tính cục bộ) - tương ứng với câu lệnh `git add`

- Commit: Ghi lại trạng thái thay đổi tại máy local (ví dụ như bạn có thể ấn Save nhiều lần với file README.md nhưng chỉ khi commit thì trạng thái của lần ấn Save cuối cùng trước đó mới được lưu lại) - tương ứng với câu lệnh `git commit`

- Push: Đẩy những thay đổi từ máy trạm lên server - tương đương lệnh `git push`

- Pull: đồng bộ trạng thái từ server về máy trạm - tương đương lệnh `git pull`

<a name="caidat"></a>
### 1. Cài đặt

<a name="linux"></a>
#### 1.1. Linux

Với OS là Ubuntu:

> apt-get install git
	
Với OS là Fedora, Centos

> yum instal git

Các thiết lập ban đầu:

- Bạn cần thiết lập tên và email của mình để mỗi khi commit lên server sẽ nhận biết được ai commit lên vì một repo có thể có nhiều người tham gia.
	
> git config --global user.name "Duc NC"

> git config --global user.email nguyencongduc3112@gmail.com

- Lựa chọn trình soạn thảo mặc định, có thể là vi, vim, nano,...

> git config --global core.editor vi

- Liệt kê các thiết lập:

> git config --list

**Liên kết với tài khoản github bằng SSH**

> ssh-keygen -t rsa

```sh
Enter file in which to save the key (/root/.ssh/id_rsa): [Press enter]
Enter passphrase (empty for no passphrase): [Press enter]
Enter same passphrase again: [Press enter]
Your identification has been saved in /root/.ssh/id_rsa.
Your public key has been saved in /root/.ssh/id_rsa.pub.
```

Nếu bạn nhập passphrase thì hãy nhớ pass này!

Kết quả:
> ls ~/.ssh/

```sh
id_rsa       id_rsa.pub   known_hosts
```

> ssh-agent -s

> ssh-add ~/.ssh/id_rsa

> cat ~/.ssh/id_rsa.pub

copy đoạn mã này

Truy cập đường dẫn sau https://github.com/settings/ssh (đảm bảo bạn đã đăng nhập vào github), chọn Add SSH key, đặt tên cho key này tại `Title` và paste nội dung vừa copy vào ô `Key`

<img src=http://i.imgur.com/zuxavZ5.png>

Lúc này bạn đã có thể commit lên github tại máy local mà không cần nhập username và password.

<a name="windows"></a>
#### 1.2. Windows	

Download tại địa chỉ: https://windows.github.com/

Cài đặt bình thường, yêu cầu phải có .NET 4.5

Giao diện của chương trình:

<img src=http://i.imgur.com/Ebx6dJD.png>

Thêm tài khoản Github:

- Click vào tool and options (hình bánh răng cạnh biểu tượng Sync) chọn options, Add account. Khai báo username và password trên github.

- Tại mục Configure git thêm Tên và email của mình

<img src=http://i.imgur.com/DSLP60i.png>

Click Update


<a name="thaotacvoirepo"></a>
### 2. Thao tác với Repo

<a name="21trenlinux"></a>
#### 2.1. Trên Linux

<a name="211taomoi"></a>
##### 2.1.1. Tạo mới

Tạo một repo mới trên trang github.com

<img src=http://i.imgur.com/alRFWKl.png>

<img src=http://i.imgur.com/MJZjYMm.png>

<a name="212clone"></a>
##### 2.1.2. Clone

Clone repo đó về bằng một trong các cách sau:

**Linux**

***SSH:***
`git clone git@github.com:ducnc92/demo1.git`

hoặc: `git clone git@github.com:ducnc92/demo1.git /opt/demo` để clone vào thư mục /opt/demo

đối với phương pháp này các bạn cần nhập passphrase của ~/.ssh/id_rsa (có thể không cần nếu bạn không đặt passphrase)

***HTTPS:***
`git clone https://github.com/ducnc92/demo1.git`

hoặc: `git clone https://github.com/ducnc92/demo1.git /opt/demo` để clone vào thư mục /opt/demo

Để lấy các link SSH, HTTPS này ta làm như sau: Click vào các hyperlink HTTPS hoặc SSH rồi click Copy to clipboard.

<img src=http://i.imgur.com/1DozAVz.png>

Ở đây tôi sử dụng lệnh `git clone git@github.com:ducnc92/demo1.git`

Lúc này trong thư mục hiện tại sẽ có thêm thư mục demo1 chứa các file trong repo trên github.

Chuyển vào thư mục này:

> cd demo1/

> ls

Lúc này sẽ thấy trong thư mục này có file `README.md`. Để sửa file này ta có thể sử dụng bất cứ trình soạn thảo nào, chẳng hạn vi, nano, gedit,...
 
> vi README.md

Thêm vào nội dung như sau:

```
Xin chao!
Toi la Ducnc.
```

Tạo một thư mục mới, chẳng hạn tên là script để chứa các script của tôi.

> mkdir script

Tạo một script mới trong thư mục đó.

> vi script/script1.sh

```sh
#!/bin/sh
echo "Hello Python Vietnam"
sleep 10
```

bằng cách tương tự các bạn có thể tạo thêm nhiều thư mục, file hướng dẫn, cấu hình, script,... tùy ý

<a name="213addcommitpush"></a>
##### 2.1.3. Add, commit, push

Để thực hiện hành động `add` ta sử dụng lệnh sau

> git add README.md
để `add` file README.md

hoặc `git add *` để add tất cả các file hiện có.
 
Để thự hiện hành động commit file README.md ta thực hiện lệnh
> git commit README.md

hoặc `git commit *` để commit tất cả.

ta nên thêm tham số -m để ghi lại một comment cho hành động đó
 
> git commit README.md -m "ducnc sua doi" 

Lúc này các thay đổi của bạn đã được lưu lại trên máy cục bộ. Để đồng bộ lên server Github ta thực hiện lệnh:

> git push origin master

=> nhập passphrase (nếu bạn đặt passphrase ở mục 1.1.) với phương pháp clone ssh hoặc nhập username, password nếu clone bằng https

<img src=http://i.imgur.com/VOPSzBT.png>

Lúc này trở lại trang github.com và xem `repo script` lúc đầu sẽ thấy các commit của ta đã được đẩy lên.

<img src=http://i.imgur.com/TNAzy5m.png>

Một cách khác nếu bạn không muốn thực hiện clone về máy như bước trên thì bạn có thể làm như sau:

- Tạo một repo mới trên github.com mà không tạo file README.md (giả sử ở đây là repo demo2)

- Tại máy local tạo một thư mục để chứa repo mới này. Ví dụ:

> mkdir /opt/demo2

> cd /opt/demo2

- Thực hiện tạo các file, thư mục như ý muốn. Sau đó thực hiện add, commit, push tương tự như trên
Nhưng ở đây cần thêm lệnh `git remote add origin $git-url` trước khi push. Tham khảo ví dụ sau:

> vi README.md

> git add README.md

> git commit README.md

hoặc `git commit README.md -m noi dung`

> git remote add origin git@github.com:ducnc92/demo2.git

> git push origin master

Sau đó nhập passphrase(nếu cần) hoặc username + password (nếu sử dụng SSH)

<a name="214pull"></a>
##### 2.1.4. Pull

Giả sử trên server github của bạn có những thay đổi mà máy local chưa cập nhật những thay đổi đó. Bạn thực hiện lệnh sau:

> cd cd /opt/demo1/

> git pull

<a name="22trenwindows"></a>
#### 2.2. Trên Windows

<a name="221taomotrepomoi"></a>
##### 2.2.1. Tạo một repo mới

Tạo repo trên github.com tự như mục 2.1.1.

Tạo repo bằng phần mềm Github

- Click vào dấu cộng, chọn tab Create, đặt tên và chọn đường dẫn cho repo mới

<img src=http://i.imgur.com/MXrpZZu.png>

- Tuy nhiên repo mới sinh ra mới chỉ có ở máy trạm, tại mục `Other`. Chọn chuột phải vào repo đó và chọn `Open in Explorer` để sửa nội dung của repo này.

<img src=http://i.imgur.com/v4Dkdiw.png>

- Sau khi chỉnh sửa xong, để đẩy repo đó lên github.com ta click vào `Publish this repository` và thực hiện như hình sau. Chú ý cần chọn Organization đặt repo này.

<img src=http://i.imgur.com/6kXeDfL.png>

<a name="222clone"></a>
##### 2.2.2. Clone

Click vào dấu cộng, chọn tab Clone, lựa chọn tổ chức mong muốn và chọn repo cần clone

<img src=http://i.imgur.com/YlrTOzQ.png>

Để chỉnh sửa nội dung của repo này ta chọn chuột phải vào nó và chọn `Open in Explorer`

<img src=http://i.imgur.com/Xx8JOR5.png>

Lúc đó chương trình Windows Explorer sẽ mở ra thư mục chứa repo của github, bạn có thể chỉnh sửa các file trong này, tạo xóa thư mục,... một cách bình thường.

<a name="223"></a>
##### 2.2.3. Add, commit, push, pull 

Trở lại với chương trình Github ta sẽ thấy dòng `uncommited changes` tại repo ta vừa sửa. Bạn hãy điền vào đó comment và ấn `commit to master`

<img src=http://i.imgur.com/NWX4RIM.png>

Lúc này sự thay đổi của bạn với mã nguồn đã được ghi lại trên máy local, để đồng bộ nó lên server github bạn hãy ấn vào biểu tượng `Sync` ở góc trên cùng bên phải.

Sau khi đồng bộ xong, quay trở lại repo trên trang github.com.

<img src=http://i.imgur.com/xFcnmsI.png>

Để đồng bộ những thay đổi trên github.com về máy local (pull) ta cũng click vào biểu tượng `Sync` như bên trên.


<a name="3"></a>
### 3. Thao tác với tổ chức trong Github

Để tạo một nhóm cho nhiều người cùng làm việc ta làm như sau:

- Truy cập URL: https://github.com/settings/organizations, chọn New Organizations

- Đặt tên và email cho tổ chức

<img src=http://i.imgur.com/IvHecWe.png>

Tại mục `Choose the organization’s plan` chọn Open Source để miễn phí, nhưng lúc này các Repo trong tổ chức sẽ là public.

- Mời các thành viên cho tổ chức

<img src=http://i.imgur.com/xV3Cukc.png>

Lúc này vào trang cá nhân của bạn sẽ thấy tại mục Organizations có tổ chức mới vừa tạo. Để cấu hình tổ chức này ta click thẳng vào nó.

<img src=http://ducnc.imgur.com/all/>

Ở đây tôi sẽ tạo một team mới như hình sau:

<img src=http://i.imgur.com/7kWLNYE.png>

<img src=http://i.imgur.com/zO3kvzZ.png>

Các member của team này có quyền write với các repo của team.

Với 3 mức: Read Access, Write Access, Admin Access Github cho phép chúng ta phân quyền tới các thành viên của nhóm.

Để mời một người dùng khác vào team, ta click vào team đó và search tên của người dùng cần tìm

<img src=http://i.imgur.com/Usep9GP.png>

Sau đó hệ thống sẽ yêu cầu bạn nhập password để xác thực, nếu thành công, một email xác nhận sẽ được gửi đến người được mời và người này sẽ xác nhận có tham gia vào tổ chức hay không.

Để tạo một repo cho tổ chức, ta chỉ cần click vào tổ chức đó, sau đó chọn `Create new Repostory`. Các hành động clone, add, commit,... làm như bình thường.

<a name="4"></a>
### 4. Thao tác với nhánh (branch)

```
Sẽ cập nhật và bổ sung sau
```

<a name="5"></a>
### 5. Issues


Giả sử bạn đang theo dõi repo của tôi và thấy có một số chỗ cần sửa đổi, bạn có thể comment ý kiến của mình vào Repo đó. Sau đó người quản trị sẽ xem xét, thay đổi và trả lời bạn.

Để làm việc này bạn cần vào repo đó, click vào `Issue`. Ví dụ như hình sau:

<img src=http://i.imgur.com/JGiXt76.png>

Sau đó chọn `New issue` (màu xanh) để tạo một issue mới.

<img src=http://i.imgur.com/RTh8QjV.png>

Lúc này tại Repo của người quản trị sẽ thấy một Issue mới, người quản trị có thể click vào Issue này để xem, sau đó xem xét sửa đổi, comment lại. Khi sửa đổi hoàn tất thì sẽ đóng issue đó lại.

<img src=http://i.imgur.com/j8ioZgA.png>

<img src=http://i.imgur.com/fJroMte.png>

Bằng cách tạo issue, bạn có thể đăng các câu hỏi, thắc mắc của mình cho chủ của repo đó.

<a name="Tongket"></a>
## Tổng kết 

Bài viết trên tôi tổng hợp lại những kiến thức thu được khi sử dụng git và github cho công việc của tôi (sys admin), hi vọng nó giúp các bạn một phần nào đó.

Chắc chắn bài viết còn có nhiều thiếu sót, mong các bạn thông cảm và gửi feedback cho tôi để hoàn thiện thêm.

Liên lạc của tôi:

- Email: nguyencongduc3112@gmail.com

- Skype: khong_giong_ai

Xin chân thành cảm ơn!
