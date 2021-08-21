---
layout: post
title:  "Tour tham quan mhà máy Biên dịch Code - Compiler"
date:   2021-08-01 19:35:00 -0700
categories: cs-foundation
---

**Viết được 1 đoạn code lởm, nhưng thôi cũng thử bấm nút compile, thế là ra được 1 cái file .exe. Hít hà lấy hơi mạnh dạn double click lên chiếc file .exe, nít thở chờ đợi, ai ngờ nó chạy thật. Ngẩn ngơ tò te tui tự hỏi, code viết dở hơi thế kia mà làm sao vẫn chạy được?**

**Tui đi hỏi bụt (google), lật mấy trang sách, để hiểu hơn sự kỳ diệu của những chương trình biên dịch code - compiler.**

<center><img src="{{ site.url }}/assets/compiler-tour/compiler-hoat-dong-nhu-the-nao.png"></center>

**Compiler** - tui gọi là nhà máy biên dịch code, thật ra là 1 chương trình software đồ sộ và hoàn chỉnh. Code mình viết ngày nay C, C++, Rust, Java, Python,... đều thuộc nhóm ngôn ngữ lập trình bậc cao - người hiểu nhưng máy không hiểu. Do đó, code viết xong được gửi vào nhà máy biên dịch để được chuyển đổi.

Nhà máy biên dịch có nhiều khâu: cắt xén, thêm thắt, chỉnh sửa, chuyển đổi, để rồi cuối cùng đóng gói để tạo ra thành phẩm là mã máy, để máy tính có thể xử lý và chạy theo.

Phân biệt một chút giữa **trình biên dịch Compiler** và **trình phiên dịch Interpreter**:

* **Compiled languages (ngôn ngữ biên dịch)**: Những ngôn ngữ như C, C++, Java, Rust và đa phần những ngôn ngữ khó nuốt là Compiled languages. Code viết xong rồi mới được gửi vào nhà máy cho xử lý. Xử lý xong thì đến nhận file để tự chạy ra kết quả.
* **Interpreted languages (ngôn ngữ phiên dịch)**: Ngoài ra, mình còn có Interpreted languages như Python, JavaScript, Pearl vân vân. Code viết trong nhà máy, đang viết giữa chừng muốn test chạy thì có sẵn giám thị kiểm tra và sửa lỗi.
* Đọc thêm về [Compiled Languages vs Interpreted Languages][compiled-languages-vs-interpreted-languages].

<center><img src="{{ site.url }}/assets/compiler-tour/interpreting-vs-compiling.jpg"></center>

Bây giờ mình làm một tour ngắn tham quan nhà máy Compiler nhé?

### __Khâu 1: Preprocessing__

Source code viết xong đầu tiên sẽ được gửi đến **khâu tiền xử lý**.

<center><img src="{{ site.url }}/assets/compiler-tour/compiler-hoat-dong-nhu-the-nao-preprocessing.png"></center>

Vào đây, code nào có documentation hay comment sẽ được lược bỏ hết. Máy tính tụi nó nào có quan tâm.

Tiếp, mở rộng **header files**.

&nbsp;&nbsp;&nbsp;&nbsp;Header files: Thông thường code trong một file sẽ tận dụng những chương trình đã được viết sẵn ở những file khác, và khai báo ngay trên đầu file trước khi viết code nên được gọi là header files. Syntax phổ biến của header files như là

  * `#include<stdio.h>` trong C
  * `use std::collections` trong Rust

&nbsp;&nbsp;&nbsp;&nbsp;Xử lý header files, các bạn công nhân sẽ dựa trên tên header files được khai báo để đi tìm file gốc, sau đó copy code gốc và dán vào cái source code cần chạy.

Tiếp, mở rộng **macro**.

&nbsp;&nbsp;&nbsp;&nbsp;Macro là một dạng viết code động - code tạo ra code. Macro code sau khi được mở rộng sẽ tạo ra 1 nhóm code tương thích với các dòng khác trong source code. C, Rust là những ngôn ngữ điển hình có hỗ trợ macro.

  * `#define`, `__FILE_NAME__` là những macro điển hình trong C
  * `#derive`, `println!`, `vec!` trong Rust

Tóm lại, khâu tiền xử lý cắt bỏ những phần máy tính không cần sử dụng, và mở rộng những phần viết tắt để sẵn sàng cho quy trình xử lý.

### __Khâu 2: Compilation__

Compilation hay biên dịch là khâu căng nhất và đồ sộ nhất trong bộ máy.  

Khâu này nhận xử lý những vật liệu thô sơ - là source code vừa được sơ chế ở trên - và sản xuất ra các bán thành phẩm là những file chứa assembly code.

<center><img src="{{ site.url }}/assets/compiler-tour/compiler-hoat-dong-nhu-the-nao-compilation.png"></center>

Các phòng ban và sứ mệnh của từng phòng như sau:

* **Analysis** - phân tích xem chính tả, syntax, khai báo kiểu dữ liệu, và logic của code xem có đúng với quy định của ngôn ngữ lập trình không. Đồng thời, tokenizer (máy tách từ) sẽ cắt code thành các token (thẻ dữ liệu) và xếp vào loại bảng, hộp chứa thông tin phù hợp.

* **Parsing** - rà soát dữ liệu cho từ các bảng chứa thông tin trên (symbol table), và vẽ lên các biểu đồ (abstract syntax tree) dựa trên logic của chương trình. Sau bước này, những trang code mình viết không còn nữa mà thay vào đó là các loại table và graph chứa thông tin cần thiết.

* **Optimize** - đến đây, nhà máy kiểm tra lại lần nữa để cắt bỏ những chỗ không cần thiết và rút gọn dữ liệu để chuẩn bị cho công đoạn biến hình.

* **Code generation** - vận dụng thông tin ở các bảng và biểu đồ để biến code thành assembly code.

Thành phẩm của khâu compilation là tạo ra chương trình dưới dạng **assembly language**. Tui gọi là bán thành phẩm vì assembly language cũng thuộc dạng ngôn ngữ bậc thấp, chưa hoàn thành nhưng cũng gần tới mã máy binary code lắm rồi!

Mỗi công đoạn kể ra cũng đều là 1 phần mềm phức tạp bao gồm các phần mềm khác - 1 bộ phận quản lý nhiều phòng ban. Có dịp tui lại làm tour đi tham quan các phòng ban này sau.

### __Khâu 3: Assembly__

Khâu lắp ráp nhận chương trình đã được compiled và chuyển thành machine code là mã máy - yay! 

<center><img src="{{ site.url }}/assets/compiler-tour/compiler-hoat-dong-nhu-the-nao-assembly.png"></center>

Sau khi lắp ráp xong, khâu Assembly sẽ cho ra kết quả là file chứa ngôn ngữ máy, trong C đây là những gile .o, chương trình nào dài thì sẽ ra nhiều file.

Ngoài ra, mỗi kiến trúc CPU khác nhau đều yêu cầu machine code khác nhau. Do đó, nếu chương trình có nhiều target machine, sẽ được nhận thêm các tệp binary cho từng loại machine. 

### __Khâu cuối: Link & Load__

<center><img src="{{ site.url }}/assets/compiler-tour/compiler-hoat-dong-nhu-the-nao-link-load.png"></center>

Khâu hàn gắn :v. 

Ở khâu này, các linker sẽ tiếp nhận các file mã máy và giải quyết các vấn đề liên quan đến bộ nhớ ngoài. Cụ thể là những chương trình tận dụng code ở những chương trình khác thì nên tìm và đặt ở đâu.

Xong xuôi, loader xuất hiện và gắn các cục .o thành 1 cục .exe, sẵn sàng để chạy.

Phù, thế là xong 1 vòng nhà máy. Dưới đây là sơ đồ chung của nhà máy để nhìn toàn diện nha.

<center><img src="{{ site.url }}/assets/compiler-tour/compiler-hoat-dong-nhu-the-nao-overall.png"></center>

[compiled-languages-vs-interpreted-languages]: https://www.geeksforgeeks.org/difference-between-compiled-and-interpreted-language/
