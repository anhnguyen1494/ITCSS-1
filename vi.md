## ITCSS: MÔ HÌNH CSS MỞ RỘNG VÀ BẢO TRÌ ĐƯỢC
bởi Lubos Kmetko ngày 10 tháng 2 năm 2016 
### Làm thế nào để tạo css có thể mở rộng và bảo trì được? Đó là mối quan ngại của mọi Front-end developer. ITCSS là một câu trả lời.

Năm ngoái khi chúng tôi bắt đầu lên kế hoạch thiết kế lại [HEROized](https://www.heroized.com/) và trang Xfive.co mới,Tôi đã tìm một mô hình CSS cho phép dễ dàng phát triển trang web và bảo trì hơn nữa.

[CSS Modules](http://www.sitepoint.com/understanding-css-modules-methodology/) khá là mới và lạ ở thời điểm đó và Tôi đã lưu tâm rằng sự giống nhau [Atomic Design](http://patternlab.io/) chemistry để lại một chút nhân tạo. Rồi tôi biết đến [Roberts’s](https://csswizardry.com/)  ITCSS trong số ra tháng 6 năm 2015 của  [net magazine](https://www.creativebloq.com/web-design/manage-large-scale-web-projects-new-css-architecture-itcss-41514731) và ngay lập tức đã yêu thích cách tiếp cận CSS đơn giản xuống thế này.

### ITCSS là gì?
ITCSS viết tắt của Inverted Triangle CSS và nó giúp bạn tổ chức lại các tệp css trong dự án theo cách bạn có thể **xử lý** tốt hơn (không phải lúc nào cũng dễ dàng xử lý) vấn đề về CSS như **global namespace, cascade and selectors specificity.**.
ITCSS có thể được sử dụng với bộ tiền xử lý hoặc không cần chúng và tương thích với CSS phương pháp luận như BEM, SMACSS or OOCSS.
Một trong những nguyên tắc chính của ITCSS là nó tách CSS codebase thành một số phần nhỏ (được gọi là layers), có dạng hình tam giác ngược:
![inverted triangle](https://other.media/wp-content/uploads/2017/01/itcss_2.png)
layers này như sau:
- Settings - được sử dụng với bộ tiền xử lý và chứa font,định nghĩa màu sắc,vv...
- Tool - các mixins và hàm được xử dùng trên toàn cục.Điều quan trọng là không đưa ra bất kỳ CSS nào trong 2 lớp đầu tiên.
- Generic - thiết lập lại and/or bình thường hóa styles, định nghĩa kích thước hộp, vv. Đây là layer đầu tiên tạo ra CSS thực tế.
- Elements - tạo mẫu cho các phần tử HTML trống (like H1, A, etc.). Các trang này đi kèm với kiểu dáng mặc định từ trình duyệt để chúng tôi có thể xác định lại chúng ở đây.
- Objects - bộ chọn các lớp cơ bản được xác định bởi các mẫu thiết kế không được trang trí, ví dụ đối tượng truyền thông được biết đến từ OOCSS
- Components - các thành phần UI cụ thể. Đây là nơi phần lớn công việc của chúng tôi diễn ra và các thành phần UI của chúng tôi thường bao gồm các đối tượng và thành phần
- Utilities - các tiện ích và các lớp trợ giúp với khả năng ghi đè bất cứ thứ gì đi trước trong tam giác, ví dụ. Ẩn lớp trợ giúp
Hình tam giác cũng cho thấy các phong cách được trình bày bằng các bộ chọn được sắp xếp trong CSS kết quả: từ các kiểu chung chung đến các kiểu rõ ràng, từ các bộ chọn có độ đặc hiệu thấp đến những kiểu cụ thể hơn (nhưng vẫn không quá cụ thể, không cho phép ID) và những cái có ảnh hưởng lớn đến những cái ít hơn.
![inverted triangle](https://other.media/wp-content/uploads/2017/01/itcss_1.png)
Tổ chức CSS như vậy sẽ giúp bạn tránh Specificity Wars và được đại diện bởi [a healthy specificity graph](https://jonassebastianohlsson.com/specificity-graph/)
### Tài liệu
Chỉnh sửa 10/27/2016: TCác tạp chí net vừa tái xuất bản bài báo ban đầu từ phiên bản in (xem các nguồn dưới đây).
Thông thường, vào thời điểm này, tôi sẽ giới thiệu bạn đến [ITCSS webpage](https://itcss.io/) để nghiên cứu thêm. Tuy nhiên, không có gì giống như tài liệu mã nguồn mở tồn tại.
ITCSS vẫn sở hữu một phần và nếu bạn muốn sử dụng nó một cách trọn vẹn, bạn nên nghiên cứu giới thiệu ban đầu trong tạp chí net.Tôi không ở đây để đánh giá ý định của tác giả (tôi cảm ơn anh ta vì đã chia sẻ kiến ​​thức của mình), nhưng tôi nghĩ rằng điều này ngăn cản việc ITCSS được áp dụng rộng rãi hơn (có thể là ý định).
> Tính độc quyền một phần của ITCSS ngăn cản việc áp dụng rộng rãi hơn.

Tuy nhiên, điều này không ngăn cản bạn bắt đầu sử dụng nó trong các dự án nếu bạn thực sự muốn làm như vậy. Nhận ấn bản cụ thể của tạp chí net để tìm hiểu các nguyên tắc cơ bản của ITCSS và sau đó tìm hiểu các tài nguyên trực tuyến hiện có và các ví dụ để giúp bạn áp dụng nó trong các dự án thực tế.

### Nguồn
Tôi đã sử dụng ITCSS trên 4 dự án cho đến nay (bao gồm Xfive.co) và các Nguồn sau đây đã giúp tôi hiểu rõ hơn về nó:
- [Manage large CSS projects with ITCSS](http://www.creativebloq.com/web-design/manage-large-css-projects-itcss-101517528) - giới thiệu ITCSS của Harry Roberts (bài báo gốc được xuất bản từ phiên bản tạp chí, thiếu 1 vài cột ở biểu đồ đặc thù và bộ tiền xử lý)
- [Manage large-scale web projects with new CSS architecture ITCSS](https://www.creativebloq.com/web-design/manage-large-scale-web-projects-new-css-architecture-itcss-41514731) - ITCSS giới thiệu và phỏng vấn với Harry Roberts
- [Harry Roberts – Managing CSS Projects with ITCSS ](https://www.youtube.com/watch?v=1OKZOV-iLj4) - amột bài nói chuyện của Harry tại DaFED và các [ trang trình bày ](https://speakerdeck.com/dafed/managing-css-projects-with-itcss)
- [Manage large CSS projects with ITCSS](https://www.youtube.com/watch?v=hz76JIU_xB0) - một screencast cho bài báo net
- [ITCSS Screencast code](https://github.com/itcss/itcss-netmag) -  mã từ screencast ở trên tại GitHub
- [Một ví dụ khác của dự án ITCSS](https://github.com/csswizardry/frcss)
- Các bài viết tại csswizardry.com và đặc biệt là những điều sau đây:
- [BEMIT: Đưa quy ước đặt tên BEM lên một bước nữa](https://csswizardry.com/2015/08/bemit-taking-the-bem-naming-convention-a-step-further/)
- [Thêm mã giao diện trong suốt với Namespaces](https://csswizardry.com/2015/03/more-transparent-ui-code-with-namespaces/)
- [không thể thay đổi CSS](https://csswizardry.com/2015/03/immutable-css/)
- [The Specificity Graph](https://csswizardry.com/2014/10/the-specificity-graph/)
- [inuitcss](https://github.com/inuitcss/inuitcss) - OOCSS dựa trên ITCSS và cho thấy một số khái niệm và khả năng tiên tiến hơn
- [quy ước đặt tên BEMIT](http://www.jamesturneronline.net/blog/bemit-naming-convention.html)
Bạn cũng có thể kiểm tra [Chisel](https://github.com/xfiveco/generator-chisel/), Bộ khởi tạo Yeoman cho các dự án front-end and WordPress, có hỗ trợ ITCSS.
### Kinh nghiệm
Dưới đây là một vài suy nghĩ dựa trên kinh nghiệm của tôi với các dự án ITCSS:
##### Ít suy nghĩ về đặt tên và phong cách vị trí
Tính chất bắt buộc của ITCSS đặc biệt là khi kết hợp với [ quy ước đặt tên BEMIT](https://csswizardry.com/2015/08/bemit-taking-the-bem-naming-convention-a-step-further/)  cho phép bạn tập trung nhiều hơn vào việc giải quyết các thách thức phía trước thay vì suy nghĩ về tên và kiểu vị trí. Đây là những gì Xfive.co main.scss trông giống như:
```
@import "settings.colors";
@import "settings.global";

@import "tools.mixins";

@import "normalize-scss/normalize.scss";
@import "generic.reset";
@import "generic.box-sizing";
@import "generic.shared";

@import "elements.headings";
@import "elements.hr";
@import "elements.forms";
@import "elements.links";
@import "elements.lists";
@import "elements.page";
@import "elements.quotes";
@import "elements.tables";

@import "objects.animations";
@import "objects.drawer";
@import "objects.list-bare";
@import "objects.media";
@import "objects.layout";
@import "objects.overlays";

@import "components.404";
@import "components.about";
@import "components.archive";
@import "components.avatars";
@import "components.blog-post";
@import "components.buttons";
@import "components.callout";
@import "components.clients";
@import "components.comments";
@import "components.contact";
@import "components.cta";
@import "components.faq";
@import "components.features";
@import "components.footer";
@import "components.forms";
@import "components.header";
@import "components.headings";
@import "components.hero";
@import "components.jobs";
@import "components.legal-nav";
@import "components.main-cta";
@import "components.main-nav";
@import "components.newsletter";
@import "components.page-title";
@import "components.pagination";
@import "components.post-teaser";
@import "components.process";
@import "components.quote-banner";
@import "components.offices";
@import "components.sec-nav";
@import "components.services";
@import "components.share-buttons";
@import "components.social-media";
@import "components.team";
@import "components.testimonials";
@import "components.topbar";
@import "components.reasons";
@import "components.wordpress";
@import "components.work-list";
@import "components.work-detail";

@import "vendor.prism";

@import "trumps.clearfix";
@import "trumps.utilities";

@import "healthcheck";
```
Lưu ý: Chúng tôi sử dụng [ các thư mục riêng biệt cho mỗi lớp](https://github.com/xfiveco/generator-chisel/tree/master/generators/app/templates/styles/itcss) và tải các biểu định kiểu mới được thêm vào tự động trong [Chisel](https://github.com/xfiveco/generator-chisel/).  
##### Đối tượng sử dụng lại cho sự phát triển nhanh
đối tượng là ứng viên hoàn hảo để xây dựng một thư viện các thành phần tái sử dụng để cho phép phát triển front-end nhanh. Các phần UI sau đó sẽ bao gồm các đối tượng chung chung và các thành phần cụ thể của dự án. Ví dụ, innuitcss như một khuôn khổ dựa trên ITCSS chung chứa [một bó của các đối tượng](https://github.com/inuitcss/inuitcss/tree/develop/objects)  nhưng chỉ có [một thành phần mẫu](https://github.com/inuitcss/inuitcss/tree/develop/components)

##### Hiệu ứng
Tôi khuyên bạn nên định nghĩa các Hiệu ứng toàn cục cũng như các đối tượng như @keyframes o-fade-in trong file _objects.animations.scss
Các Hiệu ứng động cụ thể của thành phần phải được xác định trong các tệp thành phần tương ứng eg. @keyframes c-hero-scale in _components.hero.scss.
##### Sự linh hoạt
ITCSS khá linh hoạt về công việc và công cụ của bạn. Một trong những nhà phát triển của chúng tôi đã bày tỏ mối quan tâm về ITCSS boilerplate bao nhiêu. Nhưng trên thực tế điều này hoàn toàn tùy thuộc vào bạn - ITCSS không quy định rằng bạn cần phải có tất cả các lớp hiện diện (chỉ theo thứ tự chúng nên là nếu chúng có mặt).
Vì vậy, trong một thiết lập tối thiểu bạn có thể có các thành phần chỉ với các yếu tố mặc định kiểu dáng đến từ trình duyệt. Tất nhiên, điều này là không thực tế - một số cài đặt, thiết lập lại và / hoặc bình thường CSS được hầu hết mọi người sử dụng vì những lý do tốt.
##### Critical CSS 
ITCSS đóng vai trò tốt với CSS quan trọng do các chỉ số then chốt tam giác ngược. Mô hình dựa trên thành phần cho phép bạn tách UI trên giao diện người dùng thành các thành phần logic nên bạn thậm chí có thể chọn các phần của CSS quan trọng bằng tay (thêm vào đó trong bài viết sắp tới).
##### Kích thước tệp và kiểu trùng lặp
INếu có bất kỳ mối quan tâm nào với một kiến ​​trúc như ITCSS hoặc về cơ bản bất kỳ thành phần nào như kiến ​​trúc CSS, nó có thể là kích thước tệp kết quả. Các thành phần gói gọn các kiểu và cho phép chúng ta tránh xung đột và ghi đè CSS nhưng cũng có nghĩa là sự lặp lại kiểu có thể xảy ra khá thường xuyên.
ITCSS không thể cạnh tranh với [functional CSS ](https://blog.colepeters.com/building-and-shipping-functional-css/) theo nghĩa này. Mặt khác, nếu bạn thấy mình lặp lại rất nhiều kiểu dáng trong các thành phần, bạn có thể cân nhắc chuyển các kiểu này sang các đối tượng riêng biệt.
### Kết luận
Bạn sẽ không mắc sai lầm với ITCSS được. Nó là kết quả của kinh nghiệm và rất nhiều năm làm việc của Harry Roberts, một trong những tác giả CSS nổi tiếng nhất trên thế giới. Nếu bạn không phiền hãy đào sâu vào các nguồn lực một chút, bạn sẽ được thưởng một kiến ​​trúc đơn giản nhưng mạnh mẽ sẽ cho phép bạn tạo CSS có thể mở rộng và duy trì cho các dự án nhỏ hoặc lớn của bạn.

##### Quan tâm đến ITCSS nhiều hơn?
- [ITCSS: Một năm sau](https://www.xfive.co/blog/itcss-year-after/) - Năm cái nhìn sâu sắc từ năm với Tam giác Inverted CSS.
- Kiểm tra [Chisel](https://github.com/xfiveco/generator-chisel), một máy phát điện Yeoman cho các dự án front-end và WordPress, hỗ trợ ITCSS.