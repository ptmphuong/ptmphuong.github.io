---
layout: post
title:  "Prolog là gì?"
date:   2022-04-17 17:50:00 -0700
categories: programming-languages
---

Chuỗi bài giới thiệu về Prolog sẽ bao gồm 2 bài viết. Qua 2 bài viết này, tui sẽ không dạy bạn Prolog, nhưng nếu bạn đang bắt đầu học Prolog, thì thông tin ở đây sẽ vô cùng hữu ích để bạn hiểu và học nhanh hơn. Còn nếu bạn không có ý định học, thì tui sẽ cho bạn biết mùi vị của Prolog là như thế nào.

------------------

Phần 1:
1. Khởi động
2. Prolog là gì?
3. Prolog tìm kiếm câu trả lời bằng cách nào?
4. Prolog vs. SQL

## Khởi động
Đầu tiên, mình khởi động với một câu đố nhỏ:

Tui có một số thông tin về gia đình ông Homer sau:
* Ông Nobi và bà Nobi có 2 người con: chú Nobirou và chú Nobisuke.
* Ông Kataoka và bà Katao có 2 người: cô Tamako và chú Tamao.
* Nobirou có 1 người con là chú Akiyo
* Chú Nobisuke lấy cô Tamako và có 3 đứa con trai: Nobita, và Tôm và Tép.

Hỏi:
* Ông Kataoka có đứa cháu ruột nào tên Akiyo không?
* Bà Kataoka và bà Nobi có cùng những đứa cháu nào?

Nếu phải code, bạn sẽ chọn ngôn ngữ lập trình nào và chọn giải câu này bằng cách nào?

<center><img src="{{ site.url }}/assets/prolog-intro/prolog-puzzle-family-tree.png"></center>

Nếu là tui của 6 tháng trước đây - công dân OOP Java gương mẫu miệt mài Leetcode, có lẽ tui sẽ nhồi thông tin trên vào các class rồi xào xào ra mấy cái tree/graph traversal functions để dùng. Tui ngày hôm nay đã gia nhập được thêm một vài công cụ và ngôn ngữ mới, thì thấy đích thị là 1 vấn đề được sinh ra để dành cho Prolog. 

2 câu hỏi đưa ra đều liên quan đến mối quan hệ *Grandparent - Grandchild*. Để trả lời, mình cần nối các mối quan hệ *Parent - Child* được cho sẵn. 
 
Giải bằng Prolog ngắn gọn đến mức ngỡ ngàng. Mình chỉ cần liệt kê ra các thông tin ra, trong Prolog gọi là **facts**: 

```prolog
% Liệt kê facts về bố/mẹ - con theo format: parent_child(Parent, Child)
parent_child(nobisuke, tom).
parent_child(nobisuke, tep).
parent_child(nobisuke, nobita).
parent_child(tamako, tom).
parent_child(tamako, tep).
parent_child(tamako, nobita).
```
*Có tổng cộng 15 mối quan hệ Parent - Child. Code hoàn thiện tại [đây][nobita-family-tree-full].

[nobita-family-tree-full]: https://github.com/ptmphuong/tuihoccode_demo_code/blob/main/prolog/intro/nobita_family_tree.pl

Để trả lời câu đầu: Ông Kataoka có đứa cháu ruột nào tên Akiyo không?

Mình định nghĩa quy tắc - rules để định nghĩa mối quan hệ giữa Grandparent, Parent và Child, như sau:
```prolog
grandparent_grandchild(GrandParent, GrandChild) :-
    parent_child(GrandParent, Parent),
    parent_child(Parent, GrandChild).
```

Rule `grandparent_grandchild/2` có 2 variables chính là `GrandParent`, `GrandChild` (`/2` do rule này có 2 variables). Ngoài ra, mình dùng thêm `Parent` nữa để bắc cầu. Nếu muốn chạy thử, bạn copy facts và rule này cho vào [SWISH][swish.swi-prolog.org] (Prolog playground) chạy, sẽ cho ra kết quả như sau:

[swish.swi-prolog.org]: https://swish.swi-prolog.org/

<center><img src="{{ site.url }}/assets/prolog-intro/prolog-puzzle-family-tree-a1.png"></center>

Bà Kataoka và bà Nobi có cùng những đứa cháu nào? Mình lại viết thêm 1 cái rule nữa, vận dụng `grandparent_grandchild/2` đã viết ở trên. Do tìm 2 bà chung 1 cháu, nên tui dùng variable `GrandChild` để bắc cầu.

```prolog
mutual_grandchildren(GrandParent1, GrandParent2, GrandChild) :-
    grandparent_grandchild(GrandParent1, GrandChild),
    grandparent_grandchild(GrandParent2, GrandChild).
```

<center><img src="{{ site.url }}/assets/prolog-intro/prolog-puzzle-family-tree-a2.png"></center>

Đơn giản dữ vậy? Prolog trả lời thông tin cho bạn bằng cách nào? Bình tĩnh, mời đọc tiếp. 

## Prolog là gì?

Khoảng những năm 60s 70s, khi chủ đề toán logic đang nóng hừng hực trong lĩnh vực toán học, các bác nghiên cứu tin rằng có thể tạo ra một cơ sở kiến thức lớn và kết nối chúng bằng logic là nền tảng của trí tuệ nhân tạo (\*). Nhà nhà quan tâm và nghiên cứu chủ đề này, thế là đến năm 1972, Prolog chính thức ra đời, viết tắt cho programmation en logique (lập trình logic), tại Fran-xê.

(\*) *Đúng nhưng chưa đủ. Đến các năm 80 90 thì các bác bảo cần phải có số nữa. Ngày nay học ML/AI thì tất nhiên là phải học thêm rất nhiều xác suất thống kê.*

Code với Prolog, mình không cần định nghĩa một vấn đề cần giải bằng những bước nào, function không tồn tại trong thế giới Prolog. Ngược lại, mình chỉ cần khai báo ra đầy đủ **facts** và **rules**, còn lại để Prolog lo. Prolog dĩ nhiên vì vậy mà thuộc vào nhóm **Lập Trình Khai Báo - Declarative Paradigm**.

Cũng tiện note thêm, Prolog coi các từ có chữ đầu viết thường: *june*, *marge*, …  là **atom**. Atoms tựa như là literals vậy - giá trị mà nó thể hiện chính nó. Còn những từ có chữ đầu viết hoa: *Parent*, *GrandParent*, …  là **variables** - tham số.

## Prolog tìm kiếm câu trả lời bằng cách nào? 	

Facts và rules sau khi được khai báo, Prolog sẽ lưu lại trong thư viện của mình - **Knowledge Base**. Khi nhận được câu hỏi mới ở quầy Question, Prolog sẽ chạy vào Knowledge Base, lục tìm đáp án và cho ra câu trả lời.

<center><img src="{{ site.url }}/assets/prolog-intro/how-prolog-works.png"></center>

Câu trả lời có thể ở dạng:
* true/false: xác nhận xem câu hỏi có đúng với thông tin Prolog nắm được không. *(a)*
* các giá trị đáp ứng yêu cầu của rule. *(b)*

<center><img src="{{ site.url }}/assets/prolog-intro/prolog-answer-types.png"></center>

## Backtracking trong Prolog

Ai từng bị leetcode ám ảnh như tui, mỗi lần thấy chữ backtracking trồi lên là lại nhăn trán nhăn mày. Tui từng bị ám ảnh đến độ đi ngủ còn mơ thấy mình nhảy lò cò từ node này qua node nọ trên graph. Nhưng quen dần với Prolog, thì khái niệm backtracking nhẹ nhàng hơn hẳn.

Câu hỏi mang từ quầy Question vào, Prolog sẽ gọi là **Goal**. Từ Goal, Prolog sẽ tìm cách truy ngược từ goal (backtrack) trong Knowledge Base để tìm ra sự thật. Nếu có nhiều câu trả lời thì Prolog sẽ sử dụng **Union** (phép hợp nhất) và chỉ trả lại tập trả lời đạt yêu cầu. 

<center><img src="{{ site.url }}/assets/prolog-intro/prolog-backtracking-1.png"></center>

Nếu Rule này chỉ đến Rule kia thì Prolog sẽ tiếp tục đi ngược lại, vừa đi vừa dựng thêm kiến thức trong Knowledge Base, truy tìm cho đến khi nào tận gốc. Nếu tìm thấy những Facts và Rules xung đột lẫn nhau thì sẽ trả lại ngay kết quả false.

<center><img src="{{ site.url }}/assets/prolog-intro/prolog-backtracking-2.png"></center>

Trường hợp goal có liên quan đến Recursion, thì Prolog sẽ truy ra đến Base Cases. Nếu không định nghĩa recursive chính xác thì xác định ăn timeout hoặc stack overflow. Tui sẽ nói nhiều hơn về recursion trong Prolog ở phần 2 khi mình XOAY. 

Zoom kỹ hơn vào chỗ này trong hình cách hoạt động của Prolog: 

<center><img src="{{ site.url }}/assets/prolog-intro/prolog-backtracking-2.png"></center>

Bạn có ngợ ra tại sao dùng Prolog để trả lời câu đố khởi động dễ dàng đến như vậy không? 

Nếu sử dụng một ngôn ngữ imperative như Java, Python, Rust, mình sẽ phải tự code ra một thuật toán backtracking nào đó - tree dfs/bfs để sử dụng. May mắn thay, bản thân Prolog là cả một bộ máy backtracking đã được tối ưu, cho facts và rules vào là prolog chạy ra kết quả. Do đó, trong những trường hợp có nhiều dữ kiện và quy tắc cần sử dụng backtracking, Prolog là một ứng viên sáng giá. 1 lần gần đây nhất tui tự tìm đến Prolog là để giải wordle. 
 
Ngoài ra, Có một câu hỏi tui thắc mắc trong thời gian mới làm quen với Prolog: Nếu cũng là ngôn ngữ truy vấn, thì Prolog với SQL khác nhau chỗ nào? 

## Prolog vs SQL

SQL và Prolog đều là 2 ngôn ngữ mạnh về truy vấn. 

Nếu nói theo thuật ngữ của Prolog - thế giới của facts và rules, thì SQL mạnh hơn khi truy vấn trong knowledge base có nhiều facts/data. Các thao tác quản lý data (storage, retrieval, projection) SQL rõ ràng là lợi hại hơn. 

Prolog mạnh hơn khi truy vấn trong knowledge base có nhiều rules. Rules này dẫn sang rules kia, và cả recursion nữa.

SQL thường được dùng trong server, Prolog thường được chọn dùng ở phía client. 

Cả 2 ngôn ngữ đều là Turing Complete, nghĩa là bất cứ vấn đề nào có thể giải được bằng các ngôn ngữ lập trình khác, Prolog và SQL có thể giải được. Bạn có thể viết lại toàn bộ SQL code base bằng Prolog, và ngược lại. Tuy nhiên, ai lại muốn tự làm khó mình tới vậy.

----------------------
## Kết

Ok, thế là mình đã làm quen sơ với Prolog. Trông cũng có vẻ hiền lành Cho đến khi bạn phát hiện ra: Prolog không có function, không có return statement, và cũng không có for/while loop. Vậy làm thế nào để Prolog scale trong 1 code base lớn? Làm thế nào để xử lý list, pass thông tin giữa các rule? Mời quý vị đón xem tập tiếp theo. **Xoay, Xoay lộn, Xoay lộn tùng phèo với Prolog**. 




