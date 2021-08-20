---
layout: post
title:  "Chia Sẻ Kinh Nghiệm Tự Học Lập Trình Python Cho Người Mới Bắt Đầu"
date:   2020-01-16 10:43:23 -0700
categories: thoughts
---
**6 tháng trước tui bỏ việc để học lập trình. Từng lạc lối giữa nguồn kiến thức bao la, giờ có ít lông ít cánh nên xin mạo muội chia sẻ một số kinh nghiệm mà giá như tui biết từ đầu.**

Tui là dân marketing, không có căn bản lập trình. Những gì tui biết là sửa và copy code SQL để xuất số liệu và... cũng là sửa và copy code HTML để làm landing page. Nghỉ làm học lập trình, tui đặt đích đến là học sâu hơn về phân tích dữ liệu, nạp căn bản để được ngồi chung với mấy anh dev chém gió.. à không thảo luận về việc phát triển sản phẩm. 

Vẽ mục đích ra là vậy, nhưng đến khi thực sự bắt đầu thì lập tức choáng vì kiến thức ngoài kia là cả một bầu trời. Trên mạng có rất nhiều tài liệu hay, nhưng quá nhiều đi và lại còn rời rạc. Sau 6 tháng thử cái này, theo cái kia, tui cũng ráp được 1 lộ trình tạm ổn cho bản thân. Tui viết để đây để sau này track được lộ trình học, đồng thời cũng mong đỡ được các bạn mới bắt đầu như tui đỡ loay hoay trong những ngày đầu. 


### Xác định sở thích/mục đích để chọn ngôn ngữ và chương trình học ban đầu. 

Bước này vô cùng quan trọng, đây không phải là bước ngoặt, nhưng là bước quyết định sau này bạn có ngoặt được không. Ai có bỏ cuộc thì dễ sẽ bỏ tại đây. Vậy nên mới cần chọn cái mà mình có hứng thú, hoặc liên quan và hữu ích cho những kỹ năng mình đang có để cảm thấy được tính áp dụng của việc học. 

Trong các ngôn ngữ phổ biến cho người mới bắt đầu tui chọn học Python. Thứ tự học của tui như dưới đây:

- **Website [https://pythonprogramming.net/][https://pythonprogramming.net/] của anh Harrison**: Tui mở màn với khoá [Python Fundamentals][python-fundamentials], sau đó là [Data Analysis][data-analysis], thời gian học tầm 1 tháng. Quan điểm chia sẻ kiến thức của anh Harrison là dạy cho bạn hiểu và biết làm ra 1 ứng dụng đơn giản, để bạn thấy được việc học của mình là thực tế. Trong quá trình học bạn sẽ hơi lấn cấn ở một số lý thuyết căn bản, nhưng không khó để có thể tự dò ra. Học xong tui nắm được các hàm và logic Python căn bản, hiểu và sử dụng được thư viện Pandas. Anh Harrison thực tế, vui tính theo kiểu thông minh, cách tiếp cận kiến thức và vấn đề rất thẳng và dễ hiểu. Không có anh Harrison thì đời học code và cái blog này của tui không biết đã trôi nổi về đâu.

- **[Chương trình Applied Data Science (của University of Michigan)][michigan-data-science-course]** Học miễn phí với chế độ Audit, hoặc trả tiền để lấy bằng. Khoá học được gắn mác Intermediate, tui theo sau khi đã được anh Harrison rèn cho tí căn bản rồi. Thời gian học hết 1 khoá là 3 tháng (nếu bạn chăm). Nội dung học áp dụng trên chủ đề thực tế như thể thao, kinh tế, thời tiết, ... sử dụng cái số liệu trên wikipedia, hoặc từ các trang số liệu của chính phủ. Điểm tui vừa thích (mà cũng vừa ngán) là bài tập và bài thi trời ơi khó. Nội dung bài tập chắc tầm 150% - 200% nội dung học, đòi hỏi tui phải tự tìm tòi thêm, và tự rèn cách giải quyết vấn đề. Sau khi học, tui thành thạo hơn pandas và numpy, biết sơ về scikit learn, và có thể làm osin đi clean dữ liệu :)). Ngoài ra cũng bồi bổ thêm 1 số kiến thức về thống kê.


### Nạp kiến thức nền tảng để vững căn bản

Sau khi nhập môn xong thì lúc này đầu tui lùng bùng 1 mớ khái niệm và thuật ngữ căn bản, nhắc đến *“à hình như tui hơi hiểu”* nhưng  bảo giải thích thì chỉ biết gãi đầu. Nếu bạn cũng như tui, thì đây là lúc đi nạp căn bản. Các nội dung học dưới đây áp dụng chung cho những ai muốn học lập trình. Bước này giúp tui vỡ lẽ ra được những thứ gần như là học vẹt khi nhập môn. Lắm lúc còn vỗ đùi rồi hoan hô vì các mắt xích đang dần nối lại với nhau :-j. 

- **[Khoá Mathematics for Computer Science của MIT][mit-math-course-youtube] trên youtube**: Đây là khoá học kinh điển về toán cho lập trình, tui lân la đủ các diễn đàn đều được các tiền bối xịn đề cử học. Nội dung của khoá tập trung dạy Discrete Math (toán học rời rạc) và một số kiến thức toán nền tảng cho lập trình nói chung. Quả như lời đồn, học rất hay, vui và cuốn hút. Thời gian học là 2 tháng (again nếu bạn chăm) cho việc học và giải bài tập. [Website của khoá học][mit-math-course-website] hỗ trợ đầy đủ tài liệu như cho sinh viên MIT khoá luôn, toàn bộ giáo trình, bài luyện tập và bài thi có thể tải về miễn phí. Tui mê thầy Tom lắm, lúc xưa là giảng viên MIT, giờ là CEO của [Akamai][akamai-website] - một công ty công nghệ lớn với hơn 6000 nhân viên.

- **[Video Data Structures của freeCodeCamp][freeCodeCamp-data-structure-course]**: Học về cấu trúc dữ liệu với thời gian học là 8 tiếng. Nếu bạn đã hoàn thành các khoá học trên thì đây là 1 khoá học nhanh gọn, đầy đủ và đi thẳng vào vấn đề nên cũng không có gì để bình luận nhiều.

- Đoạn này tui muốn học thêm 1 khoá **thuật toán - Algorithms** nữa, nhưng vẫn còn phải thử và tìm những khoá phù hợp. Xin phép chia sẻ sau nhé. 

À mà.. tui đang giữa chừng ở đoạn ni thôi, nếu các bạn có tò mò về những khoá học dài đến 2 3 tháng trở lên tui sẽ viết review chi tiết sau. Nếu nhập môn thì tui nghĩ đến đây là đủ để bạn tự tin biết mình cần học gì tiếp, hoặc chọn làm project, như tui đã đủ lông đủ cánh để mần django và deploy ra con blog này đây (còn cùi nhưng cũng đủ xài tạm).

Ngoài thời gian chủ động đốt não, tui cũng tranh thủ sử dụng một số nguồn kiến thức có thể tiếp thu thụ động như nghe podcast, đọc blog, xem youtube về chủ đề công nghệ; chiu khó lượn stackoverflow, năng nổ trên các group trên facebook để giao lưu với các tiền bối hoặc các bạn đồng trang lứa. Đây lại là 1 chủ đề dài, chi tiết tui để dành viết sau nha. 

Thời gian đầu rất dễ nản nhưng may mắn tui cũng kịp thời tìm được những nguồn học hữu ích và thú vị. Chúc các bạn học tốt, nếu nản, hãy biết là ngoài kia cũng có người đang bơi như bạn, là tui nè. *Just keep swimming*.

<!-- ![chia-se-kinh-nghiem-tu-hoc-lap-trinh]({{ site.url }}/assets/kinh-nghiem-tu-hoc-lap-trinh.jpg) -->

<center><img src="{{ site.url }}/assets/post1/kinh-nghiem-tu-hoc-lap-trinh.jpg"></center>

[https://pythonprogramming.net/]: https://pythonprogramming.net/
[python-fundamentials]: https://pythonprogramming.net/python-fundamental-tutorials/
[data-analysis]: https://pythonprogramming.net/data-analysis-tutorials/
[michigan-data-science-course]: https://www.coursera.org/specializations/data-science-python
[mit-math-course-youtube]: https://www.youtube.com/watch?v=L3LMbpZIKhQ&ab_channel=MITOpenCourseWare
[mit-math-course-website]: https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-042j-mathematics-for-computer-science-fall-2010/
[akamai-website]: https://www.akamai.com/
[freeCodeCamp-data-structure-course]: https://www.youtube.com/watch?v=RBSGKlAvoiM&ab_channel=freeCodeCamp.org
