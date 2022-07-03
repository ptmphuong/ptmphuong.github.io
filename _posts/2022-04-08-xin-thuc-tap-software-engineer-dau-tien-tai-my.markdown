---
layout: post
title:  "7 tháng tìm công việc thực tập SWE đầu tiên tại Mỹ"
date:   2022-04-08 22:14:00 -0700
categories: career-stories
---

Hè 2021 là kỳ học cuối tui có thể học từ xa, tui tranh thủ khăn gói laptop vào vali và đi lòng vòng nước Mỹ. Cuối tháng 8 về lại trường, tui ngẩn ngơ khi thấy bạn bè xung quanh đã và đang miệt mài luyện leetcode, chuẩn bị phỏng vấn, dự career fair,… Rồi đứa em nó nhắn: *chị phải chuẩn bị cv liền đi, các công ty học đang đăng tuyển cho hè năm sau rồi đấy!* 

Thế là tui, tháng 9/2021, trong tâm trạng hoang mang, vắt chân lên cổ tham gia cuộc đua tìm internship cho mùa hè 2022.

## __Sao phải bắt đầu nộp sớm thế?__

Tháng 8, 9 là thời điểm sớm nhất cho các công ty bắt đầu mở nhận hồ sơ cho mùa hè năm sau, dù cũng vẫn có một số công ty bắt đầu trễ hơn - vào tháng 11, 12. Thực tập mùa hè thường bắt đầu vào tháng 6, như vậy là cũng sớm hơn đến cả nửa năm. Họ bắt đầu sớm như vậy vì một số lý do sau:
* Quá trình phỏng vấn gồm nhiều giai đoạn, tốn nhiều thời gian. Những công ty lớn tuyển nhiều thì càng tốn nhiều thời gian hơn.
* *Early bird gets the worm*. Nhiều công ty tranh thủ tổ chức tuyển dụng sớm để chiếm sớm những ứng viên giỏi.
* Cần dành ra thời gian làm các thủ tục hành chính từ lúc chốt offer cho đến lúc bắt đầu đi làm (chọn ứng viên vào từng team và project phù hợp, sinh viên quốc tế có thời gian xin SSN - mã số an sinh xã hội, CPT để có thể thực tập, vân vân) 

## __Quá trình phỏng vấn cho Software Engineer Intern__
Dưới đây là các bước chung cho giai đoạn phỏng vấn. Các vòng được cắt bớt, hoặc chèn thêm, tùy vào từng công ty.

### 1. Nộp resume
Tui nhớ khoảng tháng 9 đến 11 là mùa tuyển dụng cao điểm cho mùa hè năm sau., các công ty nô nức trẩy hội đăng tuyển đăng tuyển trên các trang tuyển dụng như [LinkedIn][linkedin.com], [Handshake][handshake.com],... và cả trang nghề nghiệp của các trường. Một số công ty lớn có tổ tổ chức thực tập quanh năm (thu, xuân) thì sẽ đăng khoảng trước 6 tháng trước cho mùa làm việc đó..

[linkedin.com]: https://www.linkedin.com/
[handshake.com]: https://joinhandshake.com/

### 2. Online Assessment
Nếu hồ sơ được lọt qua vòng đầu, bạn sẽ được gọi làm bài test online, mọi người hay gọi tắt là OA. Ở vòng này, mình được gửi link dẫn đến các trang làm bài test (như [Codesignal][codesignal.com], [Hackerrank][hackerrank.com]) và làm tầm 2~4 câu hỏi dạng leetcode trong vòng 60~120 phút.

[codesignal.com]: https://codesignal.com/
[hackerrank.com]: https://www.hackerrank.com/

#### Câu hỏi dạng leetcode là gì?
Đây là những câu đố ngắn, thường được sử dụng để kiểm tra tư duy và kiến thức lập trình căn bản.

| Ví dụ: |
| ------ |
| Cho một từ `word = “abcvee”`, hỏi ký tự nào trong `word` là ký tự đầu tiên không tuân thủ trình tự của bảng chữ cái? Tìm cách giải cho `word` bất kỳ, có thể cho rằng các từ `word` đều chỉ bao gồm chữ trong bảng chữ cái tiếng anh. |

 Câu trả lời là `‘v’`.

Cái chính ở đây là mình phải code cách giải cách tối ưu (time and space complexity), đáp ứng cho mọi trường hợp - như ở đây thì mình phải bao gồm cả trường hợp có ký tự viết hoa viết thường lẫn lộn - `“aBCvEE”` chẳng hạn. 

Đây chỉ là một ví dụ đơn giản. Với các vấn đề khó hơn, như graph, dynamic programing vân vân, thì mình phải biết áp dụng các cách giải đã được chứng minh, hay thuật toán (algorithms) để giải quyết.

### 3. Phone screen
Vòng này cũng vẫn là leetcode, nhưng mình code live trên google sheet hay [coderpad][coderpad.io] cùng với 1 nhân viên lập trình của công ty, vừa giải vừa nói những gì mình đang suy nghĩ. 

Các câu hỏi ở vòng này có thể sẽ mờ ảo hơn. Ngoài việc giải, mình còn phải thể hiện cách tiếp cận với những vấn đề chưa rõ ràng, cách trình bày vấn đề, tư duy giải quyết cho người phỏng vấn. 

[coderpad.io]: https://coderpad.io/

| Cũng với câu hỏi trên |
| ------ |
| Tìm ký tự đầu tiên không tuân thủ trình tự của bảng chữ cái cho 1 word **bất kỳ**. |

Thì mình phải cân nhắc đủ các trường hợp ngoại lệ, và đề xuất cách giải quyết:
* `word = “abcv”` mọi ký tự đều	thuận bảng chữ cái
* `word = “r1?a”` trường hợp có số/symbol
* `word = “”` 		  trường hợp vườn không nhà trống
* …

Đối với những câu hỏi hóc búa, họ còn quan sát xem mình phản ứng ra sao - hoang mang sợ hãi, hay có thể giữ bình tĩnh để suy nghĩ và hợp tác với người phỏng vấn để giải quyết vấn đề. 

Một lần phỏng vấn, anh lập trình viên cũng thử dạy cho tui một số kỹ năng mới, mục đích là để xem xem khả năng tiếp thu thông tin, kiến thức tới đâu.

### __4. Final__

Final lại kiểm tra leetcode như trên lần nữa, hoặc test kỹ năng mềm, hoặc cả hai.

**Bạn có kỳ vọng gì cho đợt thực tập này? (What do you look for in this internship?)** là câu hỏi lần nào phỏng vấn tui cũng gặp.

Đối với kỹ năng mềm, họ hỏi những câu hỏi tình huống kiểu như: 
* Kể về 1 lần bạn thất bại
* Bạn học công nghệ mới bằng những cách nào?
* Với mình, tại sao lại chọn chuyển ngành? 

Ngoài ra họ cũng hay hỏi thêm về kinh nghiệm, các chi tiết technical mà mình nêu trên resume. 

Sau mỗi buổi phỏng vấn từ phone screen đến final, mình đều có 5-10’ cuối buổi để hỏi về trải nghiệm của họ trong team và công ty.

### __5. Offer__

Tới bước này là thảo luận thủ tục, thù lao - thường được trả theo tiếng hoặc theo tuần. Các công ty lớn, hào phóng thì còn có hỗ trợ thêm chi phí nhà ở, di chuyển. Sau đó mình ký offer rẹt rẹt rồi đi ăn mừng thôi.


## __Cảm nhận cá nhân về quá trình__

### __A leetcode a day keeps unemployment away__

Là intern/new grads chưa có nhiều kinh nghiệm, nên phần lớn quá trình tuyển dụng đều xoay quanh các câu hỏi leetcode để test cách tư duy của ứng viên.

_Tui không thích leetcode đâu_. (*) Thời gian đầu tui chỉ muốn lao đầu vào làm project, học các công nghệ mới. Nhưng phải công nhận luyện leetcode giúp tui rất nhiều trong việc rèn cấu trúc dữ liệu, thuật toán, viết code thơm tho sạch sẽ hơn. Xịn nhất là khi tui phát hiện ra mình cũng tiến bộ về cách tiếp cận và giải quyết vấn đề ra phết.

(*) Tui xin rút lại câu này 😅 Bài viết đính chính ở đây: [Leetcode luyện phỏng vấn vs. Đi làm]([url](https://tuihoccode.com/career-stories/2022/06/20/leetcode-luyen-phong-van-vs-di-lam.html))


Mọi thứ đều xoay quanh leetcode cũng là một kẽ hở của quy trình này. Trang leetcode có 1 kho câu hỏi, ai chăm giải leetcode nhiều thì có thể nhớ cách giải. Do đó nếu tuyển dụng chỉ dựa trên leetcode thì khó có thể test toàn diện được khả năng của ứng viên.

### __Chuyển ngành là một lợi thế lớn__

Tui tuy chưa có kinh nghiệm làm software engineer intern nào cả, nhưng trước đây đã đi làm business được gần 5 năm. Vào đến vòng ứng xử, tui có rất nhiều câu chuyện liên quan đến chuyển ngành để chém, cụ thể là về những rào cản, khó khăn mà đã vượt qua. Đây là những điểm giúp tui dễ dàng nổi bật hơn những ứng viên khác. 

Khi trả lời những câu hỏi tình huống, tui thấy tui thường bị vặn ít hơn khi kể về các tình huống ở lĩnh vực khác ngoài tech. Chắc là họ không rành nên cũng không hỏi sâu, tui đoán vậy.

### __Yếu tố may mắn__

Lượng gửi hồ sơ đến các công ty rất lớn, ngoài việc lọc cv bằng cách scan từ khóa ra, tui  mạnh dạn đoán rằng họ cũng búng tay bớt đi để chọn ra ai được đi các vòng tiếp theo. Có các bạn cùng học với tui, CV trông tương tự, cũng nộp cùng một đống công ty như nhau, nhưng có chỗ thì chỉ gọi tui, chỗ thì chỉ gọi nó.

Người phỏng vấn cũng là một yếu tố may mắn rất lớn. Lúc không hên, tui gặp phải người ít nói, hoặc đúng lúc người ta đang bận tâm việc khác, thì áp lực giải bài phải khá nặng nề. Còn khi hên thì mình gặp phải người vui vẻ hòa đồng, trao đổi nhiều và họ cho gợi ý, hoặc có lúc cùng brainstorm, collab với mình để giải đề. Những lúc phỏng vấn vậy mình rất vui, như là làm cùng với đồng nghiệp vậy, nên tâm trạng cũng thoải mái để giải bài. 

## __Kinh nghiệm cá nhân__

CV của tui khá giản đơn, chưa có kinh nghiệm gì nên chỉ bao gồm những môn đã học trên trường, thêm project tự làm hoặc làm ở trên trường. Project của tui cũng chỉ gà gà, tầm nhỏ - trung bình nhỏ thôi. Trên trường, tui có một số hoạt động như làm trợ giảng, tham gia câu lạc bộ tui có thêm vào. Ngoài ra tui cũng điểm ra các kỹ năng liên quan, như làm analytics, hoặc landing page ở những công việc cũ. 

Nay là cuối tháng 3, tui may mắn có chút thành tích gọi là nên note lại mấy dòng này, gọi là kết thúc quá trình 7 tháng tìm chỗ thực tập.

| Đơn nộp | Làm OA | Phone | Final | Offer |
| ------- | ------ | ----- | ----- | ----- |
| 235 | 10 | 5 | 3 | 3 |

Đơn nộp nhiều, nên cứ vài ba ngày là tui lại nhận mail "we've decided to move forward with other candidates".

Những lúc làm xong OA, hay phỏng vấn thì cứ thấp thỏm chờ đợi mail, nếu là mail từ chối thì càng buồn gấp bội. 7 tháng trôi qua rất chậm, nhưng tình hình chung là vậy, nên mình cứ phải cố gắng thôi.

Có 1 [trang][2022-summer-intern-process-tracking] này thu thập tiến độ của nhiều người, nhưng xem cho vui thôi vì tui cảm giác là các bạn được tiến xa hơn thì hay chăm chỉ vào điền mấy cái form này hơn.

[2022-summer-intern-process-tracking]: https://www.cscareers.dev/process-tracking/2022-summer-intern

<center><img src="{{ site.url }}/assets/first-internship-app/2022-summer-intern-process-tracking.png"></center>

## __Kết__

Có bạn bảo: *Hình như tech là ngành duy nhất yêu cầu bạn phải có đam mê mới theo đuổi được*. Nhưng là tui hoàn toàn không đòng ý. Ngành nào cũng cần đam mê và tận tụy để theo đuổi và thành công hết. Nhưng có 1 điều không thể phủ nhận được là tech là một trong những ngành cạnh tranh nhất trên thị trường hiện nay. Các bạn mới bắt đầu, và bắc ngang như mình phải cần cù chịu khó thật nhiều, thì mới bước chân được vào cánh cửa. Nên mình phải cố lên thôi, cố cho đến ngày mình làm được, cho đến ngày yếu tố may mắn nháy mắt với mình *\*blink blink\**

<center><img src="{{ site.url }}/assets/first-internship-app/welcome-to-confluent.png"></center>
<br>
<center><img src="{{ site.url }}/assets/first-internship-app/welcome-aboard-noogler.png"></center>
