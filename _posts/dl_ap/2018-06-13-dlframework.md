---
layout: post
title: Deep Learning Next Generation
subtitle: ???.
tags: [tutorial, edge computing, deep learning]
comment: true
---

# Khi Deep learning gặp Edge computing

Nếu như những năm 2010 cụm từ "cloud computing" (tạm dịch là tính toán trên mây) xuất hiện dày đặc trên mặt báo và các hội thảo lớn nhỏ thì trong những năm gần đây, khái niệm “edge computing” (tạm dịch là tính toán ở rìa) đang ngày càng thu hút sự chú ý. Thật vậy, theo báo cáo của Gartner, một công ty chuyên về nghiên cứu và tư vấn công nghệ, edge computing sẽ bùng nổ trong 2 đến 5 năm tới (Hình 1). Trong bài viết này, chúng ta sẽ cùng nhau tìm hiểu sơ lược khái niệm edge computing, mối liên hệ giữa deep learning và edge computing, nguyên nhân dẫn đến sự bùng nổ của edge computing cũng như các ứng dụng hiện tại và tương lai của nó. Cuối cùng, một số nghiên cứu mới nhất về deep learning trên edge sẽ được giới thiệu sơ qua.

![Scene_text](/img/20180725/Hinh1.png) 
Hình 1 - Những công nghệ "hot" đang được phát triển. (Nguồn Gartner)

## 1.	Edge computing là gì?
Edge computing là một khái niệm dùng để chỉ việc xử lí các tác vụ được thực hiện trực tiếp trên các thiết bị di động, hay còn được gọi là các thiết bị edge. Đặc điểm của các thiết bị này thường nhỏ, gọn, và sử dụng ít năng lượng. Ngược lại với việc edge computing là cloud computing, nơi mà mọi thông tin từ các thiết bị phải được gửi về cloud để xử lí. Sau khi xử lí xong, cloud sẽ gửi trả kết quả về các thiết bị đó. 
 
Edge computing thật ra đã được ứng dụng phổ biến trong cuộc sống hàng ngày nhưng chúng ta có thể không để ý. Ví dụ như: 
* Camera an ninh thường nén video lại để tiết kiệm băng thông trước khi truyền về trung tâm. Chuẩn nén có thể là motion JPEG, H.264, hoặc mới nhất hiện nay là H.265. Nếu camera truyền video với tốc độ 24 frame/s và chất lượng full HD ở dạng thô, băng thông tiêu tốn sẽ lên đến 1.14 Gb/s (1920 x 1080 x 3 bytes x 24 frame/s = 142 MB/s = 1.14 Gb/s). Nếu video được nén lại theo chuẩn H.264, băng thông tiêu tốn khi này chỉ khoảng 10 Mb/s, tức là giảm khoảng 114 lần.  
* Điện thoại thông minh cho phép chúng ta thực hiện thanh toán tự động khi mua sắm. Các điên thoại khi này không bắt buộc phải được kết nối với máy chủ mà nó đóng vai trò như một gateway chứng thực người dùng. Các điện thoại thông minh còn có thể giúp quản lí sức khỏe của người sử dụng thông việc qua đo nhịp tim, số bước đi, lượng đồ ăn hàng ngày, …  

Nhìn chung, các thiết bị edge có khả năng trực tiếp xử lí một số tác vụ dựa vào các tài nguyên sẵn có của nó, thay vì phải gửi về cloud và đợi kết quả trả về. Nhờ đó, chúng ta có thể tiết kiệm đáng kể băng thông cũng như thời gian chờ xử lí. Mặc dù đã được sử dụng trong một thời gian dài, nhưng nó chỉ mới được đề cập nhiều trong những năm gần đây. Hãy cùng nhau tìm hiểu lí do trong phần kế tiếp sau đây.

## 2.	Tại sao edge computing lại "hot" trong những năm gần đây?
Nếu chúng ta tưởng tượng edge computing như một quả tên lửa, thì ba động cơ chính của nó là công nghệ bán dẫn (semiconductor), Internet-of-Things (IoT), và machine learning mà nổi bật là deep learning (Hình 2).
 
![Scene_text](/img/20180725/Hinh2.png) 
Hình 2 – "Nhiên liệu" của quả tên lửa edge computing

### a)	Sự phát triển của công nghệ bán dẫn (semiconductor): 
Các chip hiện đại ngày nay không chỉ chứa nhiều cores mà còn được tích hợp các bộ xử lí chuyên dụng như bộ xử lí nén và giải nén video, các bộ xử lí mã hóa giải mã cho Wifi và Bluetooth, các bộ chuyển đổi tín hiệu từ số sang tương tự và ngược lại. Các chip này được gọi tên chung là SoC (System-on-chip hay Hệ thống trên chip). Bên cạnh việc tăng hiệu năng, giá thành của chip SoC ngày càng giảm. Nhờ vậy, các chip này ngày càng được sử dụng rộng rãi. 

Ví dụ: chip SoC trên board Raspberry Pi Zero W (Hình 3) không chỉ tích hợp 1-GHz ARM core và 512 MB bộ nhớ RAM mà còn có bộ nén và giải nén full HD, 802.11 b/g/n wireless LAN, và Bluetooth năng lượng thấp. Tuy nhiên, giá thành của một board chỉ vào khoảng 10 USD.   
 
![Scene_text](/img/20180725/Hinh3.png) 
Hình 3 – Board Raspberry Pi Zero W. (Nguồn: Internet)

Nói tóm lại, sự phát triển của công nghệ bán dẫn, đặc biệt là khả năng tính toán ngày càng tăng của các chip SoC, đã tạo điều kiện cho edge computing có thể được thực hiện dễ dàng hơn.

### b)	Sự phát triển của IoT:
Trong thế giới ngày nay, chúng ta đã không còn xa lạ việc các thiết bị điện tử có thể giao tiếp trực tiếp với nhau hoặc thông qua các servers. Ví dụ, trong nông nghiệp thông minh (Hình 4), các thiết bị dùng để thu thập nhiệt độ, độ ẩm, ánh sáng, phân bón, … được kết nối mạng với nhau để từ đó người nông dân biết được tình trạng cây trồng và có chế độ chăm sóc phù hợp. Tùy theo quy mô và yêu cầu cụ thể mà các mạng này có thể chứa từ vài trăm đến vài chục nghìn thiết bị như vậy. Nhờ vào công nghệ vi mạch phát triển, giá thành chip ngày càng rẻ, nên việc triển khai hàng chục nghìn thiết bị không phải là một việc quá khó khăn.
 
![Scene_text](/img/20180725/Hinh4.png) 
Hình 4 - Ứng dụng của IoT trong nông nghiệp. (Nguồn: Internet)

Tuy nhiên, khi một loạt thiết bị cùng gửi trả tín hiệu về cùng một lúc sẽ dẫn đến nguy cơ nghẽn mạng. Các thông tin đã gửi đi có thể sẽ không đến được thiết bị mong muốn. Khi đó, mỗi thiết bị sẽ phải gửi đi gửi lại cùng một dữ liệu nhiều lần, dẫn đến việc tiêu tốn năng lượng. Nếu như các thiết bị này có thể xử lí tín hiệu thu thập được và chỉ gửi đi các thông tin cần thiết (ví dụ chỉ gửi thông tin nhiệt độ khi nhiệt độ cao hơn ngưỡng cho trước), chúng ta sẽ tiết kiệm được băng thông, từ đó tiết kiệm được năng lượng tiêu tốn. Nói cách khác, sự phát triển của IoT gắn liền với sự cần thiết của edge computing.

### c)	Sự phát triển của deep learning. 
Mặc dù đã ra đời từ rất lâu, machine learning, mà đặc biệt là mạng neural chỉ mới thật sự nổi lên từ năm 2012 sau màn trình diễn đầy ấn tượng của AlexNet. Lần đầu tiên, một mạng deep neural chứng tỏ được hiệu năng vượt trội so với các phương pháp machine learning truyền thống dùng rút trích đặc trưng bằng tay. Thành công của deep learning còn có sự góp phần đáng kể của công nghệ bán dẫn, mà cụ thể là các GPUs. Thật vậy, nhờ có GPUs mà thời gian training cho các mạng deep neural được rút ngắn đi nhiều lần so với việc dùng các CPUs truyền thống.  
 
![Scene_text](/img/20180725/Hinh5.png) 
Hình 5 – Kết quả cuộc thi ImageNet Challenge từ năm 2010 đến 2015. (Nguồn: M. Verhelst et al., Embedded Deep Neural Network Processing: Algorithmic and Processor Techniques Bring Deep Learning to IoT and Edge Devices,” IEEE Solid-State Circuits Magazine, vol. 9, no. 4, pp. 55-65, 2017)

Một trong những xu hướng hiện tại là làm cho các thiết bị IoT ngày càng thông minh nhờ vào machine learning hoặc deep learning. Cùng nhau xem lại các ví dụ ở Mục 1, chúng ta có thể thấy:

* Camera ngày càng thông minh hơn: thay vì chỉ truyền video về server, camera trong các xe thông minh có thể phát hiện và nhận dạng vật cản, từ đó đưa ra các cảnh báo hoặc ngừng khẩn cấp. Các cảnh báo này phải được xử lí trong thời gian cực nhanh nên thông tin thu nhập cần phải được xử lí tại edge, thay vì tại server (Hình 6). Ví dụ, một xe chạy tốc độ 60 km/giờ = 16.7 m/giây, hay cứ 1 giây di chuyển được 16.7 m. Độ trễ xử lí khi này phải tính bằng mili-giây chứ không thể nào bằng giây được.
 
![Scene_text](/img/20180725/Hinh6.png) 
Hình 6 – Sự kết biệt về độ trễ giữa edge và cloud computing. (Nguồn: Internet)

* Các điện thoại thông minh ngày nay có thể được bảo mật bằng vân tay, giọng nói, mống mắt, … Các xử lí này được thực hiện trực tiếp trên chip SoC trong điện thoại. Ngoài ra, các trợ lí ảo như Google Now có thể trả lời truy vấn mà không cần kết nối với server. Nếu các thiết bị này gửi về server xử lí, tùy theo chất lượng kết nối mà thời gian chờ có thể tính bằng vài chục giây, gây ra nhiều bất tiện cho người dùng. 
* Các thiết bị kiểm soát bệnh liên quan đến não hoặc tim cũng cần xử lí trực tiếp. Ví dụ, người bênh động kinh cần phải đeo một thiết bị chuyên dụng bên người. Nếu não người bệnh bị nhiễu loạn, các cơn co giật sẽ xuất hiện. Lúc này các thiết bị sẽ phải tự động phát hiện và phát ra các xung điện kích vào não để triệt tiêu các cơn co giật. Các cơn co giật này đặc biệt nguy hiểm khi người bệnh đang lái xe hoặc làm các công việc có tính chất nguy hiểm. Do vậy, các thiết bị cần phải có độ trễ trong xử lí cực thấp, thường dưới 1 giây.

Nhìn chung, sự tiến bộ vượt bậc của công nghệ bán dẫn cũng như sự bùng nổ của IoT và deep learning trong thời gian gần đây đã tạo điều kiện cho edge computing phát triển. Theo dự đoán của Gartner (Hình 1), edge computing đang là xu hướng phát triển trong vòng 5 năm tới. Các nghiên cứu cho edge computing, đặc biệt là deep learning trên các thiết bị edge do vậy cũng sẽ tăng theo. Trong phần dưới đây, chúng ta sẽ cùng điểm qua một số nghiên cứu mới nhất cho deep learning trên thiết bị edge. 

## 3.	Các hướng nghiên cứu cho deep learning trên edge

### a)	Cải tiến về model: 
Deep learning truyền thống đòi hỏi nhiều tính toán trong khi các thiết bị edge thường bị giới hạn bởi năng lượng (thời lượng pin) cũng như khả năng xử lí (CPU và RAM thường không quá cao). Do vậy, các model cần phải được tối ưu theo hướng nhỏ gọn và giảm yêu cầu tính toán. Các cải tiến hay dùng gồm:

* Train các weight ở dấu chấm tĩnh (1, 2, 4, 8, 16-bit fixed point) thay vì dấu chấm động (32-bit floating point).  
* Lượng tử hóa các weight để giảm kích thước model.
* Do ReLU và dropout ngày càng được sử dụng rộng rãi, các mạng neural ngày càng thưa (sparse). Khi này các weight bằng 0 sẽ ngày càng nhiều. Xử lí các phép nhân với số 0 hoặc nén các weight trở nên cấp thiết.
* 	 …

Các cuộc thi về model deep learning công suất thấp cũng thu hút nhiều sự chú ý, ví dụ như cuộc thi Low-Power Image Recognition Challenge (https://rebootingcomputing.ieee.org/lpirc). Một trong những đội thắng giải năm nay đã cải tiến model MobileNet của Google để giảm khối lượng tính toán cũng như giảm năng lượng tiêu tốn.

### b)	Cải tiến về hardware:
Các chip SoC truyền thống thường không được thiết kế tối ưu cho các ứng dụng deep learning dẫn đến thời gian tính toán sẽ tăng không đáp ứng được thời gian thực. 

Năm 2016, nhóm nghiên cứu của GS. Vivienne Sze tại đại học MIT công bố và demo Eyeriss, chip xử lí CNN đầu tiên trên thế giới, tại hội nghị ISSCC (được coi như là “Oscar” của công nghệ bán dẫn thế giới). Chip này cho hiệu năng vượt trội so với GPU dùng trong các điện thoại di động, trong khi tiết kiệm năng lượng hơn gấp nhiều lần. Kể từ đó, hằng năm có ít nhất 10 đến 20 chip liên quan đến deep learning được giới thiệu tại ISSCC. Apple cũng vừa thương mại hóa chip SoC có xử lí IPCore deep learning trong năm 2017.     

## 4. Kết luận
Bài viết này mong muốn cung cấp đến bạn đọc các khái niệm cơ bản về edge computing, nguyên nhân dẫn đến sự bùng nổ của deep learning trên các thiết bị edge cũng như các ứng dụng hiện tại và tương lai. Các nghiên cứu về hướng này đang và sẽ rất hot trong thời gian tới. Các bài viết tiếp theo sẽ cung cấp kĩ hơn các nghiên cứu cũng như phương pháp triển khai deep learning trên các thiết bị edge. 

Nguyễn Xuân Thuận.
