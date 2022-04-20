---
layout: post
title:  "Xoay lộn tùng phèo với Prolog"
date:   2022-04-17 17:50:00 -0700
categories: programming-languages
---

Chuỗi bài giới thiệu về Prolog sẽ bao gồm 2 phần: 
* __A. Prolog là gì? Prolog hoạt động như thế nào?__
* __B. State transition, list and recursions in Prolog.__

Tui sẽ viết liền tù tì cả 2 phần trong bài viết này. Cả bài viết sẽ dài hơn các bài bình thường nên bạn có thể chia thời gian ra đọc theo dàn bài dưới đây. Trong bài viết này, tui sẽ không dạy bạn cách code bằng Prolog; nhưng nếu bạn đang bắt đầu học Prolog, thì thông tin ở đây sẽ vô cùng hữu ích để bạn hiểu và học nhanh hơn. Nếu bạn không có ý định học, thì 2 phần này sẽ cho bạn biết mùi vị của Prolog là như thế nào.

* [Phần A:](#phần-a)
   * [Khởi động](#1-khởi-động)
   * [Prolog là gì?](#2-prolog-là-gì)
   * [Prolog tìm kiếm câu trả lời bằng cách nào?](#3-prolog-tìm-kiếm-câu-trả-lời-bằng-cách-nào)
      * [Prolog backtracking](#backtracking-trong-prolog)
   * [Prolog vs SQL](#4-prolog-vs-sql)
* [Phần B:](#phần-b)
   * [State transitions](#state-transitions)
   * [List](#list-iteration)
   * [Accumulator & Tail recursion](#accumulator-and-tail-recursion)
   * [Hạn Chế và Ứng dụng của Prolog](#ứng-dụng-và-một-số-hạn-chế)
   * [Prolog có đáng học không?](#prolog-có-đáng-học-không)

------------------

# __Phần A__

## __1. Khởi động__

Mình khởi động với một câu đố nhỏ:

Tui có cây phả hệ của nhà Nobita như sau:

<center><img src="{{ site.url }}/assets/prolog-intro/prolog-puzzle-family-tree.png"></center>

Hỏi:
* Ông Kataoka có đứa cháu ruột nào tên Tôm không?
* Bà Kataoka và bà Nobi có cùng những đứa cháu nào?

Nếu phải code, bạn sẽ giải 2 câu này và những câu tương tự về mối quan hệ trong gia đình bằng cách nào? Bạn sẽ chọn ngôn ngữ lập trình nào để code?

Nếu là tui của 6 tháng trước đây - công dân OOP Java gương mẫu miệt mài Leetcode, có lẽ tui sẽ nhồi thông tin trên vào các class rồi xào xào ra mấy cái tree/graph traversal functions để dùng. Tui ngày hôm nay đã gia nhập được thêm một vài công cụ và ngôn ngữ mới, thì thấy đích thị là 1 vấn đề được sinh ra để dành cho Prolog - bà  trùm trong nhóm ngôn ngữ lập trình logic. 

Để tui dùng Prolog giải nhé. Bạn sẽ thấy giải bằng Prolog dễ và ngắn gọn đến mức ngỡ ngàng.

2 câu hỏi đưa ra đều liên quan đến mối quan hệ *Grandparent - Grandchild*. Để trả lời, mình cần nối các mối quan hệ *Parent - Child* được cho sẵn. Mình chỉ cần liệt kê ra các thông tin này ra, trong Prolog gọi là **Facts**: 

```prolog
% Liệt kê facts về bố/mẹ - con theo format: parent_child(Parent, Child)
parent_child(nobisuke, tom).
parent_child(nobisuke, tep).
parent_child(nobisuke, nobita).
parent_child(tamako, tom).
parent_child(tamako, tep).
parent_child(tamako, nobita).
```
*Có tổng cộng 15 mối quan hệ Parent - Child. Code hoàn thiện tại [đây][nobita-family-tree-full].*

[nobita-family-tree-full]: https://github.com/ptmphuong/tuihoccode_demo_code/blob/main/prolog/intro/nobita_family_tree.pl

Để trả lời câu đầu: **Ông Kataoka có đứa cháu ruột nào tên Tôm không?**

Mình định nghĩa **Rule** sau để miêu tả mối quan hệ giữa Grandparent, Parent và Child:

```prolog
grandparent_grandchild(GrandParent, GrandChild) :-
    parent_child(GrandParent, Parent),
    parent_child(Parent, GrandChild).
```

Rule `grandparent_grandchild/2` có 2 variables chính là `GrandParent`, `GrandChild`. Ngoài ra, mình dùng thêm `Parent` nữa để bắc cầu. Nếu muốn chạy thử, bạn [full demo code][nobita-family-tree-full] này và cho vào [SWISH][swish.swi-prolog.org] (Prolog playground) chạy, sẽ cho ra kết quả như sau:

[swish.swi-prolog.org]: https://swish.swi-prolog.org/

<center><img src="{{ site.url }}/assets/prolog-intro/prolog-puzzle-family-tree-a1.png"></center>

Để trả lời câu tiếp theo: **Bà Kataoka và bà Nobi có cùng những đứa cháu nào?** Mình lại viết thêm 1 cái rule nữa, vận dụng `grandparent_grandchild/2` đã viết ở trên. Do tìm 2 bà chung 1 cháu, nên tui dùng variable `GrandChild` để bắc cầu.

```prolog
mutual_grandchildren(GrandParent1, GrandParent2, GrandChild) :-
    grandparent_grandchild(GrandParent1, GrandChild),
    grandparent_grandchild(GrandParent2, GrandChild).
```

<center><img src="{{ site.url }}/assets/prolog-intro/prolog-puzzle-family-tree-a2.png"></center>

Đơn giản dữ vậy? Prolog trả lời thông tin cho bạn bằng cách nào? Bình tĩnh, mời đọc tiếp. 

## __2. Prolog là gì?__

Khoảng những năm 60s 70s, khi chủ đề toán logic đang nóng hừng hực trong lĩnh vực toán học, các bác nghiên cứu tin rằng trí tuệ nhân tạo có thể tạo ra dựa trên một cơ sở kiến thức lớn và kết nối chúng bằng logic (<span style="color:blue">*</span>). Nhà nhà quan tâm và nghiên cứu chủ đề này, thế là đến năm 1972, Prolog chính thức ra đời, viết tắt cho programmation en logique (lập trình logic).

(<span style="color:blue">*</span>) *Đúng nhưng chưa đủ. Đến các năm 80 90 thì các bác bảo cần phải có số nữa. Ngày nay học ML/AI thì tất nhiên là phải học thêm rất nhiều xác suất thống kê.*

Code với Prolog, mình không cần định nghĩa một vấn đề cần giải bằng những bước nào, function không tồn tại trong thế giới Prolog. Ngược lại, mình chỉ cần khai báo ra đầy đủ **facts** và **rules**, còn lại để Prolog lo. Prolog dĩ nhiên vì vậy mà thuộc vào nhóm **Lập Trình Khai Báo - Declarative Paradigm**.

Cũng tiện note thêm, trong Prolog:
* Các từ có chữ đầu viết thường: *june*, *marge*, …  là **atom**. Atoms tựa như là literals vậy - giá trị mà nó thể hiện chính nó. 
* Các từ có chữ đầu viết hoa: *Parent*, *GrandParent*, …  là **variables** - tham số.

## __3. Prolog tìm kiếm câu trả lời bằng cách nào?__

Facts và rules sau khi được khai báo, Prolog sẽ lưu lại trong thư viện của mình - **Knowledge Base**. Khi nhận được câu hỏi mới ở quầy Question, Prolog sẽ chạy vào Knowledge Base, lục tìm đáp án và cho ra câu trả lời.

<center><img src="{{ site.url }}/assets/prolog-intro/how-prolog-works.png"></center>

Câu trả lời có thể ở dạng:
* true/false: xác nhận xem câu hỏi có đúng với thông tin Prolog nắm được không. *(a)*
* các giá trị đáp ứng yêu cầu của rule. *(b)*

<center><img src="{{ site.url }}/assets/prolog-intro/prolog-answer-types.png"></center>

## Backtracking trong Prolog

Ai từng bị leetcode ám ảnh như tui, mỗi lần thấy chữ backtracking trồi lên là lại nhăn trán nhăn mày. Tui bị ám ảnh đến nỗi đi ngủ mơ thấy mình nhảy lò cò từ node này qua node nọ trên graph. Nhưng từ khi quen dần với Prolog, khái niệm backtracking với tui nhẹ nhàng hơn hẳn.

Câu hỏi mang từ quầy Question vào, Prolog sẽ gọi là **Goal**. Từ Goal, Prolog sẽ tìm cách truy ngược từ goal -> facts trong Knowledge Base để tìm ra sự thật. Nếu có nhiều câu trả lời, Prolog sẽ sử dụng **Union** (phép hợp nhất) và chỉ trả lại tập trả lời đạt yêu cầu. 

<center><img src="{{ site.url }}/assets/prolog-intro/prolog-backtracking-1.png"></center>

Nếu Rule này chỉ đến Rule kia thì Prolog sẽ tiếp tục đi ngược lại, vừa đi vừa dựng thêm kiến thức trong Knowledge Base, truy tìm cho đến khi nào tận gốc. Nếu tìm thấy những Facts và Rules xung đột lẫn nhau thì sẽ trả lại ngay kết quả false.

<center><img src="{{ site.url }}/assets/prolog-intro/prolog-backtracking-2.png"></center>

Trường hợp goal có liên quan đến Recursion, thì Prolog sẽ truy ra đến Base Cases. Nếu không định nghĩa recursive chính xác thì xác định ăn timeout hoặc stack overflow. Tui sẽ nói nhiều hơn về recursion trong Prolog ở phần B khi mình XOAY. 

Zoom kỹ hơn vào chỗ này trong hình cách hoạt động của Prolog: 

<center><img src="{{ site.url }}/assets/prolog-intro/prolog-backtracking-unification.png"></center>

Từ đây, bạn có thể đoán tại sao dùng Prolog để trả lời câu đố khởi động dễ dàng đến như vậy không? 

Nếu sử dụng một ngôn ngữ imperative như Java, Python, Rust, mình sẽ phải tự code ra một thuật toán backtracking nào đó - tree dfs/bfs để sử dụng. Prolog rất tiện ở một chỗ là: bản thân Prolog là cả một bộ máy backtracking đã được tối ưu. Muốn sử dụng, mình chỉ cần cho facts và rules vào để Prolog chạy ra kết quả. Do đó, trong những trường hợp có nhiều dữ kiện và quy tắc cần sử dụng backtracking, Prolog là một ứng viên sáng giá. 


Có một câu hỏi tui thắc mắc trong thời gian mới làm quen với Prolog: Nếu cũng là ngôn ngữ truy vấn, thì Prolog với SQL khác nhau chỗ nào? 

## __4. Prolog vs SQL__

SQL và Prolog đều là 2 ngôn ngữ mạnh về truy vấn. 

Nếu nói theo thuật ngữ của Prolog - thế giới của facts và rules, thì SQL mạnh hơn khi truy vấn trong knowledge base có nhiều facts/data. Các thao tác quản lý data (storage, retrieval, projection) SQL rõ ràng là lợi hại hơn. 

Prolog mạnh hơn khi truy vấn trong knowledge base có nhiều rules. Rules này dẫn sang rules kia, và cả recursion nữa.

SQL thường được dùng trong server, Prolog thường được chọn dùng ở phía client. 

# __Phần B__

## __State Transitions__ 

Prolog không có function, nghĩa là cũng không có `return` statement. Để chuyển trạng thái của 1 logic object, mình đành dựa vào tính truy vấn của Prolog và sự linh hoạt của Variable trong Rule.

Ở ví dụ khởi động, mình dùng rule `grandparent_grandchild/2` để định nghĩa mối quan hệ giữa GrandParent, GrandChild.
```prolog
grandparent_grandchild(GrandParent, GrandChild) :-
    parent_child(GrandParent, Parent),
    parent_child(Parent, GrandChild).
 ```
Nếu muốn truy vấn xem GrandParent và GrandChild được kết nối bởi Parent nào, mình chỉ cần thêm vào Rule như sau:
```prolog
grandparent_grandchild(GrandParent, GrandChild, Parent) :-
    parent_child(GrandParent, Parent),
    parent_child(Parent, GrandChild).
```

Và truy vấn lại như sau: 
* `grandparent_grandchild(mrKaotaoKa, tom, Parent)` => `tamako`
* `grandparent_grandchild(mrKaotaoKa, akiyo, Parent)` => `false`

Trường hợp không tìm được Parent nào cả, Prolog sẽ chỉ trả lời false.

Nhìn ở khía cạnh rộng hơn, Variable có thể được pass ngay trong body của Rule, và tạo thành một chuỗi chuyển đổi trạng thái (a sequence of state transitions).

Một ví dụ khác tóm tắt một quy trình tối ưu như sau:
```prolog
program_optimized(Prog0, Prog) :-
    optimization_pass_1(Prog0, Prog1),
    optimization_pass_2(Prog1, Prog2),
    optimization_pass_3(Prog2, Prog).
```

Prog0 là chương trình ở trạng thái bạn đầu. Prog0 sẽ chạy qua 3 passes:
* pass_1 biến Prog0 thành Prog1
* pass_2 biến Prog 1 thành Prog2
* Và cuối cùng pass_3 biến Prog 2 thành thành phẩm Prog
* Prog được thêm vào trong Variable program_optimized để có thể truy vấn và trả về.

## __List iteration__ 
 
Prolog cũng không có for/while loop. Nên các thao tác liên quan đến Iteration, mình phải dựa vào recursion. Thao tác với List trong Prolog hệt như thao tác với Linked List vậy.

Ví dụ dưới đây để tìm **Length of a list**:
```prolog
% Base case - Length of an empty list is 0
list_length([], 0).

% Recursive case - Length of a list is 1 + the remaining of the list (everything but the first element)
list_length([_|Xs], L) :-
    list_length(Xs, N),
    L is N+1.
```
Kết quả: 
* `list_length([], N)` => N = 0
* `list_length([1, 1, 3], N)` => N = 3

Đôi điều đáng chú ý ở đây:
* Prolog sử dụng **Pattern matching** để match Rule của base case và các recursive cases. Thứ tự và vị trí của các Variables nên thống nhất để mình có thể dễ dàng dùng lại trong trường hợp cần query hoặc sử dụng cho state transition. 
* Trường hợp mình đã biết được atoms, ví dụ như empty list: `[]`, mình không cần phải định nghĩa Variable nữa, mà mình định nghĩa thẳng vào Rule luôn.

Thừa dễ xông lên, **reverse a list** làm thế nào?

Tương tự với cách sử dụng pattern matching ở trên, mình có thể viết Rule để xoay ngược list như sau
```prolog
% Base case: Reverse of an empty list or a list of 1 element is itself.
reverse( [] , [] ) .  
reverse( [X] , [X] ) .  

% Recursive case,  a list of length >= 1:
reverse([X|Xs], Reversed) :- 
  reverse(Xs, T),                % - recursive call - reverse the tail (DFS)
  append( T , [X] , Reversed)    % - append the head to the reversed tail.
```
Kết quả:
* `reverse([1, 2, 3], Reversed)` => Reversed = [3, 2, 1]

Cách viết trên không sai, nhưng mình có thể làm tốt hơn:
* *Time complexity:* List trong Prolog căn bản là linked list. Time complexity của `append` là O(N), mình phải đi từ đầu đến cuối đuôi của list để thêm dữ kiện vào. Thay vào đó, mình có thể sử dụng `prepend`, thêm dữ kiện vào đầu của list, với time complexity là O(1).
* *Tận dụng tail recursion:*
   * Rule `reverse/2` được viết theo lối **non-tail recursion**. Nghĩa là sau recursive call vẫn còn các bước tính toán nữa. Cách làm này bị một cái là tốn bộ nhớ, vì mình cần phải 1 - tính toán recursive call, 2 - tạm lưu kết quả recursive call, 3 - tính toán các bước sau đó, 4 - rồi mới được trả lại kết quả của rule. Hậu quả có thể dẫn đến overflow khi phải tính toán nhiều.
   * Thay vào đó, mình có thể tìm cách viết lại với **tail recursion** sao cho recursive call là bước trả về cuối cùng, để khi có kết quả recursive call, mình có thể trả về kết quả ngay lập tức mà không cần bước tạm lưu.

Sử dụng Accumulator, mình có thể thanh toán được 2 vấn đề trên.

## __Accumulator and Tail Recursion__

Mình dùng thêm 1 variable như là 1 trợ lý, trong trường này là 1 empty list:

```prolog
% using helper rule reverse_acc/3
reverse1(Original, Reversed) :-
  reverse_acc(Original, [], Reversed). % the empty list will be our accumulator
```

Khi gọi recursive calls, mình iterate qua list, vừa đi vừa tích lũy thêm vào cái list trợ lý này, nên được gọi là **Accumulator**.

```prolog
% reverse with an accumulator

% if the OriginalList is empty - this is where the process stops:
% our accumulator has already accumulated all elements, andand contains the reversed list we want.
reverse_acc([] , Reversed, Reversed).

reverse_acc([Head|Tail] , Accumulator , Reversed) :-     % if the list is non-empty, we reverse the list
   reverse_acc(Tail, [Head|Accumulator ] , Reversed).    % by recursion down with the head of the list prepended to the accumulator
```

Các bước reverse trông sẽ giống như vậy:
| Original List | Accumulator | Reversed List |
| --- | --- | --- |
| [1,2,3,4] | []           | []
| [2,3,4]   | [1]          | []
| [3,4]     | [2,1]        | []
| [5]       | [3,2,1]      | []
| []        | [4,3,2,1]    | []
| []        | []           | [4,3,2,1]

## __Ứng dụng và một số hạn chế__

#### __Hạn chế của Prolog__ ####

Mình search trên github với từ khóa `language:prolog` và tìm ra có khoảng hơn [10,000 repositories][prolog-on-github] sử dụng Prolog. Một con số không nhỏ, nhưng khá là khiêm tốn so với Java hoặc JavaScript - được sử dụng ở hơn 4 triệu repositories. 

[prolog-on-github]: https://github.com/search?q=language%3Aprolog

Model của Prolog xoay quanh việc tối ưu hóa cho DFS, backtracking, unification cho facts và rules. Tuy Prolog được coi là Turing Complete, nghĩa là những vấn đề các ngôn ngữ khác code được, Prolog cũng code được, nhưng viết ra thì có thể sẽ rất rườm rà. Với các ứng dụng lớn, DFS, backtracking có thể chỉ đóng một phần rất nhỏ; chưa kể các ngôn ngữ khác nếu cần thì cũng có thể tự implement được.

Ngoài ra, bản chất logic và declarative của Prolog không được thuận cách suy nghĩ của con người cho lắm, do đó số lượng người dùng, và support community cũng khó lòng mà cạnh tranh nổi với các ngôn ngữ imperative. 

#### __Ứng dụng của Prolog__ ####

Nói đi thì cũng có nói lại, tính năng của Prolog rất phù hợp với những công việc có liên quan đến pattern matching và backtracking như: *graph db engine, language parsing trees, expert systems,* … 

* 90%+ source code của **[Terminusdb]**[terminusdb-github] - graph database and document store được viết bằng Prolog.
* **IBM Watson** sử dụng Prolog để phân tích cú pháp của ngôn ngữ tự nhiên, hỗ trợ trong việc dịch từ ngôn ngữ người sang các thông tin có thể hiểu và phân tích được bởi Watson
* Các ứng dụng khác của Prolog đa phần được viết thành những chương trình nhỏ (dưới 100,000 lines of codes), là một mảnh ghép trong các ứng dụng lớn hơn.
* Ngoài ra, Prolog hiện vẫn đang được giảng dạy ở nhiều trường học. Ngoài mục đích nghiên cứu, thì toán logic vẫn căn bản vẫn là nền tảng của CS. 

[terminusdb-github]: https://github.com/terminusdb/terminusdb

## __Prolog có đáng học không?__

Nếu học để kiếm tiền thì *tui nghĩ* là không. Nhưng để thỏa đam mê hoặc trí tò mò thì có.
Tui thích học ngôn ngữ, đặc biệt là những ngôn ngữ bắt mình phải nghĩ lại 1 vấn đề đã biết theo một hướng hoàn toàn mới. Prolog là một trong những ngôn ngữ như vậy.
  

#### __Các nguồn học Prolog:__
* [Learn Prolog Now](http://www.let.rug.nl/bos/lpn//)
* [The Power of Prolog](https://www.metalevel.at/prolog)








