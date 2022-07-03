---
layout: post
title:  "Leetcode luyện phỏng vấn vs. Đi làm"
date:   2022-06-19 19:00:00 -0700
categories: career-stories
---

Trong một bài blog [cũ][Xin thực tập Software Engineer đầu tiên tại Mỹ], tui hùng hồn tuyên bố: 

<center>“Ttui không thích leetcode đâu."</center>

<br>

Ồ queo queo 😅, tui xin rút lại lời nói đó.

[Xin thực tập Software Engineer đầu tiên tại Mỹ]: https://tuihoccode.com/career-stories/2022/04/09/xin-thuc-tap-software-engineer-dau-tien-tai-my.html](https://tuihoccode.com/career-stories/2022/04/09/xin-thuc-tap-software-engineer-dau-tien-tai-my.html

Tuần thứ 2 đi thực tập, tui bắt đầu làm quen với code base của team và viết một helper function nho nhỏ. Lúc này mới ngộ ra những kỹ năng khi luyện phỏng vấn với leetcode giúp ích cho mình như thế nào.

Note: Leetcode bài nào (vd: Tree, BFS, DFS, DP, … ), có áp dụng vào công việc không thì tui không biết. Cái đó tuỳ thuộc vào tính chất công việc, team, và công ty.

Ở đây, tui chỉ đề cập đến những kỹ năng bạn học được khi giải algo và luyện leetcode để phỏng vấn có thể áp dụng được đến đâu trong môi trường làm việc của Software Engineer.

##  **1. Tìm cách giải tối ưu**

Ticket đầu tiên của tui là làm **string manipulation for a name field** để hỗ trợ chức năng tìm kiếm cho một sản phẩm nội bộ. Nói đơn giản là vậy.

Đọc xong mô tả, tui thở phào “ồ, cũng dễ mà. cái này viết 10 phút là xong". Cho đến nửa ngày sau, tui vẫn còn đi lạc trong cái code base để tìm xem mình sẽ nhét cái chỗ sửa của mình ở đâu, và nhét các helper function của mình ở đâu, tui mới bắt đầu mở mắt to ra và nhận ra rằng: cái code của mình, chắc chỉ tầm 5 dòng thôi, nhưng nó sẽ liên quan đến cả cái đống code này.

Lúc này tui gác tay lên trán và suy nghĩ: Làm sao để trà trộn cái feature siêu nhỏ của mình vào đây mà không ảnh hưởng đến performance của đống code chất lượng này? Viết như thế nào cho tối ưu nhất?

Khi giải leetcode, mình luyện giải tối ưu cho time & space complexity để ghi điểm cho buổi phỏng vấn. Khi đi làm, mình có trách nhiệm với khối lượng dữ liệu và người dùng lớn, mình thấm thía tầm quan trọng của việc viết code tối ưu và hiệu quả. Every optimization counts.



## **2. Cân nhắc hết các trường hợp ngoại lệ aka edge cases**

Lúc viết xong 1 bản nháp của code, tui rà lại code, test nhẹ trên các trường hợp sẵn có và nhận được các kết quả như ý muốn. Sướng quá nên tui hí hửng đem đi khoe với mentor thì được bốp lại câu này: 
> “Test cases are your friend. Via postman it will usually work because the database has correct values but we need our code safeguarded against all future bad values.”

Thấm thía thiệt, tui nghĩ mình đã cover các trường hợp input *rỗng* và *null*. Nhưng thế chưa đủ, mình phải đặt thêm nhiều câu hỏi. Khi công ty hoặc sản phẩm đó phát triển thêm, giải pháp của mình có đủ trường tồn không? Làm sao để đạt được điều đó?

Khi làm leetcode, mình có thể make assumptions về các thể loại input. Khi đi làm thật, mình phải suy nghĩ thấu đáo hơn. Mình phải viết đầy đủ **tests, unit tests**, để chắc chắn code chạy đúng như mình dự định.

Một tip nhẹ khi đi phỏng vấn, nếu tình huống cho phép hãy đặt bài toán và giải pháp của mình vào một dự án thật. Mình có thể đặt thêm câu hỏi về tương lai phát triển của tính năng này và đưa ra những phương án thích hợp. 

## **3. Viết code dễ đọc**

Tui không ngờ rằng nội cái chuyện nghĩ tên cho từng function và variable thôi mà lại tốn thời gian đến thế.

- Tên thế này đã đủ nói lên công dụng của cái variable này chưa? Chọn tên `name` cho ngắn hay phải ghi `nameWithoutPrefix` cho đầy đủ dễ đọc nhỉ?
- Tên này có đồng bộ với cách đặt tên của các variable khác trong code base không?
- Đoạn code này đọc vào có thể hiểu ngay mà không cần phải thêm comment không?

Ngoài việc đặt tên đồng bộ, mình còn phải chú ý đến việc đồng bộ code style.

Ví dụ trong Java mình có thể viết one-liner for `return`  statement:

```java
if (this) return that;
```

Nhưng code style không cho phép thì mình cũng phải sửa lại thôi:

```java
if (this) {
        return that;
        }
```

Ngoài ra còn có chuyện viết log, dùng paradigm, ... ti tỉ các chi tiết khác cần được viết đồng bộ với code base nữa.

Khi phỏng vấn, làm leetcode, thực hành đặt tên biến dễ đọc, viết code dễ hiểu luôn là một điểm cộng. Khi làm việc trong một code base lớn cùng với nhiều người khác, đây là chuyện bắt buộc.

Đó, một đoạn code tui xuề xoà tưởng chừng mất 10’ cuối cùng ngốn tui hết tận nửa ngày, còn chưa kể thời gian đi làm trong code base. Nhưng đó là lần đầu tiên tui cống hiến, cũng là lần đầu tiên tui đi làm software engineer, nên thôi chắc du di và mong rằng sau này sẽ lẹ hơn, không thì người ta đuổi sớm tui mất.

## **4. Khả năng trình bày giải pháp**

Last but not least, khả năng trình bày và lý luận giải pháp của mình là một trong những kỹ năng tui học được khi luyện phỏng vấn, và dùng làm bàn đạp để giao tiếp hiệu quả hơn trong công việc.

Trước khi bắt tay vào code, tui có đề nghị cách tiếp cận và xác nhận là phù hợp với cấu trúc hiện tại của code base. Với những tính năng có tầm hơn, từ các sếp đến dân mọn như tui cũng phải viết proposal. Proposal phải nhận được chấp thuận của dân tình rồi mới được tiến hành code.

Khi bí và cần giúp đỡ, mình phải biết nhanh chóng trình bày context và giải thích tại sao mình bí. Trình bày tốt thì mình tạo được thiện cảm và được giúp đỡ nhiệt tình. A hèm, khi phỏng vấn mà bí thì may ra cũng có thể xin hint.


## **Kết**

Bài này một phần là để đính chính lại lời tuyên bố nai tơ của mình 🥹. Phần còn lại là để trả lời cho câu hỏi hồi đi luyện phỏng vấn mình vẫn hay kiếm tìm: “Luyện leetcode phỏng vấn có giúp ích gì cho khi đi làm không?”.

Tui không cố xuý việc phải luyện học thuộc nhiều trăm câu leetcode để đối phó với việc phỏng vấn. Nhưng, các kiến thức algo, và việc sử dụng leetcode để luyện phỏng vấn đều giúp ích rất nhiều cho những người mới đi làm như tui này.

---

À quên, không biết có ai quan tâm không, nhưng tui đi làm vui lắm. Sau khi nghỉ việc mông lung gap year 1 năm, đi học 2 năm, giờ được quay lại với môi trường làm việc thấy đời bỗng rộn ràng. Vậy thôi, see you in the next post : )

<br>

<center><img src="{{ site.url }}/assets/about/leetcode-vs-dil-lam-2.JPG"></center>
