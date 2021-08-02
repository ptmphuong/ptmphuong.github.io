---
layout: post
title:  "Bà cụ non Rust và ông chú Python"
date:   2020-08-17 06:46:00 -0700
categories: programming-languages
---
**Cảm nhận tự học Rust từ một người chỉ biết Python.**

Xin báo cáo: tui tự học Rust được 1 tháng rồi. Từ Python đến Rust - chà, phải nói đây là một chặng đường khó nhưng vô cùng đúng đắn để hiểu hơn về các khái niệm nền tảng về Computer Science. Dưới đây, tui mở màn chuỗi bài về Rust bằng chia sẻ cảm nhận học ban đầu nhé. 

À, xin 30s nói về background của tui. Trước khi đến với Rust, tui tự mần Python được gần 1 năm - thân thuộc với Pandas, Numpy, Matplotlib, có bắt tay làm project bằng Dash (để theo dõi Corona), và Django (chiếc blog này nè). Gần đây, khi tìm hiểu thêm về các đề tài về kiến thức nền như cấu trúc máy tính, cách hoạt động của memory, tui thấy mình bơi một chút trên biển C và bây giờ thì đang đắm đuối bên Rust. 

### __1. Giới thiệu bà Rust.__

**Rust** hello world từ 2010, mới 10 tuổi thôi nhưng cho tui ấn tượng của một ngôn ngữ rất cứng cáp:

* các tài liệu để học và đọc đều có tổ chức,
* cấu trúc ngôn ngữ chặt chẽ,
* cộng đồng Rust cũng đều rất chững chạc.

Trong đầu tui, Rust trông y hệt 1 bà cụ non.

Rust được sinh ra ở lò **Mozilla**, cùng lò với trình duyệt Firefox. Sứ mệnh của Rust là để sánh vai cùng ông bà hoàng C và C++ trong vấn đề quản lý tài nguyên, và thậm chí còn qua mặt họ trong tính an toàn - memory safety nữa. Được tạo ra bởi các ông mụ bà mụ đầu ngành, Rust là nổi tiếng là một ngôn ngữ khó nuốt bởi Rust đòi hỏi người dùng phải hiểu các khái niệm thấp của máy tính, cùng các khái niệm đặc thù của Rust nữa. Đấy, cộng đồng Rust vững và chững là vì đã vượt qua những khổ ải này rồi.

Nghĩ đi cũng phải nghĩ lại, ôi ông chú Python nhà mình. Ông chú đã hơn 30 tuổi rồi nhưng vẫn còn trẻ trung phết. Nếu Python xuất hiện trong hình hài con người, tui tưởng tượng Python sẽ là một ông chú mặc áo sơ mi hawaii cùng chiếc quần jeans thụng bạc màu, mặt mày hớn hở cười tươi, tay thì kéo một chiếc vali siêu bự một đống đồ nghề (là các thư viện ấy) tích trữ mấy chục năm nay. Chưa hết, ông chú Python còn có hẳn 1 cái fanclub chiếm đa phần là các nam thanh nữ tú bắt đầu đến với lập trình, tui cũng ở trỏng nè.

<center><img src="{{ site.url }}/assets/rust-vs-python/rust-vs-python.jpeg"></center>
<center>[Nguồn ảnh][https://leftoversalad.com/c/015_programmingpeople/
[programming-languages-sketches]</center>

Bà cụ non Rust và ông chú Python, mỗi bên đều có một cá tính thú vị. 

### __2. Phân biệt căn bản giữa Python và Rust: Interpreted vs Compiled Language__

**Python là ngôn ngữ thông dịch - interpreted language**. Khi viết xong chương trình bằng Python, mình chỉ cần bấm nút Build hoặc Run thì chương trình sẽ bắt đầu chạy đúng không? Dưới bề mặt, code Python của bạn sẽ được dịch qua mã máy line by line trong khi chương trình đang chạy.

**Rust là ngôn ngữ biên dịch -  compiled language**. Sau khi viết xong chương trình, code của bạn sẽ được dịch toàn bộ qua mã máy bởi Compiler. Sau khi dịch xong toàn bộ, chương trình của bạn mới được chạy.

<center><img src="{{ site.url }}/assets/rust-vs-python/rust-vs-python-interpreted-vs-compiled.jpeg"></center>
<center>Nguồn ảnh: tui chứ ai.</center>

Lúc này, có 1 nhân vật mới xuất hiện: anh chàng Compiler - đệ tử của bà Rust nhưng khó tính không thua kém. Mới gặp thì cười cười vậy thôi chứ code thử vài dòng là sẽ thấy ngay độ dữ dằn của ảnh nhé.

<center><img src="{{ site.url }}/assets/rust-vs-python/rust-vs-python-compile-your-code.png"></center>
<center>[Nguồn ảnh][https://www.slideshare.net/LizBaillie/rustconf-2016-illustrated-adventure-guide-65894363]</center>

### __3. Cái khó khi học Rust__

Từ Python nhảy thẳng qua học Rust, mèn đéc ơi nó khó. Thử nhìn khác biệt ở cá tính và độ tuổi giữa Rust và Python thôi là cũng đủ thấy phê rồi.

Với Pyhon, bạn không cần phải lo về vấn đề quản lý dữ liệu khi khai báo biến. Nghĩa là gì? Nếu bạn không biết thì hẳn là chú Python đã bao bọc bạn nhiều quá đấy! Mỗi khi khai báo dữ liệu, chú Python sẽ giúp bạn phán đoán loại dữ liệu và đặt vào memory giúp bạn. Anyway những thứ đó chú Python lo, việc của bạn là tập trung 100% vào logic giải quyết vấn đề. 

Bà Rust không chiều bạn ngọt như chú Python đâu. Bạn phải hiểu cách hoạt động của Memory (Stack và Heap dùng như thế nào), và nắm được những luật của Rust khi (như Borrow and Ownership) để khai báo và sử dụng dữ liệu đúng cách. Đừng hòng khua tay múa chân từa lưa, Compiler sẽ xuất hiện và dập liên hoàn error.

Ví dụ dưới đây để so sánh giữa Python và Rust. Công việc cần làm là: 1. Khai báo String x. 2. Gán y qua x

<center><img src="{{ site.url }}/assets/rust-vs-python/rust-vs-python-variable-ownership.jpeg"></center>
<center>Python vs Rust khi khai báo String</center>

* Với Python - hình trái , bạn có thể gán dữ liệu từ `x` qua `y` và sử dụng tùy thích. Cách sử dụng ở đây là print nó ra.
* Với Rust - hình phải, khi viết `let x = y`, bạn đã chuyển Ownership (quyền làm chủ dữ liệu) của dòng String từ `x` qua `y`. Lúc này, Compiler sẽ chặn bạn khỏi nỗ lực print `x` - 1 biến rỗng.

Khi viết Python, nếu có vấn đề, tui thường khua tay múa chân (hơi bẩn 1 tý) nhưng luồn lách là qua khỏi. Mặt khác, đồ nghề ông chú Python thì bao la phương pháp, thư viện có sẵn cho bạn xài. Bí quá thì mình lên hỏi Stackoverflow, 5’ sau đã có trợ giúp, mà nếu là Python thì thực ra những câu hỏi của bạn đều đã được hỏi và trả lời từ lâu rồi. Còn với Rust, nếu cần cầu cứu Stackoverflow thì hãy chuẩn bị tinh thần là ngồi chờ và mong người trả lời cho bạn nhé. 

Những lúc khó khăn như thế, bạn sẽ nhớ chú Python biết bao. Nhưng đừng nản chí, bà Rust có nhiều trò hay ho lắm đấy.

### __4. Cái lợi khi học Rust__

Học Rust, bạn mới có cơ hội thấy thế giới thật. Và bạn sẽ được trao rất nhiều quyền!

Quyền làm quen với Heap và Stack - 2 cô gái vàng trong làng Memory. Dựa vào đó, bạn có quyền quản lý  liệu của mình. Thích tiết kiệm memory thì mình mượn (borrow) bằng pointer, sang thì mình clone hẳn data để xài riêng.

Cùng vấn đề gán String ở trên, bạn có thể chọn Borrow hoặc Clone tùy nhu cầu để không gặp lỗi - quan trọng nhất là dòng 3 nhé..

<center><img src="{{ site.url }}/assets/rust-vs-python/rust-vs-python-borrow.jpeg"></center>

Những cách làm này đều có thể tạo ra sự khác biệt về chất lượng của chương trình ở quy mô lớn. Đây là sự linh động mà bạn không được sở hữu ở Python. 

Quyền tạo ra các loại dữ liệu đặc thù sử dụng struct và enums, cần thì gán thêm cá tính cho tụi nó bằng traits. Hay ho lắm. Còn với flow control, ngoài `if` statement, thì bạn còn có thể chọn xài `match`, hay `if let`. Khi áp dụng đúng hoàn cảnh, code trông sẽ gọn gàng hơn hẳn. 

<center><img src="{{ site.url }}/assets/rust-vs-python/rust-vs-python-if-syntax.jpeg"></center>
<center>So sánh syntax của `if` statement và `match` trong Rust.</center>

Thêm nữa là quyền được gặp cả OS để chạy Concurrency và Asynchronous - hiểu gọn là phân luồng cho nhiều công việc chạy cùng nhau cùng lúc. Nắm được các bí kíp này, chương trình có thể chạy nhanh hơn gấp nhiều lần. (khái niệm Concerrency này cũng có thể được vận dụng ở C, tuy nhiên Rust được thiết kế để chạy an toàn hơn - như đã hứa trong sứ mệnh ra đời).

<center><img src="{{ site.url }}/assets/rust-vs-python/rust-vs-python-performance.jpeg"></center>
<center>So sánh performance của các ngôn ngữ lập trình, sử dụng nhiều đề bài khác nhau.</center>
<center>Nguồn ảnh: [https://julialang.org/benchmarks/]</center>

Từng bước một, bạn sẽ vỡ lẽ ra những khái niệm bậc thấp trước đây được chú Python bao bọc. Cẩn thận đấy, String và List không ngây thơ như bạn đã từng biết đâu!

### __5. With great power comes great responsibility__

Câu này tui không biết dịch. Nhưng đại loại là nên chú ý: quyền càng nhiều thì nghĩa vụ càng lớn.

**Borrow, Ownership và Lifetimes** là 3 luật căn bản bạn có nghĩa vụ tuân theo để nắm được Rust. (Ở đây tui nói sơ thôi , sâu lắm nên có dịp viết riêng 1 bài sau, nha)

3 luật này được tạo ra nhằm phục vụ mục đích lớn lao nhất của Rust: Memory Safety (tránh tràn/overflow bộ nhớ, hoặc để chương trình tìm đến địa chỉ rỗng trên memory rồi bị sập, ...)

Trong Rust:

* Tất cả dữ liệu đều cần được phân rõ chủ quyền - theo đạo luật Ownership. Mỗi dữ liệu đều thuộc 1 chủ - duy 1 chủ duy nhất.

```
fn main() {
    let mut a = vec![1, 2]; 
    //a is the owner of the list vec![1,2]
    //mut is mutable, meaning the list can be changed later
}
```

* Ai muốn mượn dữ liệu thì tuân theo đạo luật Borrow - mỗi lần chỉ cho phép 1 người mượn - nghĩa là nếu đã có người mượn rồi thì không ai khác có thể mượn nữa. Đạo luật này khoan dung cho phép được tráo đổi đồ khi mượn :)) Nếu chủ tuyên bố ok, đây là hàng có thể tráo: mut a. Lưu ý, khi đang tráo hàng thì không ai khác được vào xem hay can thiệp nhé (read or write).

```
fn main() {
    let mut a = vec![1, 2];

    let b = &mut a; //b borrows the list from a
    b.push(3); //b adds 3 to the list

    println!("{:?}", a); //b's done with the job. It's inferred that b has returned the list to a.
    // The output here is vec![1, 2, 3]
}
```

* Mỗi Owner đều có 1 tuổi thọ - Lifetimes. Sau khi hoàn thành nhiệm vụ thì phải ra đi thôi.  Khi Owner ra đi, thì dữ liệu thuộc owner đó cũng đi theo.


```
fn main() {
    let mut a = vec![1, 2];

    let b = &mut a; 
    b.push(3); //b is last seen here. b's lifetime is ended now.

    println!("{:?}", a); //a is last seen here. a's lifetime is ended now.
}
 
```
Đấy, nếu không còn đóng góp gì nữa thì sẽ bị đào thải thôi. Chú Python đã bao bọc bạn khỏi những khắc nghiệt này. Thôi thì tin tốt là bạn không cần phải tự tay đi dọn xác của những owner đã ra đi (gặp ông bà C/C++ là bạn phải malloc để đi hốt từng xác đấy). Bà Rust là một người bạn tốt, bả sẽ giúp bạn tự động giải phóng (free) những linh hồn ấy thông qua Ownership system. Việc của bạn là đừng khi không mà đến tìm mấy địa chỉ ma (null pointer) đó thôi. Thời gian đầu không biết thì hãy chuẩn bị tinh thần ăn mắng thường xuyên từ Compiler nhe.

<center><img src="{{ site.url }}/assets/rust-vs-python/rust-vs-python-compile-your-code.png"></center>
<center>Nguồn ảnh: [https://www.slideshare.net/LizBaillie/rustconf-2016-illustrated-adventure-guide-65894363]</center>

### __6. Kết thân với Compiler__

Cộng đồng Rust hay đùa với nhau thế này:

* Q: What's the answer to most questions in Rust?
* A: COMPILER ERRORS. 

Hài nhưng rất thật. The Rust Compiler nổi tiếng trong việc khó tính và vô - cùng - bảo - thủ.  If it compiles, it works. Trong sách học Rust, compiler còn tự tuyên bố rằng nếu gặp lỗi - đặc biệt nếu liên quan đến memory safety thì compiler thà quăng error nhầm còn hơn bỏ sót. 

Tuy nhiên, thật lòng mà nói thì compiler rất chi tiết trong việc chỉ ra lỗi sai và gợi ý cách sửa lỗi.  Bảo thủ và annoying đến thế, nhưng compiler error message được rất nhiều Rustaceans tín nhiệm. Và tui cũng tiết kiệm được khá nhiều câu hỏi Stackoverflows nhờ vào việc bám sát vào những messages này. 

### __7. Bắt đầu học Rust từ đâu.__

Tài liệu Học Rust:

- Nếu bạn đang thắc mắc "Chỉ biết mỗi Python thôi thì có học Rust được không?" Ơ, thế đứa nào đang viết bài này? Tuy nhiên, nếu bạn chưa có kiến thức về memory, chịu khó detour học [CS50] nhé. Thầy sẽ sử dụng C căn bản để hỗ trợ giải thích. Kiến thức này sẽ bổ trợ rất nhiều cho bước tiếp theo. 
- Đọc [sách Rust] - đây là Bible học Rust, sách rất hay, mạch lạc, gần gũi và là tất cả những gì bạn cần để hiểu về Rust. 

Theo dõi tin tức mới nhất của Rust:

- This week in Rust - newsletter cập nhật tin tức của Rust và cộng đồng mỗi tuần
- Rust Blog - blog chính thức của Rust

Tất cả những nguồn đề cập trên đều miễn phí hết nha!

Cuối cùng, xin đính kèm thành tích của Rust để bạn lấy động lực học Rust nào. Chắc hẳn bạn cũng tò mò có gì trong ngôn ngữ lập trình được yêu thích nhất liền 5 năm trên Stackoverflow?

<center><img src="{{ site.url }}/assets/rust-vs-python/rust-most-loved-language.png"></center>
<center>Nguồn ảnh: [https://insights.stackoverflow.com/survey/2020#technology-most-loved-dreaded-and-wanted-languages-loved]</center>

Phù cuối cùng cũng viết xong. Ai đã đọc đến đây thì xin chân thành cảm ơn và kính chào tạm biệt! … cho đến bài tiếp theo.
[https://leftoversalad.com/c/015_programmingpeople/]: https://leftoversalad.com/c/015_programmingpeople/
[https://www.slideshare.net/LizBaillie/rustconf-2016-illustrated-adventure-guide-65894363]: https://www.slideshare.net/LizBaillie/rustconf-2016-illustrated-adventure-guide-65894363
[https://julialang.org/benchmarks/]: https://julialang.org/benchmarks/
[CS50]: https://online-learning.harvard.edu/course/cs50-introduction-computer-science?delta=0
[sách Rust]: https://doc.rust-lang.org/book/title-page.html
[https://insights.stackoverflow.com/survey/2020#technology-most-loved-dreaded-and-wanted-languages-loved]: https://insights.stackoverflow.com/survey/2020#technology-most-loved-dreaded-and-wanted-languages-loved
