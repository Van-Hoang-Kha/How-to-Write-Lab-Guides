# **Cách viết một Lab Guide**

## **I. Phần 1: Chuẩn bị**
 1. **Tải Hugo Theme** 
 - Lab guide sử dụng [**Theme Hugo**](https://gohugo.io/) có thể được cài đặt trên nhiều nền tảng tại [đây](https://gohugo.io/getting-started/installing/) , chỉ cần gõ **```hugo version```** trong **Terminal/CMD/PowerShell** chạy được là được.
 
 2. **Tải IDE**
 - [Visual Studio Code](https://code.visualstudio.com/download) 
 - Hoặc bất cứ IDE nào mà bạn thích.
 - **Một IDE** nào đó có các plug-ins hỗ trợ các loại ngôn ngữ cho thuận tiện trong việc viết: Visual Studio Code, Atom, Notepad++,... (Người viết guide này đang xài Visual Studio Code).
 - **Các plug-ins theo IDE**: Nghiễm nhiên sẽ cần plug-ins dành cho Markdown (như **Markdown All in One**, **Markdown TOC**,...). Mỗi khi viết 1 file ngôn ngữ gì thì VS Code cũng gợi ý cài cái plug-ins liên quan nên không phải lo lắng
 
 3. **Tải Snagit 2019**
 
 4. [Tải Active Presenter](https://atomisystems.com/download/)
 
 5. **Tải Draw.io**
 - Có thế tải về máy [tại đây](https://www.diagrams.net/) 
 - Hoặc có thể vẽ trên [web](https://www.diagrams.net/)
 - Tải bộ icon mởi nhất của AWS [tại đây](https://aws.amazon.com/vi/architecture/icons/)

 **Lưu ý:** Vẽ diagrams theo đúng format và style của sư phụ Gia Hưng.

## II. **Phần 2: Nội dung**

## 1. Cấu trúc file

#### **Thư mục *content***
	
Chúng ta tạm quy ước với nhau là sẽ tổ chức bài Lab với 2 cấp độ là tối đa (VD: **2. -> 2.1.** tương ứng với **2.write-content -> 2.1-Directory structure**)
	
Trong mỗi thư mục sẽ bao gồm:
- Các thư mục thứ cấp.
- Tập tin **_index.md** : Chứa nội dung tiếng Anh.
- Tập tin **_index.vi.md** : Chứa nội dung tiếng Việt.
	

*Nếu chỉ đang viết guide tiếng Việt thôi thì sẽ copy **_index.vi.md** ra một bản nữa và đổi tên thành **_index.md** nhá. (Để dịch sau)*


	
#### **Thư mục *static/images***
	
Đây sẽ là thư mục chứa ảnh cho Lab Guide. Mọi ảnh đều được bỏ vào trong đây. Có thể phân cấp thư mục cho các ảnh để dễ quản lý ảnh.
	
Các ảnh này sẽ được sử dụng trong bài viết bằng thẻ gán ảnh:
	
```md
![Đây là tên ảnh (Hiển thị khi không load được ảnh)](/images/2.1/SNAG001.png?width=90pc)
```
- Sử dụng ?width=90pc với các ảnh toàn màn hình và ?width=40pc hoặc ?width=50pc đối với các ảnh crop.
	


#### **Thư mục *public***
	
*Đây là thư mục sẽ được tạo ra bởi hugo.*
	
Sau khi viết hoàn chỉnh guide hoặc một phần guide mà muốn kiểm tra hiển thị thì có thể chạy lệnh sau để build project
	
```bash
$ hugo
```
	
Sau khi build hoàn thành thì sẽ có thư mục public xuất hiện. Tiến hành chạy server để xem thành quả tại [http://localhost:1313](http://localhost:1313)
	
```bash
$ hugo server
```
	
*Tới đây rồi thì hãy thử xóa thư mục public và chạy thử xem Guide này có hoạt động được không nhá.*

## 2. Nội dung

1. **Thực hiện bài Hand-on Lab một lần** để nắm các bước cần phải làm. (Ghi chú lại những bước lỗi do thiếu (có thể là IAM Role, Permissions,...))
2. **Lên cấu trúc** cho Lab Guide (phân theo từng bước). Đây (có thể) cũng chính là cấu trúc thư mục của bài thực hành.
3. **Clean up** và **thực hiện lại** bài Lab lần thứ 2. Lần này quay phim lại (có thể sử dụng **Active Presenter**) hoặc screenshot từng bước và đánh số thứ tự hình ảnh (có thể dùng **SnagIt**)
4. Viết phần nội dung text cho Lab Guide. (Để sẵn các placeholder cho hình ảnh)
5. Nếu quay phim thì trích xuất hình ảnh từ video ra (có thể sử dụng **VLC Player** có mục **Screenshot**) và đặt hình ảnh vào những vị trí đã xác định.
6. Crop hình ảnh **loại bỏ** đi khung viền của browser (Nếu sử dụng SnagIt thì **xác định vùng chụp cố định** bỏ đi khung viền browser)
7. **Kiểm tra** và **format** lại nội dung với các [Notice](https://learn.netlify.app/en/shortcodes/notice/), bổ sung các [Tập tin đính kèm](https://learn.netlify.app/en/shortcodes/attachments/) (nếu có)

____

#### **Phần tiêu đề**
	
Ở đầu mỗi trang đều có phần header này để hiển thị **tiêu đề** và xác định điều hướng ở bên **Navigation panel bên trái trang**.
	
- ```title = "Viết nội dung"```: Để nội dung ngắn gọn súc tích để vừa 1 dòng ở bên **Navigation panel bên trái**.
- ```chapter = false``` : Để mặc định là false. Title ở trên cũng sẽ hiển thị là h1 ở trong bài viết.
- ```pre = "<b>2. </b>"``` : Đây là đánh số cho trang hiển thị ở **Navigation panel bên trái**.
	
```
+++
title = "Viết nội dung"
date = 2020
weight = 2
chapter = false
pre = "<b>2. </b>"
+++

```
	
#### **Phần heading**
	
Chúng ta sẽ thống nhất việc dùng tiêu đề cho các section trong 1 trang sẽ sử dụng h4 (####).
	
Ví dụ chính là heading của phần này.
	
#### **Phần Table of Contents (TOC)**
	
Sau khi viết xong nội dung (hoặc liệt kê xong các Heading của 1 trang), chúng ta có thể xây dựng **Table of Contents (TOC)** tự động bằng plug-in.
	
Sử dụng tổ hợp phím ```Ctrl + Shift + P``` sau đó gõ vào **Create Table of Contents** rồi chọn lựa chọn của plug-in **Markdown All in One**. Enter.
	
Chúng ta sẽ có một cái TOC như sau:
	
```text
Nội dung:
- [**Cách viết một Lab Guide**](#cách-viết-một-lab-guide)
	- [**I. Phần 1: Chuẩn bị**](#i-phần-1-chuẩn-bị)
	- [II. **Phần 2: Nội dung**](#ii-phần-2-nội-dung)
	- [1. Cấu trúc file](#1-cấu-trúc-file)
			- [**Thư mục *content***](#thư-mục-content)
			- [**Thư mục *static/images***](#thư-mục-staticimages)
			- [**Thư mục *public***](#thư-mục-public)
	- [2. Nội dung](#2-nội-dung)
			- [**Phần tiêu đề**](#phần-tiêu-đề)
			- [**Phần heading**](#phần-heading)
			- [**Phần Table of Contents (TOC)**](#phần-table-of-contents-toc)
			- [**Phần ghi chú**](#phần-ghi-chú)
			- [**Phần tập tin đính kèm**](#phần-tập-tin-đính-kèm)
			- [**Phần vẽ bảng**](#phần-vẽ-bảng)
			- [**Phần hình ảnh**](#phần-hình-ảnh)
		- [**Update config.toml**](#update-configtoml)
- [Cre: Sư Huynh Minh Lê, Sư Huynh Thanh Hiệp](#cre-sư-huynh-minh-lê-sư-huynh-thanh-hiệp)

```
	
#### **Phần ghi chú**
	
Trong bài viết có thể sẽ có các đoạn cần làm nổi bật lên như Ghi chú, Cảnh báo,... thì sẽ dùng shortcode theo hướng dẫn tại [đây](https://learn.netlify.app/en/shortcodes/notice/)
	
{{% notice note %}}
Đây là Note
{{% /notice %}}
	
{{% notice info %}}
Đây là Info
{{% /notice %}}
	
{{% notice tip %}}
Đây là Tip
{{% /notice %}}
	
{{% notice warning %}}
Đây là Warning
{{% /notice %}}

#### **Phần tập tin đính kèm**
	
Phần này sẽ thực hiện theo hướng dẫn tại [đây](https://learn.netlify.app/en/shortcodes/attachments/)
	
**Vị trí đặt tập tin sẽ là trong thư mục tương ứng với tên trang md.**
	
VD: 
- **_index.md** ---> **_index.files**
- **_index.vi.md** ---> **_index.vi.files**
	

*Nghĩa là nếu có nhiều ngôn ngữ thì mỗi ngôn ngữ 1 thư mục như vậy cho 1 trang.*

	
	
**Sử dụng shortcode sau để tạo phần đính kèm:**
	
- **title** : Tiêu đề phần đính kèm
- **pattern** : Xác định các tập tin được hiện ra trong box (có thể để tên tập tin hoặc pattern để xác định theo đuôi)
	
Ví dụ lọc tập tin Dockerfile:
	
```
{{%/*<attachments title="Dockerfile" pattern="Dockerfile"/*/%}}
```
	
Sẽ được như vầy:
	
{{%attachments title="Dockerfile" pattern="Dockerfile"/%}}
	
Ví dụ lọc tập tin theo đuôi:
	
```
{{%/*attachments title="Build Scripts" pattern=".*(ps1|sh)"/*/%}}
```
	
Sẽ được như vầy:
	
{{%attachments title="Build Scripts" pattern=".*(ps1|sh)"/%}}
	
#### **Phần vẽ bảng**
	
Để đơn giản hóa việc vẽ bảng, người viết thường sử dụng công cụ [Tables Generator](https://www.tablesgenerator.com/markdown_tables)
	
1. Truy cập tới trang.
2. Nhập nội dung xong bấm **Generate** rồi **Copy to clipboard**.
3. Xong vô đây **Paste** vào thôi.
	
#### **Phần hình ảnh**
	
1. **Phần mềm chụp màn hình khuyên dùng:** SnagIt (2019/2020)
	
2. **Thiết kế hình ảnh:**
	
Để tạo sự đồng nhất và dễ hiểu cho người xem, chúng ta định hình ra một chuẩn chung như sau:
	
 - Về Screenshot Console: 
 - **Trình duyệt:** Chrome tắt Bookmark bar (khuyên dùng)
 - **Zoom:** Mặc định không zoom in (100%)
 - **Độ phân giải màn hình:** FullHD (1920 x 1080)
 - **Định dạng:** PNG (Khuyên dùng)
 - Về Font chữ ghi trên hình:
 - **Font:** Arial Black
 - **Size:** 18
 - **Không** bật Shadow.
- Về Khung đánh dấu khu vực cần chú ý:
  - **Màu:** Trùng với màu chữ ghi chú
  - **Độ dày (Thickness):** 1 px
  - **Độ mờ (Opacity):** 100%
	
### **Update config.toml**

```conf
[Languages.en]
title = "How to Write a Lab Guide"
weight = 1
languageName = "English"
	
[Languages.vi]
title = "Cách viết một Lab Guide"
weight = 2
languageName = "Tiếng Việt"
```

# Cre: Sư Huynh Minh Lê, Sư Huynh Thanh Hiệp
