---
layout: post
title:  "Các nhà nghiên cứu nghĩ gì về thời kỳ ủ bệnh của Covid-19?"
date:   2020-04-07 09:54:00 -0700
categories: project
---

**Chia sẻ cách làm và kết quả 3 ngày làm lao công dọn dẹp dataset gồm 52,000 bài viết học thuật về nCoV.**

Hi mọi người,

Gần đây Kaggle - cộng đồng data hùng hậu nhất thế giới đang dồn lực vào các challenge liên quan đến nCov-19 trong nỗ lực đẩy lùi dịch bệnh này. Tui có loanh quanh đọc các thảo luận và code của một số bài tham gia. Nói chung khá là thú vị khi đọc những giải pháp về 1 vấn đề mình biết và quan tâm. 

Cá nhân tui rất tò mò về vũ khí nguy hiểm nCoV này - đó là khả năng ủ bệnh của nó, nên cũng thử sức bơi trong 1 dataset gồm hơn 52,000 bài viết nghiên cứu, lặn ngụp để tìm câu trả lời cho riêng mình. Dưới đây là kết quả 3 ngày làm lao công dọn dẹp mớ data này.

Tui hy vọng tìm được câu trả lời cho 2 câu hỏi sau:

* Thời gian ủ bệnh của covid-19 **trung bình** là bao lâu?
* covid-19 có thể ủ bệnh **tối đa** bao lâu?

Dưới đây tui sẽ trình bày về dataset, phương pháp xử lý data, và cuối cùng - dĩ nhiên là đáp án. Độc giả nào chỉ quan tâm tới đáp án cuối cùng thì hãy nhắm mắt, vuốt thật mạnh 10 lần sang phải, nhầm, xuống dưới để đọc phần **3. Findings** nhé.

### __1. Đôi điều về CORD-19 dataset và challenge.__

__Dataset__

Có tên là [COVID-10 Open Research Dataset (CORD-19)][kaggle-cord-19-dataset], dataset tổng hợp tất cả các bài viết học thuật (scholarly articles) về nCoV và các dịch bệnh liên quan. Dataset này được tạo và cập nhật bởi các tổ chức nghiên cứu hàng đầu trên thế giới cùng Nhà Trắng.

[kaggle-cord-19-dataset]: https://www.kaggle.com/allen-institute-for-ai/CORD-19-research-challenge

<center><img src="{{ site.url }}/assets/covid-incubation/kaggle-cord-19.png"></center>
<br>

Số lượng bài viết được cập nhật up-to-date (theo tui để ý là hàng tuần). Trong lần cập nhật gần nhất thì tui đã tải về được 52,097 bài viết có đầy đủ nội dung (full-text). Mỗi bài được lưu dưới dạng file `.json` và trông như thế này này (bên trái). Ngoài ra dataset còn đính kèm 1 file `metadata.csv` siêu bự (bên phải) gồm các thông tin điểm của bài viết như `number id`, `license id`, `ngày công bố`, `link bài viết`. Chiếc file csv siêu bự, dùng excel thử chỉnh 1 ly là đi mất 1 phút cuộc đời.

<center><img src="{{ site.url }}/assets/covid-incubation/cord-19-data-files.png"></center>
<br>

### __Kaggle challenge:__

Trong challenge này, Kaggle kêu gọi các nhà khoa học và chuyên gia AI phát triển *bộ công cụ khai thác văn bản (text mining)* cho dataset này, với mục đích giúp ngành y tế nhanh chóng tổng hợp kiến thức từ tất cả các nhà nghiên cứu trên thế giới đã biết về ncov-19 cùng các dịch bệnh liên quan, từ đó dự đoán và đẩy lùi bệnh dịch.

Nghe ghê hông, dĩ nhiên không phải là tui rồi. Tui chưa thạo 2 bộ môn Machine Learning và Natural Language Processing cần thiết để giải quyết vấn đề trên. Nhưng nhà có gì xài nấy. Đang thực hành python, tui cũng có ít đồ nghề có thể lôi ra để dùng:

* Thư viện pandas: dùng để tổng hợp, cắt xén, truy suất và phân tích dữ liệu.
* Công cụ regex (viết tắt cho Regular expression): dùng để nhận diện cú pháp của ngôn ngữ, hỗ trợ tự động nhận diện và lọc ra thông tin tui cần tìm.
OK, đã lên đồ xong, bắt tay vào làm việc thôi. 

### __2. Phương pháp xử lý__

__Bước 1: Tổng hợp__

Bộ dataset tui sử dụng dưới đây được **cập nhật vào ngày 4/4/2020.**

Đầu tiên, tui match thông tin các paper từ `.json` files cùng `.csv` file để có trọn vẹn thông tin của từng bài viết; và kamehamehaaaa tui có 1 `dataframe siêu-to-khủng-lồ`, sẵn sàng để truy cập, lọc và cắt xén dần.

 `Dataframe siêu-to-khủng-lồ` chứa nội dung của 52,097 bài viết. Nhưng ngoài những thông tin về ncov-19, trong đây còn bao gồm các bài viết về các dịch bệnh liên quan. Do đó, mình cần tiến hành bước tiếp theo. 

__Bước 2: Cắt xén__
Những bài viết về nCoV chắc chắn phải có chứa chữ **nCoV** hoặc các tên gọi của con virus này, đúng không? Do đó, ở đây tui sẽ chỉ chọn ra các bài viết phù hợp điều kiện này.

* `covid_terms`: "covid-19", "covid 19", "covid-2019", "covid 2019", "2019-ncov", "ncov-2019", "wuhan virus", "wuhan coronavirus", "wuhan pneumonia", "sars-cov-2", "sars-cov2".
Và hiện tui cũng chỉ quan tâm đến thời gian ủ bệnh của nCoV này, nên từ danh sách trên, tui cũng chỉ chọn ra những bài viết có đề cập đến chữ "ủ bệnh": "incubation".

Một yếu tố khá thiên thời địa lời cho tui đó là chữ *"ủ bệnh - incubation"* là một chữ rất đặc thù khi nói về thời kỳ ủ bệnh của nCov. Thông thường ý này sẽ được diễn tả bằng cụm từ *incubation period.*
> ví dụ: *"The median incubation period was estimated to be...",  "a case with an incubation period of 27 days has been known". Do đó, ở đây tui chỉ lọc các bài viết có chữ "incubation".*

Cuối cùng, tui cũng loại luôn các bài viết được công bố trước năm 2020 và các bài viết không có ngày công bố.

Lượng bài viết được cắt xén như sau:

<center><img src="{{ site.url }}/assets/covid-incubation/ncov-articles-filter.png"></center>
<br>

Có thể thấy là chỉ khoảng 5% số bài viết nói về ncov phải không? Lần cắt xén đầu tui không đặt đủ điều kiện để lọc kỹ. Kết quả cuối cùng trả về thấy 1 bài viết báo cáo thời gian ủ bệnh trung bình tới tận 20 ngày. Hốt hoảng, tui đọc paper để xác nhận lại rồi mới biết đó là thời kỳ ủ bệnh trung bình của sốt rét. Đó là 1 pha hú vía.

Khuyết điểm của phương pháp cắt xén dựa vào cụm từ như trên mà không can thiệp tới machine learning, là việc tui có thể đã cắt đi cả những dữ liệu phù hợp. Tuy nhiên, với project này tui chọn phương án thà giết sai còn hơn bỏ sót.

### __Bước 3: Truy tìm câu trả lời__

Với 488 bài viết còn lại trong tay, tui tiếp tục đi tìm câu trả lời về thời gian ủ bệnh trung bình và tối đa của con virus.

__3.1 Thời gian ủ bệnh trung bình - Average Incubation Period__

Tui dự đoán các từ được sử dụng khi diễn tả thời gian trung bình như sau: 

* `average_terms`: "mean", "average"

Cạnh đó, tui sử dụng **regex** để cắt nội dung của từng bài viết thành:

* compound sentences - ngắt nhau bởi dấu chấm câu và xuống dòng. Sau đó, thành
* simple sentences - ngắt nhau bởi dấu phẩy.
* trong simple sentence, tui cắt ra số ngày là digit trong cụm "{digit} days" nếu simple sentence có xuất hiện các cụm từ của average_terms, cùng chữ "incubation"
* nếu 1 bài viết trả nhiều hơn 1 kết quả, tui chỉ giữ lại 1 kết quả cuối cùng, với giả định về cuối thường là kết luận của bài viết.

Demo kết quả **tìm thời gian ủ bệnh trung bình của ncov** tựa như sau:

<center><img src="{{ site.url }}/assets/covid-incubation/mean-incubation-demo1.png"></center>
<br>

Bằng cách này, tui lọc ra được **99 kết quả**. Sau khi tự verify bằng cách dò từng kết quả cho thấy cách làm này giúp tui được số ngày ủ bệnh trung bình chính xác 89% trong tổng số kết quả trả về. (mừng muốn chết). 

Các kết quả không đúng/không phù hợp thường có 3 lý do:

* A. có nội dung không liên quan, không chứa nội dung tui cần tìm. Ví dụ:
    * we estimated that the length of isolation in the high risk population will decrease from two weeks to an average of 7 days which is within the range of the average incubation period. 
* B. câu mơ hồ biểu đạt không rõ nghĩa. Ví dụ:
    * the average incubation period is between 2 and 21 days
* C. trong simple sentence có chứa nội dung tui cần tìm, nhưng có cách biểu đạt phức tạp nên tui dò ra sai ngày.
    * the average incubation period has changed from 7 days determined in january to 3 days estimated recently, which means 2019-ncov infected people are more likely to show symptoms.
        * kết quả của tui: 7 days, kết quả đúng: 3 days
    * they also estimated mean incubation and contagious periods of 5 and 11 days, respectively. 
        * kết quả của tui: 11 days, kết quả đúng: 5 days

### __3.2 Thời gian ủ bệnh tối đa - The Longest Incubation Period__

Tương tự như trên, tui cũng vận dụng phương pháp ngắt câu và tìm từ trong câu để tìm thời gian ủ bệnh tối đa.

Ở đây, tui dự đoán các từ liên quan đến tối đa như sau:

* `longest_terms`: "range", "ranging", "ranged", "longest", "up to", "maximum"

Một điểm khác trong việc chọn số ngày tối đa, tui chọn số ngày cao nhất trong những ngày trả lại để có kết quả đúng mong muốn hơn.

<center><img src="{{ site.url }}/assets/covid-incubation/longest-incubation-result-demo.png"></center>
<br>

Với các điều kiện trên, tui nhận được **54 kết quả cho thời gian ủ bệnh tối đa**, trong đó nhận diện đúng số ngày 83%.

Lý do của kết quả sai cũng tương tự như khi tìm average. 

Ngoài ra, các từ thuộc `longest_terms` đa phần đều kém trực tiếp hơn `average_terms`. Ví dụ, trong kết quả trả về, tui nhận phải kết quả của *"interquatile range"* (độ trải giữa dùng trong toán thống kê) thay vì đơn thuần là *"range"* (phạm vi) mà tui cần tìm.

Để tổng hợp kết quả để biểu diễn trên graph, tui sẽ bỏ các kết quả sai thuộc mục A. không liên quan, B. câu mơ hồ, không rõ nghĩa. Với C kết quả nhận diện sai ngày, tui sẽ cập nhật kết quả đúng

 Nhìn lại số lượng kết quả và độ chính xác:

<center><img src="{{ site.url }}/assets/covid-incubation/word-search-results.png"></center>
<br>

### __3. Findings__

Voilà. Đã đến phần findings. Ai đã vuốt mạnh 10 lần để xuống đây nói tui nghe? Không nói tui dò google analytics cũng biết được nghe chưa. 

__Thời gian ủ bệnh trung bình__

<center><img src="{{ site.url }}/assets/covid-incubation/ncov-average-incubation-result.png"></center>
<br>

Như vậy **thời gian ủ bệnh trung bình của nCoV theo các nhà nghiên kíu rơi vào khoảng 5-6 ngày.**

Có 1 chi tiết tui thắc mắc ban đầu khi nhận được kết quả đó là có đến 29 bài viết báo cáo số ngày trung bình là **5.2 ngày**? Tại sao không phải là 5, là 6, mà lại là một con số không chẵn 5.2 ngày? Tui rà và đọc sơ các bài viết thì có 3 yếu tố sau, và bạn đọc cũng nên lưu tâm khi tham khảo kết quả trên của tui.

1. Các bài nghiên cứu về nCoV đến thời điểm này đa phần đều dựa trên các trường hợp mắc bệnh trong thời kỳ đầu ở bệnh dịch, đó là ở Trung Quốc, cụ thể hơn là ở tỉnh Hubei.
2. Nhiều bài nghiên cứu cùng thuộc một journal, nghĩa là cùng 1 lò thường cho chung 1 kết quả. Nếu cái lò đó đăng nhiều bài viết hơn sẽ làm cho số lượng kết quả đó tăng nhiều hơn.
3. Các bài viết có thể đề cập (refer) lẫn nhau, mục đích là để so sánh, khẳng định lại, hoặc để đưa ra kết luận cho 1 luận đề khác chẳng hạn. Trong trường hợp này, theo tui nghĩ nếu số liệu được referred thì độ tin cậy của số liệu đó cũng tốt hơn. 5.2 ngày là số ngày ủ bệnh trung bình được tính toán độc lập bởi ít nhất 3 bài viết: (i) [Early Transmission Dynamics in Wuhan, China, of Novel Coronavirus–Infected Pneumonia][link-study-1], (ii) [The incubation period of 2019-nCoV from publicly reported confirmed cases: estimation and application][link-study-2], (iii) [Evolving epidemiology of novel coronavirus diseases 2019 and possible interruption of local transmission outside Hubei Province in China: a descriptive and modeling study][link-study-3]

[link-study-1]: https://www.nejm.org/doi/10.1056/NEJMoa2001316
[link-study-2]: https://www.medrxiv.org/content/10.1101/2020.02.02.20020016v1
[link-study-3]: https://www.medrxiv.org/content/10.1101/2020.02.21.20026328v1

Ngoài ra, các sample size của các paper đều khác nhau. Có bài viết sử dụng sample size lớn hơn 1,000 người và có những bài viết đề cập đến 1 ca nhiễm đặc biệt nào đó. Do sự hạn chế của dataset, và phương pháp của tui nên tui không tiêu chuẩn hóa được số liệu này. Mong quý độc giả thông cảm và lưu ý dùm.

__Thời gian ủ bệnh tối đa của nCoV__

Việt Nam vừa thông báo [người nhiễm nCoV ủ bệnh những 23 ngày][23-day-incubation-period-case-in-vn], nhưng ca ủ bệnh trên lâu nhất trên thế giới đến nay là bao lâu?

[23-day-incubation-period-case-in-vn]: https://vnexpress.net/phat-hien-nguoi-nhiem-ncov-sau-23-ngay-den-bach-mai-4080322.html

<center><img src="{{ site.url }}/assets/covid-incubation/ncov-longest-incubation-result.png"></center>
<br>

55 ngày. naaniiiiiii. Đây cũng chính xác là phản ứng của tui lúc đầu khi nhìn thấy con số này và đã nghĩ chắc tui đã lấy phải kết quả tào lao. Nhưng tin buồn cho mọi người đây là 1 kết quả có thực. 
> "Fever (153, 77.6%) was the most common presentations, following cough (89, 45.2%) and weakness (29, 14.7%), respectively. Other less common symptoms were sore throat (11, 5.6%), shortness of breath (10, 5.1%), and muscle ache (9, 4.6%, Table 2). However, 3 patients without any complaints were detected by chest CT scan. Among all those patients, the average days from exposure to symptom onset was 6.14±9.27days. The longest incubation period was 55 days. 48 patients were accompanied with underlaying illness, including cardiovascular (24.4%) and cerebrovascular diseases (4.6%), endocrine system diseases (9.1%), chronic renal disease (1.5%), malignant tumor(1.5%), and digestive system diseases (1.0%), nervous system diseases. Considering vital sign and CT manifestations, 56 patients were admitted to intensive cure unite （ICU）, and 141 patients were transferred to general isolation wards." by [Clinical features and outcomes of 197 adult discharged patients with COVID-19 in Yichang, Hubei][a-research-case-in-hubei]

[a-research-case-in-hubei]: https://www.medrxiv.org/content/10.1101/2020.03.26.20041426v2

Thông thường các bài viết đều cho rằng thời gian ủ bệnh của nCoV có phạm vi từ 0-14 ngày. Cũng không ít trường hợp (đa phần ở Trung Quốc) kết luận là từ 0-24 ngày. Nhưng theo câu hỏi của tui đặt ra ban đầu, thì **55 ngày - thời gian ủ bệnh lâu nhất của nCoV tính đến nay** chính là câu trả lời.

Xỉu.

Đừng chủ quan, hãy rửa tay thường xuyên và đeo khẩu trang nha mọi người.

### __Lời kết__

Phù, cuối cùng cũng viết xong. Nếu quá dài, xin lỗi người đọc vì đây là lần đầu tiên tui thực sự thả và tự bơi trong 1 real-world dataset bự và khó nên cũng có đôi chút phấn khởi với kết quả nhận được. Từ ý định ban đầu là "explore", đến lúc nhận được tập kết quả đầu tiên với quá nhiều dữ liệu sai và tưởng như không thể hoàn thành đòi hỏi tui phải suy nghĩ hoài về cách giải quyết, và cuối cùng cũng tìm được một số thông tin khá thú vị từ project này. Cảm giác thật toẹt vời vì lâu rồi mới có 1 project cuốn tui ngày đêm tới mức vậy.

Phần code xử lý theo phương pháp trên tui đã đăng lên trang [github][my-github] của tui. Có phần nào sơ suất, rất mong nhận được ý kiến đóng góp, góp ý của quý độc giả. Nếu được yêu mến, có thể tui sẽ viết thêm 1 bài blog về cách triển khai code gà của tui.

[my-github]: https://github.com/ptmphuong/cord-19/

Đến đây là hết, tui-out.
