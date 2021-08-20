---
layout: post
title:  "Lập Trình Hướng Đối Tượng (Object Oriented Programming / OOP) Là Gì?"
date:   2020-02-03 07:58:23 -0700
categories: cs-foundation
---

**Lập trình hướng đối tượng (OOP) là gì? "Đối tượng" là cái chi chi? Việc gì phải hướng vào đó?**

Lập trình hướng đối tượng / Object oriented programming / OOP hẳn là một trong những khái niệm mơ hồ nhất đối với những bạn vừa bắt đầu học lập trình. Khái niệm này thường xuyên được nhắc đến trên các tài liệu, blog, sân chơi diễn đàn lập trình. Nhưng tui, mới học code - đang làm quen với variables, if-else, loops, function các kiểu, vậy Object là cái bíp gì? Rồi class, objects, methods làm nghề bíp gì? Và còn Abstraction, Inheritance, ... đóng vai trò bíp gì ở đây? Bíp bíp bíp bíp bíp bíp ?!$#$#%@ 

Câu cuối cùng ở trên là tóm tắt trạng thái xoắn cực đại của tui trước khi làm bài viết này. Sau khi luyện công từ tầm 30 bài viết trên mạng, tui mạn phép xuất ra linh đan là bài viết đơn giản hóa khái niệm OOP dưới đây, bao gồm:

* Tại sao phải có OOP?
* Object-oriented là gì?
* Giải thích 4 đặc tính của OOP 
* Class là gì? Ví dụ về Class và Object.

### __Tại sao phải có OOP?__

Trước khi giải thích vấn đề, hãy cùng nhìn vào cách tui - 1 con amateur chính hiệu - viết code. Đại loại trông nó như thế này:

```
main program:
   ======================
   ======================
   if ===================
      ===================
   ======================
   while ================
      ===================
      ===================
   ======================
   for ==================
      ===================
   ======================
   ======================
   if ===================
      ===================
      ===================
   else =================
      ===================
   ======================
...
```

Code suôn, được viết logic thẳng từ trên xuống dưới và cho chạy thì ra được kết quả. Cũng ngon đấy nhưng lối logic này chỉ dùng được khi tui có tầm 50 dòng code đổ lại. Nếu chương trình phát triển lên tới một cây tre trăm (dòng) code, thì chắc chắn cái đống code này trở thành một mớ bòng bong, có nhiều đoạn code lặp đi lặp lại, người khác đọc vào hẳn sẽ bị lạc. Nghĩ bụng, tui cần một cách tư duy và sắp xếp code thông minh hơn xíu. 

Theo lẽ tự nhiên, tui tiến đến tới một programming paradigm (phương pháp/tư duy lập trình) căn bản nhất, đó là procedural programming (phương pháp lập trình thủ tục). Trong phương pháp này, tui cắt đống code của mình thành nhiều procedure (thủ tục) và function (hàm số).Trong đó:

* **Procedure - thủ tục** là tập hợp một đoạn code liên quan đến nhau, và được đặt một cái tên chung - là tên của procedure.
* Còn **function - hàm số** là một dạng procedure có trả lại một giá trị khi kết thúc.

Nhờ vào **procedural programming**, code của tui gọn gàng và dễ quản lý hơn. Nếu muốn xài lại một đoạn code nào đã được đưa vào procedure thì chỉ cần gọi tên nó ra chứ không cần copy lại nữa. Lúc này, code của tui sẽ trông như sau:

```
main program:
   ======================
   ======================
   call fred
   ======================
   if ===================
      ===================
   x := bob()#define function
   ======================
   while ================
      ===================
   ======================
   call eric
   ======================
   ======================
   ======================

procedure fred: #define procedure
   ======================
   ======================

procedure eric:
   if ===================
      ===================
   ======================

function bob:
   ======================
   return ===============
```

Phù, tốt hơn khá nhiều so với đoạn code đầu rồi đấy. Tuy nhiên, nếu dự án này một lớn dần, lượng data và function trong code tăng dần lên thì tui sẽ lại bắt đầu gọi loạn xạ, và procedural paradigm cũng không ăn thua. Lúc này, tui cần sắp xếp những đoạn code theo một cái gì đó cụ thể hơn, và một trong những giải pháp ở đây là sử dụng Object-oriented (hướng đối tượng). Vậy,... 

### __Object-oriented - hướng đối tượng là gì?__

Trong chương trình hướng đối tượng của mình, tui sắp xếp các đoạn code của mình vào nhiều object; cũng y như là dọn hết đồ đạc trên bàn cho vào nhiều ngăn tủ vậy. Mỗi Object đều bao gồm: 

* **data / properties (đặc tính)** - những biến, dữ liệu, cấu trúc dữ liệu, tất tần tật liên quan đến dữ liệu của chương trình.
* **functions / methods (phương pháp)** - những công thức, hàm số để áp dụng cho các dữ liệu trên.
* và đừng quên cái tên của object đó để gọi nó khi cần.

<center><img src="{{ site.url }}/assets/oop/oop-la-gi-1.png"></center>

Việc bao gồm data và functions này cũng chính là giải thích cho đặc tính đầu tiên của OOP: **Encapsulation (tính đóng gói)**. Encapsulation cụ thể là đóng gói những data và function liên quan đến nhau vào một Object. Đơn giản là vậy.

* Nhưng mục đích sâu xa hơn của đặc tính này là để bảo mật function và data. Data có thể được tạo và cất giấu kín ở dạng private trong các object. Phương thức này còn có tên gọi chuyên môn là **Data Hiding**. 

Với **Encapsulation**, code trở nên gọn ghẽ hơn. Những gì không cần thiết để trên bàn thì ta sắp xếp vào ngăn kéo. Trong chương trình, Data và function nào liên quan đến nhau thì ta gom lại cất vào object. Cất xong rồi, nhìn vào chương trình bạn chỉ cần quan tâm đến việc object này có tính năng gì và phục vụ mục đích nào, mà không cần tập trung vào các chi tiết nhỏ nhặt bên trong. Việc đơn giản hóa vấn đề này chính là đặc tính Abstraction (trừu tượng hóa) của OOP. Trừu tượng hóa giúp ích khá nhiều trong việc bảo trì chương trình, các chi tiết nhỏ nhặt không đụng tới thì làm sao mà sai được, đúng hem?

Nói đến Abstraction, Alan Kay - cha đẻ chính thức của OOP còn tâm niệm rằng:

> “[…] the whole point of OOP is not to have to worry about what is inside an object. Objects made on different machines and with different languages should be able to talk to each other […]” ~ Alan Kay

> Nghĩa là " sử dụng OOP thì không cần phải phiền muộn về những chi tiết bên trong Object. Các object dù được tạo bởi cái loại máy khác nhau, với nhiều ngôn ngữ khác nhau, nhưng đều nên có thể tương tác với nhau được."

Đó là tầm nhìn của Alan Kay về OOP - một mô hình lập trình bao gồm một chuỗi các mạng lưới object tương tác và phối hợp với nhau để giải quyết vấn đề. "The big idea is messaging":

<center><img src="{{ site.url }}/assets/oop/oop-la-gi-2.jpeg"></center>

Alan định hình OOP như là một mạng lưới máy tính vậy, trong đó các server truyền thông tin và tương tác với nhau.

* Còn tui thì tưởng tượng OOP chẳng khác gì một cái sơ đồ nhân sự. Mỗi người là một object. Ai cũng đều có dữ liệu  (data) và các task cần làm (methods/functions). Để vận hành công ty một cách mượt mà, các sếp sẽ giao việc cho từng người, sau đó giao việc cho nhiều người hoặc nhiều team phối hợp với nhau.

<center><img src="{{ site.url }}/assets/oop/oop-la-gi-3.png"></center>

* Đối với bạn, bạn biết mình có gì và cần làm gì. Về đối ngoại, bạn cần biết ai làm nghề gì, bộ phận nào phục vụ chức năng gì là đủ, ai hơi đâu mà để ý đến từng task đồng nghiệp đang làm, hay chi tiết team người ta đang họp cái mô, nhỉ. Nhưng nhìn từ trên xuống, mạng lưới được sắp xếp càng chặt chẽ, thì hiệu suất công việc càng cao. 

Một mạng lưới chặt chẽ là một mạng lưới đồng nhất và tránh sự trùng lặp - **Dont Repeat Yourself (DRY)**. OOP sử dụng đặc tính **Inheritance (tính kế thừa)** để đạt được hiệu suất tối đa nhất. Với những object có nhiều điểm tương đồng, những điểm tương đồng đó đều được vào một Parent, còn những thứ khác nhau thì bỏ vào Child. Child có thể sử dụng tất cả những element trong parent và kết hợp với những element mình có.

* Cũng giống như cách phân bổ làm việc của một team vậy. Team marketing chẳng hạn, bạn làm Digital (online) và bạn làm offline dĩ nhiên là có phạm vi công việc khác nhau, nhưng đều hưởng chung các task làm việc như run_ad(), write_content(), report(), vân vân. Ở đây, parent là Marketing, còn child là Digital_M và Traditional_M. 

<center><img src="{{ site.url }}/assets/oop/oop-la-gi-4.jpeg"></center>

**Inheritance (tính kế thừa)** và **Polymorphism (tính đa hình)** thường đi song song với nhau. Polymorphism là từ mỹ miều cho cụm từ many forms - nghĩa là đa hình. Đa hình ở đây có thể hiểu là tính linh động của các child và parent object trong OOP. 

* Marketing vừa là Digital, và vừa là Traditional. Khi team chạy campaign, các team con sẽ tự điều phối để chạy trên các kênh phù hợp.

### __Ơ, thế còn class là gì?__

Nếu bạn đã hiểu Object rồi thì Class dễ lắm. Muốn tạo được Object, và data, function, child object các kiểu trong đó, thì trước tiên bạn phải tạo Class. Class là một cái Object rỗng không có dữ liệu gì hết. Có class rồi bạn mới tạo từng Object và gán dữ liệu vào đó.

<center><img src="{{ site.url }}/assets/oop/oop-la-gi-5.jpeg"></center>

Nãy giờ nói nhiều rồi, xem thử pseudo code của tui theo kiểu oop không? Còn cái ví dụ này nốt nữa thôi là tui xong.

```
main program:
   marketing_manager= new marketing  # tạo object digital_marketing từ class marketing
   digital_marketing.run_ad(500) # chạy dự án/campaign với ngân sách 500$
   ======================
   ======================
   if ===================
      ===================
   marketing_manager.report()
   ======================
   ======================
   while ================
      ===================
   ======================
   marketing_manager.report()
   ======================
   ======================

define class marketing:
data:
   ======================
   ======================
method spend_budget:
   ======================
   ======================
method report:
   ======================
   ======================
end class marketing
```

Dưới đây là một số tài liệu hay về OOP để các bạn tham khảo thêm nhé:

Tiếng Anh:

* [(Video) Object-oriented Programming in 7 minutes][video-object-oriented-programming-in-7-minutes]
* [What is Class and Object in Java OOPS?][what-is-class-and-object-in-java-OOPS]
* [How to explain object-oriented programming concepts to a 6-year-old][how-to-explain-object-oriented-programming-concept-to-a-6-year-old]
* [Python Object-Oriented Programming (OOP): Tutorial][python-object-oriented-programming]

Tiếng Việt:

* [OOP là khỉ gì?][oop-la-khi-gi]

[video-object-oriented-programming-in-7-minutes]: https://www.youtube.com/watch?v=pTB0EiLXUC8&t=75s&ab_channel=ProgrammingwithMosh
[what-is-class-and-object-in-java-OOPS]: 
[how-to-explain-object-oriented-programming-concept-to-a-6-year-old]: https://www.freecodecamp.org/news/object-oriented-programming-concepts-21bb035f7260/
[python-object-oriented-programming]: https://www.datacamp.com/community/tutorials/python-oop-tutorial
[oop-la-khi-gi]: https://kipalog.com/posts/OOP-la-khi-gi-
