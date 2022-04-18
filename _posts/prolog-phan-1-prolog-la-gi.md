---
layout: post
title:  "Xoay lộn tùng phèo với Prolog. Phần 1: Prolog là gì?"
date:   2022-04-17 17:50:00 -0700
categories: programming-languages
---

Chuỗi bài giới thiệu về Prolog sẽ bao gồm 2 bài viết: 

* **Phần 1: Prolog là gì? Prolog hoạt động như thế nào?**
* **Phần 2: States, Lists và Recursion trong Prolog**

Trong 2 bài viết này, tui sẽ không dạy bạn Prolog, đúng hơn là không dạy nổi. Nhưng nếu bạn đang bắt đầu học Prolog, thì thông tin ở đây sẽ vô cùng hữu ích để bạn hiểu và học nhanh hơn. Còn nếu bạn không có ý định học, thì tui sẽ cho bạn biết mùi vị của Prolog là như thế nào.

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

Tui hỏi:
* Ông Kataoka có đứa cháu ruột nào tên Akiyo không?
* Bà Kataoka và bà Nobi có cùng những đứa cháu nào?

Nếu phải code, bạn sẽ chọn ngôn ngữ lập trình nào và chọn giải câu này bằng cách nào?

Để tui vẽ cái sơ đồ ra để mọi người dễ mường tượng: 
<center><img src="{{ site.url }}/assets/prolog-intro/prolog-puzzle-family-tree.png"></center>

Nếu là tui của 6 tháng trước đây - công dân OOP Java gương mẫu miệt mài Leetcode, thì có lẽ sẽ nhồi thông tin trên vào các class rồi xào xào ra mấy cái tree/graph traversal functions để dùng.

Tui ngày hôm nay đã gia nhập được thêm một vài công cụ và ngôn ngữ mới, thì thấy đích thị là 1 vấn đề được sinh ra để dành cho Prolog. 

2 câu hỏi đưa ra đều liên quan đến mối quan hệ Grandparent - Grandchild. Để trả lời, mình cần nối các mối quan hệ Parent - Child được cho sẵn. 
 
Giải bằng Prolog ngắn gọn đến mức ngỡ ngàng. Mình chỉ cần liệt kê ra các thông tin ra, trong Prolog gọi là facts: 

```prolog
% Liệt kê facts về bố/mẹ - con theo format: parent_child(Parent, Child)
parent_child(nobisuke, tom).
parent_child(nobisuke, tep).
parent_child(nobisuke, nobita).
parent_child(tamako, tom).
parent_child(tamako, tep).
parent_child(tamako, nobita).
```

Để trả lời câu đầu: Ông Kataoka có đứa cháu ruột nào tên Akiyo không?

Mình định nghĩa quy tắc - rules để định nghĩa mối quan hệ Grandparent - Parent - Child, như sau:
```prolog
grandparent_grandchild(GrandParent, GrandChild) :-
    parent_child(GrandParent, Parent),
    parent_child(Parent, GrandChild).
```

Rule `grandparent_grandchild/2` có 2 variables chính là `GrandParent`, `GrandChild` (`/2` do rule này có 2 variables). Ngoài ra, mình dùng thêm `Parent` nữa để bắc cầu. Nếu muốn chạy thử, bạn copy facts và rule này cho vào SWISH (Prolog playground) chạy, sẽ cho ra kết quả như sau:

<center><img src="{{ site.url }}/assets/prolog-intro/prolog-puzzle-family-tree.png"></center>


\* 
