---
layout: post
title:  "Tour tham quan nhà máy biên dịch code  Compiler"
date:   2021-08-01 19:35:00 -0700
categories: cs-foundation
---

**Viết được 1 đoạn code lởm, nhưng thôi cũng thử bấm nút compile, thế là ra được 1 cái file .exe. Hít hà lấy hơi mạnh dạn double click lên chiếc file .exe, nít thở chờ đợi, ai ngờ nó chạy thật. Ngẩn ngơ tò te tui tự hỏi, code viết dở hơi thế kia mà làm sao vẫn chạy được?

Tui đi hỏi bụt (google), lật mấy trang sách, để hiểu hơn sự kỳ diệu của những chương trình biên dịch code - compiler.**

<center><img src="{{ site.url }}/assets/compiler-tour/compiler-hoat-dong-nhu-the-nao.png"></center>

Compiler - tui gọi là nhà máy biên dịch code, thật ra là 1 chương trình software đồ sộ và hoàn chỉnh. Code mình viết ngày nay C, C++, Rust, Java, Python,... đều thuộc nhóm ngôn ngữ lập trình bậc cao - người hiểu nhưng máy không hiểu. Do đó, code viết xong được gửi vào nhà máy biên dịch để được chuyển đổi.

Nhà máy biên dịch có nhiều khâu: cắt xén, thêm thắt, chỉnh sửa, chuyển đổi, để rồi cuối cùng đóng gói để tạo ra thành phẩm là mã máy, để máy tính có thể xử lý và chạy theo.

Phân biệt một chút giữa trình biên dịch Compiler và trình phiên dịch Interpreter:

	* Những ngôn ngữ như C, C++, Java, Rust và đa phần những ngôn ngữ khó nuốt là Compiled languages (ngôn ngữ biên dịch). Code viết xong rồi mới được gửi vào nhà máy cho xử lý. Xử lý xong thì đến nhận file để tự chạy ra kết quả.
	* Ngoài ra, mình còn có Interpreted languages như Python, JavaScript, Pearl vân vân. Code viết trong nhà máy, đang viết giữa chừng muốn test chạy thì có sẵn giám thị kiểm tra và sửa lỗi.

	* Đọc thêm về [Compiled Languages vs Interpreted Languages][compiled-languages-vs-interpreted-languages].

<center><img src="{{ site.url }}/assets/compiler-tour/compiler-hoat-dong-nhu-the-nao.png"></center>

[compiled-languages-vs-interpreted-languages]: https://www.geeksforgeeks.org/difference-between-compiled-and-interpreted-language/
