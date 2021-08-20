---
layout: post
title:  "Giải Thích Khái Niệm Lập Trình Cơ Bản 1 - COMPUTER BASICS"
date:   2020-01-17 09:14:00 -0700
categories: cs-foundation
---

**Nếu bạn vừa đến với lập trình như tui, thì chắc hẳn bạn cũng đang bị chôn vùi trong đống thuật ngữ, khái niệm, quy tắc về lập trình ngoài kia.**

[Lộ trình tự học của tui][link-to-post-1] là lao thẳng vào những chủ đề/ứng dụng tui quan tâm (Python, Data Analysis), thay vì học đầy đủ nền tảng lý thuyết trước. Có 1 điểm trừ của cách học này là hay bị khớp ở những khái niệm lập trình cơ bản, đặc biệt lặp đi lặp lại trong các tài liệu tiếng anh. Thậm chí các tài liệu, blog lập trình tiếng việt cũng vẫn giữ nguyên từ gốc ... để giữ gìn sự trong sáng của tiếng lập trình.

Thời gian gần đây tui cặm cụi mài google, kiến thức đã dần tạo thành những mắt xích, nên tui tranh thủ làm chuỗi bài này nhằm mục đích chính là ráp lại các khải niệm căn bản cho bản thân. Nhân đây tui cũng viết lại theo cách đơn giản nhất và chia sẻ ở đây, mong có thể gãi ngứa cho các bạn cũng có lộ trình học lập trình tương tự. Ở đây tui sẽ:

- Giải thích nhẹ nhàng, tập trung vào việc giải thích định nghĩa để bạn bớt vướng mắc khi đọc tài liệu công nghệ (đi sâu quá, tui chưa đủ trình T-T).

- Ưu tiên sử dụng các thuật ngữ tiếng anh sau khi đã giải thích ở trước, hoặc tập trước. Vì vậy, có phần nào không hiểu thì bạn cứ lui về những tập trước nhé. 

- Dẫn link các bài viết hay, xịn cho các bạn nào muốn tìm hiểu sâu hơn, hen.

Ok, giờ mình đi thẳng vào **tập 1 - Máy tính nói chung**.

*****

### Computer Science - Khoa học máy tính

Đây là ngành nghiên cứu về công nghệ thông tin, phép toán, và ứng dụng trong các hệ thống máy tính. Nói đơn giản, **trong ngành khoa học máy tính, người ta nghiên cứu sử dụng máy tính để giải quyết nhiều vấn đề.**

### Computer Basics - Cơ bản về máy tính

**Máy tính (computer)** là chiếc máy có thể thực hiện những phép toán thông qua những **hướng dẫn/câu lệnh (instructions)** từ con người.

Một chiếc máy tính có 2 bộ phận chính:

- Hardware (phần cứng)
- Software (phần mềm)

**Hardware** là những thứ cứng - gọi là cứng vì bạn có thể sờ được, và cũng là vì nó "cứng nhắc", khó sửa. 
Còn **Software** thì không sờ được, nhưng tên là mềm vì dễ dàng cập nhật, thay đổi (chứ không phải tại thằng kia tên cứng?). 

**Program (chương trình máy tính)**, hay **Application (ứng dụng)** thuộc phần mềm, được viết bằng tập hợp những hướng dẫn.

Túm lại:

> **Con người viết hướng dẫn cho máy tính bằng ngôn ngữ lập trình, những hướng dẫn này tạo thành chương trình máy tính trong phần mềm, và được gửi đi cho phần cứng chạy.**

Những thuật ngữ thường được lặp lại, và có thể tạm hiểu đồng nghĩa như nhau:

> **Code = Instructions (hướng dẫn) = Program (chương trình) = App / Application (Ứng dụng) = Software (phần mềm)**

#### Hardware - Phần cứng

Nói kỹ hơn về phần cứng, phần này có 6 bộ phận:

<center><img src="{{ site.url }}/assets/post2/phan-cung-may-tinh.jpeg"></center>

- **The Central Processing Unit**, viết tắt **CPU (bộ xử lý trung tâm)** là bộ não của máy tính, cân hết các công việc chạy code, tính toán cho máy tính. Vì làm việc lớn nên thông thường **CPU** cũng có một số nô tì riêng là mấy chiếc quạt làm mát được lắp xung quanh nè. 

- **Main memory (bộ nhớ chính)**, hay là **RAM (Random Accessed Memories)** là kho chứa: 1) code của các chương trình và 2) dữ liệu được tạo ra khi chạy các chương trình đó. Ví dụ, khi bạn mở 1 chương trình - trình duyệt chrome lên chẳng hạn - thì RAM sẽ bị chiếm đóng cho đến khi bạn tắt trình duyệt đi. Những chương trình, dữ liệu không đang hoạt động thì nằm trong **secondary storage (bộ nhớ phụ)**. 

- **Input/Output devices (thiết bị đầu vào/ra)** cho phép con người tương tác, trao đổi dữ liệu với máy tính. Ví dụ như microphone, bàn phím là thiết bị đưa dữ liệu vào; còn tai nghe, loa, máy in là đưa ra; USB thì vào ra đều được.

- **Bus** là phương tiện chở dữ liệu qua lại trong máy tính. Ví dụ khi bạn mở chrome, thì bus sẽ chở code và dữ liệu từ bộ nhớ phụ đến bộ nhớ chính để khởi động chrome. 

- **Network (mạng máy tính)** là cầu nối để máy tính này kết nối với các máy tính khác, để bạn nhận email từ ai đó, hoặc để đọc cái blog này của tui đây.

### Languages - Ngôn ngữ của máy tính

Một chiếc máy tính luôn lưu loát 2 loại ngôn ngữ, là **machine language (ngôn ngữ máy)** và **programming language (ngôn ngữ lập trình)**.

**Ngôn ngữ máy**, hoặc **mã máy**, như là tiếng mẹ đẻ của máy tính, các bộ phận máy tính giao tiếp với nhau và thực hiện các hướng dẫn bằng ngôn ngữ này. Bạn còn nhớ cái trình duyệt chrome lúc nãy bạn mở không? Nếu nó còn đang chạy, thì dữ liệu của trình duyệt được lưu trong RAM dưới dạng ngôn ngữ máy này nè. **Mã máy** được viết dưới dạng các **dãy số nhị phân (Binary)**.

<center><img src="{{ site.url }}/assets/post2/computer-languages.png"></center>

Nhị là 2, phân là phần. **Binary (hệ nhị phân)** là ngôn ngữ chỉ dùng hai ký tự 0 và 1; khác với **Decimal (hệ thập phân)** mà con người thường sử dụng để đếm từ 1 đến 10.

Tất cả các ký tự trên bàn phím đều có thể được dịch ra Binary hết. Quy trình dịch ngắn gọn là:

> **Character (ký tự) -> Decimal (Hệ thập phân) -> Binary (Hệ nhị phân)**

Bạn có thể tham khảo [bảng quy đổi - ASCII Table][ascii-table-link].

**Programming language (ngôn ngữ lập trình)** ngày nay là ngôn ngữ giao tiếp giữa máy tính và con người. Con người viết phần mềm bằng **ngôn ngữ lập trình** đưa vào máy, máy dịch ra thành **mã máy**, sau đó lưu và chạy bằng phần cứng.

Cũng như ngôn ngữ con người thì code cũng có văn phạm, chính tả, quy tắc - gọi chung là **syntax (cú pháp)**. Hồi lớp 1, cô đọc chính tả mà bạn viết thiếu dấu câu, thì sẽ bị trừ điểm. Còn viết code mà thiếu dấu câu - là 1 lỗi sai syntax, thì code sẽ không chạy được. 

*Plot twist xíu*. Thực ra mã máy là ngôn ngữ lập trình đầu tiên. Còn ngôn ngữ lập trình (tui nói trên) là một tập con của mã máy. Ngôn ngữ lập trình ngày nay được phát triển để gần với tiếng người hơn, để nhiều người có thể học và nghiên cứu máy tính hơn. 


*****

Như trên là sơ bộ những kiến thức tất yếu về máy tính nói chung. Nếu tui có sai sót chỗ nào xin được nhận ý kiến và chỉ bảo thêm ạ.

Đang có đà nói về **ngôn ngữ lập trình**, nên tập sau tui sẽ viết về chủ đề này nhé. Mời các bạn đón xem.

[link-to-post-1]: https://tuihoccode.com/thoughts/2020/01/16/chia-se-kinh-nghiem-tu-hoc-lap-trinh-python-cho-nguoi-moi-bat-dau.html
[ascii-table-link]: https://www.cs.cmu.edu/~pattis/15-1XX/common/handouts/ascii.html
