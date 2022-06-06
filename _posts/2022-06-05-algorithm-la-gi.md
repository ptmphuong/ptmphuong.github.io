---
layout: post
title:  "Algorithm là gì? Tại sao học lập trình lại phải học Algorithms?"
date:   2022-06-05 15:00:00 -0700
categories: cs-foundation
---


<center><img src="{{ site.url }}/assets/algo/what-is-algorithm.png"></center>

<br>

Bài này tui viết cho tui cách đây 2 năm, người con gái chân ướt chân ráo lơ ngơ đi học lập trình.

**Algorithm**? Cái từ gì vừa ảo ảo và còn lại hay gặp. **Thuật toán**. Chậc, nghe thật cao siêu. Hỏi [wikipedia](https://en.wikipedia.org/wiki/Algorithm) thì được đập cái đống này vào mặt:

> In mathematics and computer science, an algorithm (/ˈælɡərɪðəm/ (listen)) is a finite sequence of rigorous well-defined instructions, typically used to solve a class of specific problems or to perform a computation. 

*Finite Sequence*, *Instructions*, *Computation*, … là gì nữa? Thế là cả một thời gian đấy, đi đâu đọc tài liệu mà thấy chữ *algorithm* là đầu tui sẽ tự động beep cái đoạn đó ngay.

Bây giờ nhìn lại cũng không nhớ sao hồi xưa tui lại xoắn như vậy nữa.


## **1. Algorithm là gì?**

Algorithms có thể được hiểu rất đơn giản, là: 
<center>cách làm một công việc hoặc cách giải quyết một vấn đề<br>được viết chi tiết ra bằng nhiều bước.</center>

. . .

Một trong những thuật toán để **đập trứng bằng một tay** là:
1. Rửa tay
2. Đập bể nhẹ ngay chính giữa quả trứng
3. Vòng ngón trỏ và ngón cái xung quanh quả trứng sao cho 2 đầu ngón nằm ngay chỗ vừa bể nhẹ
4. Dùng lực ngón cái để mở banh quả trứng
5. Dùng lực 2 ngón để tách vỏ trứng và để trứng rơi ra.

Voilà! Sự nghiệp chiên trứng của tui đã tiến lên một tầm cao mới.

. . .

Có nhiều cách để hoàn thành một công việc, cũng như có nhiều thuật toán để giải quyết được một vấn đề.

Một trong những thuật toán để **sort a list `L`** là:
1. Tạo 1 list mới tên `Ls`
2. Lấy 1 số nhỏ nhất trong `L` ra rồi thêm vào `Ls`
3. Lập lại bước 2 cho đến khi không còn gì trong `L` nữa.

| L | Ls |
| --- | --- |
| 3, 4, 1, 2 |  |
| 3, 4, 2 | 1 |
| 3, 4 | 1, 2 |
| 4 | 1, 2, 3 |
|   | 1, 2, 3, 4 |

. . .

Nếu bạn đến đây là để tìm định nghĩa của Algorithms hoặc thuật toán thì nó đơn giản là vậy thôi, không có gì cao siêu cả.

## **2. Tại sao học lập trình lại phải học Algorithms**

Mình học lập trình để điều khiển máy tính làm việc theo ý mình.

Còn máy tính thì chạy dựa trên một loạt các mệnh lệnh mà mình đưa ra. Hmm, nghe giông giống… algorithms?

Quay lại với định nghĩa Algorithms của [wikipedia](https://vi.wikipedia.org/wiki/Thu%E1%BA%ADt_to%C3%A1n):

> Trong toán học và khoa học máy tính, một thuật toán, còn gọi là giải thuật, là một tập hợp hữu hạn các hướng dẫn được xác định rõ ràng, có thể thực hiện được bằng máy tính, thường để giải quyết một lớp vấn đề hoặc để thực hiện một phép tính.

Ha. Cũng có lý.

Thuật toán được dùng trong mọi ngóc ngách của Computer Science. Các chương trình máy tính về bản chất đều là các thuật toán được diễn đạt bởi các ngôn ngữ lập trình cho máy tính hiểu và thực thi.

## **3. Kết**

Bài này tui xin phép viết ngắn gọn vậy thôi. Tui của ngày trước đã từng ước gì có thể tìm một lời giải thích ngắn gọn về Algorithm để có thể nhanh chóng trở lại đọc tiếp tài liệu.

Nếu bạn thắc mắc **Tại sao phải ôn luyện Algorithms để phỏng vấn xin việc làm Software Engineer**, bài viết này của tui có nói sơ qua: [7 tháng tìm công việc thực tập SWE đầu tiên tại Mỹ](https://tuihoccode.com/kinh-nghi%E1%BB%87m/2022/04/09/xin-thuc-tap-software-engineer-dau-tien-tai-my.html).

Ngoài ra, tui rất thích series Crash Course Computer Science của Crash Course ở trên Youtube. Các bạn í có 1 tập về [Intro to Algorithms](https://www.youtube.com/watch?v=rL8X2mlNHPM&ab_channel=CrashCourse) để bạn tham khảo thêm.

Để thực tập giải algo thì xin mời bạn ghé [leetcode.com](https://leetcode.com/) quẹo lựa.




