---
layout: post
title:  "Discrete Math Là Gì? Tại Sao Học Computer Science Phải Học Discrete Math?"
date:   2020-03-02 17:05:23 -0700
categories: cs-foundation
---

**Trả lời các câu hỏi như tựa đề.**

Lang thang trên trên các chương trình giảng dạy Computer Science, từ đại học đến thạc sỹ và các chương trình bootcamp đều mở đầu với bộ môn Discrete Math. Rốt cục bộ môn này là gì và nó quan trọng tới mức nào. Bài viết này tui sẽ trả lời các câu hỏi dưới đây nhé. 

1. **Discrete Math là gì?**
2. **Tại sao học CS lại phải học Discrete Math?**

### __1. Discrete Math là gì?__

Hãy thật lòng trả lời tui: bạn còn nhớ toán cấp cấp ba và những khái niệm đại số như vi tích phân, số thập phân, đồ thị và hàm số f(x) hay hình học cùng sin, cos không? Nếu bạn không còn nhớ gì (mấy) như tui thì chúc mừng bạn vì bạn không cần vững những nền tảng trên để bắt đầu học Discrete Math.

Đa phần kiến thức toán mình đã học thời phổ thông đều thuộc dạng toán **Continuous (toán liền mạch / hàm liên tục)**. Ngược với Continuous, **Discrete math (toán rời rạc)** tập trung vào đặc điểm **rời rạc**. (Ủa?)

Dưới đây tui lấy 2 ví dụ để hiểu và phân biệt giữa Continuous và Discrete như sau: 

**Ví dụ 1:  Tập hợp số thực vs. Tập hợp số nguyên**

Mình cùng ôn tập một xíu nhé.

<center><img src="{{ site.url }}/assets/discrete-math/continuous-vs-discrete-math.jpg"></center>

Trong toán đại số, **R** là tập hợp số thực như: 0, 0.1, 0.11, 0.111, .... và các số vô tỉ (như √2 = 1.41421356...), số siêu việt (như π = 3.14159265...). Vẽ số thực trên 1 cây trục như trên sẽ thấy khoảng cách giữa số 0 đến số 1 là vô hạn, cũng như từ 0 đến 0.1 hay từ 0 đến 0.001. Không ai có thể đếm được có bao nhiêu điểm từ một số này qua số kia. Đây chính là khái niệm **Continuous (liên tục)**.

Ngược lại, ở tập hợp Z số nguyên (…–3,–2,–1,0,1,2,3…), các số đều được tách rời nhau và có khoảng cách nhất định. Sau số 1 là số 2, ở giữa 2 số này không còn ai hết. Đây chính là khái niệm **Discrete (rời rạc)**.

Giờ mình lấy thêm 1 ví dụ đời thường giữa toán Continuous và Discrete để bạn dễ mường tượng ra được tính rời rạc và tính liên tục trong thực tế

**VD2: Đồng hồ kim vs. Đồng hồ điện tử.**

<center><img src="{{ site.url }}/assets/discrete-math/continuous-vs-discrete-math-2.jpg"></center>

Đồng hồ kim thuộc khái niệm Continuous do có thời gian trải dài và liền mạch trên mặt đồng hồ. Ngược lại, đồng hồ điện tử thuộc khái niệm Discrete do thời gian nhảy theo phút, sau 12 giờ 45 sẽ là 12 giờ 46.

Note nhẹ, **Discrete Math** không phải là 1 nhánh của toán học, như các nhánh: đại số, hình học, vi tích phân đâu nhé. Đây chỉ là tên gọi chung của đặc điểm **rời rạc** trong các nhánh của toán học.

Khi nói đến 2 dòng toán **Discrete** và **Continuous**, tui tổng hợp những tính từ hay được dùng dưới đây để phân biệt:

<center><img src="{{ site.url }}/assets/discrete-math/discrete-math-la-gi.jpg"></center>

Discrete Math nghe có vẻ đơn giản hơn là toán phổ thông nữa. Vậy...

### __2. Tại sao học CS lại phải học Discrete Math?__

Tất cả đều nằm ở mấu chốt: **đặc điểm vận hành của máy tính là rời rạc**.

Trong [bài viết giải thích về căn bản máy tính][link-to-computer-basics], tui có giải thích về Binary (mã nhị phân). Ngôn ngữ mẹ đẻ của máy tính là Binary. Tất cả các dữ liệu của máy tính đều được lưu dưới dạng Binary, chỉ gồm 2 ký tự duy nhất là 0 và 1. Vì binary là nền tảng để xây xựng tất tất tật liên quan đến phần mềm, do đó mà mọi thứ của máy tính đều mang trên mình khái niệm Discrete.

Chẳng hạn như cái hệ điều hành tui đang dùng có 64-bit. Ngoài 64-bit thì còn có 32-bit, 8-bit không có cái máy nào chơi 64.5-bit cả.

Một yếu tố quan trọng trong Computer Science phải kể đến đó là môn Algorithms (thuật toán) cũng được xây dựng trên nền tảng Discrete. 
> Thuật toán là một bộ các bước hữu hạn chứa các quy tắc hay quy trình cụ thể nhằm giải quyết một vấn đề nào đó. Nếu không có Algorithms và Discrete thì tui xin R.I.P cái máy tính vì chương trình đó sẽ chạy mãi không ngừng. 

<center><img src="{{ site.url }}/assets/discrete-math/tai-sao-phai-hoc-discrete-math.jpg"></center>

Vậy đó, Discrete Math được mệnh danh là toán học dành cho máy tính, và nếu bạn muốn làm trùm Computer Science thì phải học Discrete Math. 

Khái niệm toán Discrete chỉ mới nổi lên cách đây vài chục năm cùng với sự trỗi dậy của khoa học máy tính. Do đó mà môn này chỉ được giảng dạy rộng rãi tại các chương trình giảng dạy Computer Science, chủ yếu ở bậc đại học và thạc sỹ chứ chưa được phổ biến dạy ở các bậc phổ thông trung học, dù nó cũng khá thực tiễn trong đời sống hằng ngày (tui thấy vậy).

Vậy **Discrete Math dạy những gì? Và học Discrete Math online ở đâu?** Mời các bạn đón xem ở [tập tiếp theo][discrete-math-day-nhung-gi]. 


[link-to-computer-basics]: https://tuihoccode.com/cs-foundation/2020/01/17/giai-thich-khai-niem-lap-trinh-co-ban-1-computer-basics.html
[discrete-math-day-nhung-gi]: https://tuihoccode.com/cs-foundation/2020/03/07/discrete-math-la-gi-2.html
