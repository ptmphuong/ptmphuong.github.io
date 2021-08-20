---
layout: post
title:  "Giải Thích Khái Niệm Lập Trình Cơ Bản 2 - PROGRAMMING PARADIGMS"
categories: cs-foundation
---

**Giải thích các khái niệm low-level, high-level programming languages, OOP và các progamming paradigms thường gặp**

Hello các bạn,

Về VN ăn tết mấy nay tui lỡ dở việc học hành T_T. Trước khi đi tiếp [mấy khoá tui đang theo][link-to-post-1] thì e khó mà bắt nhịp, nên tui nghĩ bụng ngồi viết chuỗi bài này để lấy đà học tiếp. (xin hứa)

Ở tập trước, tui giải thích về các thuật ngữ về [Máy tính nói chung][link-to-post-2], bao gồm các khái niệm về cách máy tính hoạt động. Nay tui tiến tới giải thích về **ngôn ngữ lập trình** và các **phong cách lập trình** nhé.

### __Programming Language & Natural Language (ngôn ngữ lập trình và ngôn ngữ tự nhiên__

**Programming language (ngôn ngữ lập trình)**, là ngôn ngữ con người dùng để giao tiếp với máy tính; cụ thể hơn là một loạt các chỉ dẫn mà con người dùng để ra lệnh cho máy tính làm. Bản chất của ngôn ngữ lập trình là thẳng thắn, 1 câu lệnh chỉ có đúng 1 ý nghĩa, từ đó máy mới có thể hiểu mà chạy.

Còn **Natural language / NP (ngôn ngữ tự nhiên)** là ngôn ngữ con người dùng để giao tiếp với nhau. **NP** được cho là ambiguous (mơ hồ), 1 câu nói có thể chứa nhiều hàm ý, do đó không đủ rõ ràng để máy tính có thể hiểu và thực hiện. 

<center><img src="{{ site.url }}/assets/post2/ngon-ngu-may-tinh.png"></center>

Ngày nay, ngành nghiên cứu **natural language processing/NLP (xử lý ngôn ngữ tự nhiên)** là một nỗ lực để máy tính hiểu được ngôn ngữ phức tạp của con người. Nỗ lực lớn nhất phải kể đến Google Translate với chất lượng dịch ngày một chuẩn và xịn. **NLP** kết hợp giữa **computer science, ngôn ngữ học và AI (trí tuệ nhân tạo)** và ti tỉ các công nghệ kỹ thuật hiện đại nói chung là lớn lao lắm, nên thôi mình lại trở về cái ao làng là căn bản lập trình nói tiếp nhé.

### __Low-level language & High-level programming language__

Trở về với 50 shades of ngôn ngữ lập trình.

**Binary** (đã giải thích ở [bài 1][link-to-post-1]) là **low-level programming language** (ngôn ngữ lập trình bậc thấp nhất) do binary gần với máy hơn, máy có thể trực tiếp hiểu các chuỗi số 0-.

Các ngôn ngữ lập trình nghe quen tai như Python, C, C++, Java, JavaScript, ... đều là những **high-level programming language** (ngôn ngữ lập trình bậc cao), do các ngôn ngữ này đều có hình thức gần với ngôn ngữ tự nhiên hơn. Những ngôn ngữ này được tạo ra để con người ngày một dễ dàng tiếp xúc và tương tác với máy tính.

> **Code = Instructions (hướng dẫn) = Program (chương trình) = App / Application (Ứng dụng) = Software (phần mềm)**

<center>Machine language <-------------------------------> Natural language</center>
<center>	Low-level PL				High-level PL</center>

#### __Programming Paradigms – phương pháp/mô hình lập trình__

Ngày nay có đến hơn ~700 ngôn ngữ lập trình. Vậy làm sao để biết sử dụng ngôn ngữ nào cho phù hợp với dự án của mình?

Bạn sẽ cần đầy đủ kiến thức về programming languages, paradigms và một rổ kinh nghiệm để làm chuyện này. Nhưng đơn giản nhất, mình có thể hình dung rằng có những ngôn ngữ phù hợp cho việc làm **web (web development), làm hệ thống (system), làm mobile (mobile app development)**, vv.

 Sở dĩ có sự phân chia như vậy, là vì ngôn ngữ lập trình có cách tư duy và những đặc tính để phục vụ những mục đích khác nhau. Dựa vào đó mà ngôn ngữ lập trình được chia ra thành nhiều **programming paradigms (mô hình/phương pháp lập trình).**

**Programming paradigms** có thể hiểu là tư duy của các ngôn ngữ lập trình. Với 1 vấn đề, các ngôn ngữ có tư duy hoặc paradigms khác nhau sẽ có cách tiếp cận vấn đề và giải quyết khác nhau. Cụ thể hơn là sự khác nhau trong cách khai báo, sử dụng syntax, các bước tính toán, vân vân.

Đây là các loại paradigms và mối quan hệ giữa các paradigms:

<center><img src="{{ site.url }}/assets/post2/types-of-paradigms.png"></center>

Trong bài viết này, tui sẽ chọn giải thích 4 khái niệm paradigms thường gặp nhất, đó là:


* **Imperative paradigm (lập trình mệnh lệnh)
* Object oriented paradigm (lập trình hướng đối tượng) 
* Declarative paradigm (lập trình khai báo)
* Functional paradigm (lập trình hàm)**

### __Đầu tiên, Imperative paradigm (phương pháp lập trình mệnh mệnh)__

Về định nghĩa, **Imperative paradigm là phương pháp lập trình dùng câu lệnh để thay đổi từng trạng thái của chương trình**.

Trạng thái huh? Bạn có thể nghĩ đến một chiếc công tắc: có 2 trạng thái đóng và mở. Khi bật công tắc lên, quạt đang ở trạng thái tắt chuyển sang trạng thái mở.

Còn trong lập trình, tui lấy ví dụ đơn giản là làm một phép toán cộng các số từ 1 tới 5 như sau:

```
public class Main
{
    int sum = 0;
    sum += 1;
    sum += 2;
    sum += 3;
    sum += 4;
    sum += 5;
    
    System.out.println("The sum is", sum); 
    //print-> The sum is 15

    return 0;
}
```
Ở đây từng câu lệnh để thay đổi trạng thái (statement) đều được liệt kê. Sau mỗi statement, trạng thái là giá trị của `sum` đều tăng lên. 

Một mẹo để nhớ về imperative paradigm: với phương pháp này, bạn phải mô tả cho máy tính cách làm (how to), cụ thể là từng bước thực hiện phải được liệt kê tận tình và tỉ mỉ tựa như 1 công thức nấu ăn vậy.

Để tui freestyle thử 1 đĩa chả giò ăn ngày tết theo phong cách imperative.

```
form nhanchagio
nhanchagio.Add(200gr groundpork, 200gr choppedshrimp, 2 eggs, 50gr ricenoodles, seasonings)
nhanchagio.Roll()
nhanchagio.Fry(3 mins)
nhanchagio.LetCool(60mins)
nhanchagio.Fry(7mins)
print nhanchagio

```

### __Object oriented paradigm / OOP (phương pháp lập trình hướng đối tượng__

**OOP** là 1 phương pháp thuộc **imperative paradigm**, vì vậy OOP cũng tập trung vào việc mô tả cho máy tính cách giải quyết vấn đề.

Riêng về **OOP**, đây là phương pháp lập trình lấy **Object (đối tượng)** làm đơn vị thao tác cơ bản. Mọi lối tư duy đều xoay quanh việc trình bày object và tương tác giữa các đối tượng đó. 

Mà **object** là gì? Lại lấy ví dụ nữa nào:

<center><img src="{{ site.url }}/assets/post2/oop-examples.png"></center>

Ở đây, sách là object chính.

Trong **1 Object**, ta có:

* **properties (đặc tính)** - những danh từ thuộc về sách, như thông tin của sách: tựa đề, tác giả, số trang, ...
* **methods (phương pháp)** - những động từ dành cho sách: đọc, mua, xuất bản, ...

Object mẹ có thể chia thành nhiều object con:
* 2 objects con là E-book và Paperback.

Lấy ví dụ trong lập trình để thấy rõ hơn object được trình bày và tương tác như thế nào nhé:

```
public class Main
{
	public static void main(String[] args) {
		Addition obj = new Addition();
		obj.num = 5;
		int answer = obj.addValues();
		System.out.println("The sum is = "+answer); //prints-> The sum is 15
	}
}

class Addition {
    int sum =0;
    int num =0;
    int addValues(){
        for(int i=1; i<=num;i++){
            sum += i;
        }
        return sum;
    }
}
```

Cũng cùng là ví dụ làm phép tính các số từ 1 tới 5. Ở đây, class `Addition` có:

* 2 properties: `sum` và `num`, đều được cho giá trị về số 0. 
1 method: `addValues()`, dùng để lấy giá trị `sum` sau khi làm các phép cộng.
Ngoài ra, trong class `Main`, mình cũng tạo 1 object mới là `obj`, thuộc class `Addition`. Sau đó, cho giá trị của `num` là 5, (để num lần lượt chạy từ 1 tới 5) và gọi method `addValues()` để thực hiện phép toán. 

OOP xuất hiện cực kỳ nhiều trong các tài liệu về lập trình. OOP còn bao gồm các khái niệm như **Class, Instances, Abstraction, Encapsulation, Inheritance, Polymorphism** tui sẽ cố thử dành trọn thanh xuân, à không, tập sau để làm rõ thêm hen.


Tạm đủ cho cặp đôi Imperative là OOP. Bây giờ mình qua một thế giới tư duy khác, Declarative và Functional.

### __Declarative Paradigm (lập trình khai báo)__

Bạn còn nhớ tấm hình phân loại và cấu trúc của các paradigm hồi nãy ở phía trên không? Nếu nhớ, bạn sẽ thấy rằng Declarative và Imperative tạo thành 2 trường phái đối lập lập trình. Mà chắc là chưa nhớ nổi đâu, tui paste lại hình dưới đây mình cùng ôn bài. 

<center><img src="{{ site.url }}/assets/post2/oop-examples.png"></center>

Nếu như trong imperative, bạn quan tâm tới cách giải quyết bài toán - how to do; thì trong declarative, bạn tập trung vào việc nói cho máy tính biết bạn muốn nhận được kết quả gì - what to do, cụ thể là chỉ việc khai quy tắc đầu vào và đầu ra, còn lại máy tính tự quyết.

	Declarative -> **what** you want done, given input and outout
	Imperative -> **how** you want it done, step by step

Microsoft có 1 [bài viết so sánh giữa imperative và declarative][microsoft-imperative-vs-declarative] rất hay và rõ ràng dành cho ai quan tâm.

### __Functional Paradigm (lập trình hàm)__

**Functional paradigm** là một nhánh của declarative, cũng chỉ tập trung vào chuyện what to do. 

Function là hàm số - là những công thức định sẵn nhằm thực hiện các yêu cầu tính toán chuyên biệt (nghe là thấy đậm mùi toán rồi).

Trong OOP, người ta thờ Object. Còn trong Funtional thì thời Function. Trong Functional paradigm là phương pháp lập trình lấy function là đơn vị thao tác cơ bản. Logic của phương pháp này xoay quanh việc trình bày function, tương tác giữa các function chủ yếu liên quan đến toán.

Trong Functional paradigm, dữ liệu không bị thay đổi trong hàm, đây cũng là khái niệm bất biến (Immutability) của phương pháp này. Ngoài ra, các lệnh như for loop, if/else cũng không cần dùng đến.

Làm luôn một ví dụ để xem nhé. Trong ví dụ này, nhiệm vụ của tui là đi tìm số nguyên tố (prime):

```
function isPrime(number){
 for(let i=2; i<=Math.floor(Math.sqrt(number)); i++){
  if(number % i == 0 ){
   return false;
  }
 }
 return true;
}
isPrime(15); //returns false
```

`isPrime()` là hàm chính để giải quyết nhiệm vụ. Trong đó, 2 hàm `Math.floor()` và `Math.sqrt()` là 2 hàm được sử dụng để giải bài toán nhanh gọn. 

`number` là input (dữ liệu đầu vào). `isPrime()` chạy xong sẽ trả về input ban đầu với kết quả `true` hoặc `false` tuỳ xem số đó có phải là số nguyên tố không. `number` hoàn toàn không bị tác động, thay đổi gì trong hàm `isPrime()` hết.

-

Đã giải thích xong 4 khái niệm. Tui kết bài bằng tiết mục Q&A tự biên tự diễn nhé. 

1. **Có học sơ qua Python, tui thấy bóng dáng của cả 4 cái paradigms trong python. Rốt cục Python là cái gì?**

Đa phần các ngôn ngữ lập trình đều có thể mang nhiều paradigms. Như Python cùng lúc có thể thực hiện 4 logic lập trình trên trong cùng 1 ngôn ngữ. 

Nếu một ngôn ngữ lập trình được chủ định thiết kế để phù hợp với nhiều paradigms, ta gọi đó là **multi-paradigm language (ngôn ngữ đa dụng)**

Những ngôn ngữ như JavaScript, Lisp, Ocalm, Scheme đều nặng về việc sử dụng function nên được gọi là "functional languages" tuy vẫn có lúc sử dụng variables và các lối tư duy của imperative.

2. **Đoạn giải thích functional paradigm, sao bên trên vừa bảo Functional không xài for loop, else/if mà ngay ví dụ vẫn có?**

Rất ít ngôn ngữ có thể áp dụng 100% 1 lối tư duy (nếu quyết tâm, thì chắc là được). Nhưng, bớt rảnh. Mục đích cuối cùng của việc lập trình vẫn là làm sao giải quyết vấn đề một cách hiệu quả nhất, miễn sao code dễ đọc, dễ hiểu thì việc kết hợp paradigms cũng vẫn ok mà.

Nếu bạn cảm thấy paradigms vẫn mông lung như một trò đùa, đừng lo. Hãy bắt tay học 1, 2 ngôn ngữ lập trình, sau đó làm bài tập hoặc chạy 1 project, khi đó bạn sẽ thấm được logic của ngôn ngữ đó, từ đó sẽ nhanh chóng nghiệm ra paradigms thôi. Cố lên!

[link-to-post-1]: https://tuihoccode.com/thoughts/2020/01/16/chia-se-kinh-nghiem-tu-hoc-lap-trinh-python-cho-nguoi-moi-bat-dau.html
[link-to-post-2]: https://tuihoccode.com/cs-foundation/2020/01/17/giai-thich-khai-niem-lap-trinh-co-ban-1-computer-basics.html
[microsoft-imperative-vs-declarative]: https://docs.microsoft.com/en-us/previous-versions/dotnet/netframework-4.0/hh323693(v=vs.100)?redirectedfrom=MSDN
