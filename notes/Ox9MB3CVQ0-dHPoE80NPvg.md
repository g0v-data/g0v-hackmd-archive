
1. The HTTP protocol
- Http là chữ viết tắt của HyperText Transfer Protocol (giao thức truyền tải siêu văn bản). Đây là một giao thức ứng dụng được sử dụng thường xuyên nhất trong bộ các giao thức TCP/IP (gồm một nhóm các giao thức nền tảng cho internet). 
- HTTP:
    + Mô hình hoạt động: Mô hình máy khách - máy chủ thông qua giao thức của HTTP.
    + Mã hóa: Không được mã hóa thông tin
    + Mức độ bảo mật: Không mã hóa thông tin nên hacker dễ dàng lấy cắp thông tin.

- HTTPS:
    + Mô hình máy khách máy chủ, bổ sung thêm giao thức SSL và TSL (đảm bảo rằng không ai khác ngoài các máy khách và máy chủ có thể hack thông tin, dữ liệu ra ngoài).
    + Được mã hóa thông tin, sử dụng SSL/ TSL tiêu chuẩn công nghệ bảo mật, truyền thông mã hóa giữa máy chủ Web server và trình duyệt.
    + Hỗ trợ việc xác thực tính đích danh (bằng cách đăng nhập vào tài khoản) của website mà máy khách truy cập thông qua việc kiểm tra xác thực bảo mật.Bảo mật thông tin, an toàn với người dùng.

2. HTTP Requests
- HTTP Request hiểu một cách đơn giản là các thông tin sẽ được gửi từ khách hàng (client) lên server. Server sẽ có nhiệm vụ tìm và xử lý các loại dữ liệu, thông tin, client mong muốn. HTTP Request có thể tồn tại dưới file text hoặc dưới dạng XML hoặc dạng Json

- Dòng đầu tiên của mọi yêu cầu HTTP bao gồm ba mục, cách nhau bằng dấu cách:
    +  Một động từ chỉ phương thức HTTP. Phương pháp được sử dụng phổ biến nhất là GET, có chức năng lấy tài nguyên từ máy chủ web
    +  URL thường hoạt động như một tên cho tài nguyênđang được yêu cầu, cùng với một chuỗi truy vấn tùy chọn chứa các tham số mà máy khách đang chuyển tới tài nguyên đó. Chuỗi truy vấn được chỉ định bằng ký tự ? trong URL.
    +  Phiên bản HTTP đang được sử dụng. Các phiên bản HTTP duy nhất được sử dụng phổ biến trên Internet là 1.0 và 1.1, và hầu hết các trình duyệt đều sử dụng phiên bản mặc định 1.1

- Một số điểm đáng chú ý khác trong HTTP Requests:
    + The referer: được sử dụng để chỉ ra URL vì người dùng đã nhấp vào liên kết trên trang đó
    + The User-Agent: được sử dụng để cung cấp thông tin về trình duyệt hoặc phần mềm máy khách đã tạo ra yêu cầu.
    + Accept-Encoding: là danh sách những thuật toán mã hóa client đề nghị server sử dụng. Sau khi nhận được đề nghị, server sẽ lọc ra những tên thuật toán hợp lệ, sau đó chọn một trong số đó để mã hóa với client rồi thông báo cho client bằng header “Content-Coding”.
    + The host: chỉ định tên máy chủ xuất hiện trong URL đầy đủ đang được truy cập
    + The cookie

3. HTTP Responses 
- HTTP Response là một phần của giao thức HTTP (Hypertext Transfer Protocol) trong lập trình web. Nó là kết quả mà máy chủ (server) trả về cho yêu cầu (request) từ máy khách (client) sau khi nhận được yêu cầu đó.
- Dòng đầu tiên của mỗi phản hồi HTTP bao gồm ba mục, cách nhau bởi khoảng trống:
    + Phiên bản HTTP đang được sử dụng.
    + Mã số trạng thái cho biết kết quả của yêu cầu. 200 là mã trạng thái chung; điều đó có nghĩa là yêu cầu đã thành công và tài nguyên được yêu cầu đang được trả lại.
        + Các mã trạng thái thường gặp bao gồm:
            + 2xx : thành công
            + 3xx : chuyển hướng
            + 4xx : lỗi từ client
            + 5xx : lỗi từ server
    + Reason phrase: nguyên nhân mô tả trạng thái của yêu cầu.
- Một số điểm đáng chú ý khác trong HTTP Responses:
    + The Server: cho biết phần mềm máy chủ web đang được sử dụng và đôi khi các chi tiết khác như các mô-đun đã cài đặt và hệ điều hành máy chủ. Thông tin chứa đựng có thể có hoặc không chính xác
    + The Set-cookie: cấp cho trình duyệt một cookie bổ sung; thông tin này được gửi lại trong tiêu đề cookie của các yêu cầu tiếp theo tới thông tin này.
    + The Pragma: 
    + The expires: cho biết nội dung đã hết hạn vào quá khứ và không nên được lưu vào bộ nhớ đệm.
    + The content-type : loại nội dung
    + The content-length : độ dài nội dung

4. HTTP Methods:
    - Mỗi method có 4 tính chất quan trọng đó là:
        - safe: độ an toàn
        - idempotent: tính bất biến
        - visibility: tính che dấu thông tin
        - cacheable: có thể cache được 
    - Một số định nghĩa:
        - Safe: một request http methods được xem là safe khi sau rất nhiều lần gọi, nó vẫn không làm thay đổi resource mà nó đang truy cập đến
        - idempotent: một request http methods được xem là idempotent nếu sau nhiều lần gọi, nó vẫn trả về kết quả như nhau
        - Một request http methods được xem là visibility khi nó không để lộ ra thông tin trên URL khi request được gửi 
        - cacheable: một request http methods được xem là cacheable khi sau lần thứ nhất của request, kết quả phản hồi có thể được lưu vào một trong các loại cache trên websites 
    - Một vài phương thức HTTP requests:
        - GET: được sử dụng để truy xuất dữ liệu từ server ở một tài nguyên rõ ràng đã được chỉ định
            +  Safe -> yes: vì phương thức chỉ lấy, yêu cầu và truy xuất dữ liệu nên nó được xem là method an toàn nhất. 
                + Nếu phương thức GET này cung cấp thông tin (user, password của admin) thì nó không được xem là an toàn.
            - Idempotent -> yes: GET method luôn là idempotent, bởi vì ta có gọi hàng ngần method này tới server thì cũng không làm thay đổi resource của nó.
            - Visibility -> no: phương thức GET không thực sự tốt, các parameter được nhìn thấy rõ trên URL. Điều này đồng nghĩa với việc các parameter này được lưu lại trong lịch sử. Những ai tò mò muốn thay đổi có thể dễ dàng làm được. 
            - Cacherable -> yes: vì method GET đơn thuần là lấy dữ liệu, nên khi đã lấy xong, ta có thể cache những giá trị này lại. Việc lưu trữ có thể là (Local Storage, Cookies,...)
        - POST: Gửi data lên server để xử lí ở một tài nguyên nhất định
            - Safe -> no: nếu một người viết web service cho API không quản lí tốt cách xác thực người dùng được thực hiện method post. Một lập trình viên có thể dễ dàng fake parameter. Sau đó gửi tới server, các hình thức tấn công đã được biết tới trước đây như là Cross-site, Request Forgery.
            - Idempotent -> no: method post là method được sử dụng rất nhiều trong Http methods. Tuy nhiên, tính idempotent của method post lại rất khó để đảm bảo. Nếu một POST được gọi để khởi tạo folder, ở lần đầu tiên -> folder được tạo. Ở lần gọi thứ hai -> thất bại -> do folder đã được tạo.
            - Visibility -> yes
            - Cacheable -> no: phương thức post không thể được cache lại. Mọi xử lí của chúng ta mong muốn về method post đều được xử lí ở server. Chính vì vậy, không thể cache lại bất cứ giá trị gì ở phía client khi ta gọi method post.
        - PUT: được sử dụng để tạo tài nguyên, hoặc ghi đè nó.
            - Safe->no: do method put thực hiện cập nhật trạng thái tài nguyên. Nên nó được đánh gíá là không an toàn.
            - Idempotent: PUT được sử dụng để cập nhật trạng thái tài nguyên. Nên nếu ta gọi method PUT n lần, lần đầu tiên sẽ cập nhật trạng thái tài nguyên. Tiếp đến, n-1 lần request tiếp theo sẽ thực hiện lặp đi lặp lại không thay đổi gì.
            - Visibility->yes: nó ẩn đi các parameter gửi đi ở URL
            - Cacheable: vì không lấy dữ liệu gì ở server nên không thể cache lại các kết quả đã lấy được.
        - HEAD: trả về nội dung headers nếu tài nguyên được chỉ định gọi tới có thể lấy được bằng method GET
            - Safe->yes: chính vì method Head chỉ trả về nội dung headers nên nó được xem là an toàn
                - Idempotent: tương tự như GET, method head cũng được đánh giá là idempotent, do sau n lần gọi giá trị của nó trả về vẫn không thay đổi.
                - Visibility->no: vì thông tin được lấy cũng nằm trong URL, nên tính che dấu thông tin của HEAD method giống GET, không được đảm bảo.
                - Cacheable->yes: do thông tin lấy được là headers, nên có thể cache lại các giá trị này cho các request tiếp theo.
        - DELETE: xóa một tài nguyên nhất định ở server bằng Request-URL
            - Safe->no: nếu như ở method GET, khi thực hiện thành công, ta nhìn thấy dữ liệu trả về thì method DELETE là không an toàn vì client không đảm bảo rằng các thao tác mong muốn khi gửi method GET đã được thực hiện ở server.
            - Idempotent->no
            - Visibility->yes
            - Cacheable->no
        - PATCH: được sử dụng để ghi đè các thông tin thay đổi
        - OPTIONS: được sử dụng để mô tả các options giao tiếp cho tài nguyên đích. 
        - TRACE: là cách để kiểm tra sự lặp lại theo đường dẫn của tài nguyên đích, dùng để chạy các thử nghiệm gở lỗi và thực hiên thao tác chẩn đoán trên API
        - CONNECT: có tác dụng tạo kết nối đến máy chủ thông qua HTTP va tham số URL

5. Request Headers:
    - Trường accept: ám chỉ loại nội dung mà client có thể hiểu được 
            - Ví dụ:
                text/html,application/xhtml+xml, application/xml;q=0.9,image/webp, image/png,*/*;q=0.8
            
         - q được gọi là quality value, mục đích của nó là để ám chỉ trong một danh sách các giá trị thì giá trị nào được ưu tiên hơn cả thì sẽ có q cao hơn, giá trị q nằm trong khoảng 0-1 và chấp nhận 3 số ở phần thập phân
         - trong ví dụ trên thì text/html,application/xhtml+xml không có giá trị q thì sẽ có giá trị q mặc định = 1, độ ưu tiên cao nhất
         - */* được gọi là wildcard character : là một kí tự đại diện cho 1 phần nội dung, ví dụ * là một kí tự wildcard, phần nội dung này có thể gồm nhiều kí tự, hoặc là 0 có kí tự nào 
             + Ví dụ: "Xin chào *," : ở đây có 1 wildcar sẽ đại diện cho một hoặc nhiều kí tự hoặc có thể là k có kí tự nào cả 
                 + Từ ví dụ trên, wildcard có thể đại diện cho các từ sau: "Xin chào Việt Nam,", wildcard ở đây là Việt Nam
                 + Hoặc "Xin chào ,", wildcard ở đây là rỗng 
        + Vậy */* có thể đại diện cho bất kì chuỗi nào có kí tự / trong đó, ví dụ: "/", "html/text, "text/" 
        + Lưu ý: bên cạnh wildcard là *, ta còn có thể gặp wildcard là ?, khác với *, ? chỉ đại diện cho một kí tự mà thôi.
    - Trường Accept-Charset: là bộ mã mà client chấp nhận, ví dụ như ASCII, qtf-8,..
    - Trường Accept-Encoding: header này đưa ra các thuật toán mã hóa dữ liệu mà client có thể hiểu được, ví dụ: gzip, deflate, * hoặc là deflate, gzip;q=0,1, *;q=0.5
    - Trường Accept-Language: ngôn ngữ mà client có thể hiểu, ví dụ: 
        - vi-VN, vn;q=0.9, en;q=0.8, de;q=0.7, *;q=0.5
    - Trường Authorization: khi cilent yêu cầu một research trên server thì không phải lúc nào server cũng trả lời mà server sẽ yêu cầu bạn phải có quyền thì mới được thực hiện và authorization là nơi mà bạn báo cho server là có quyền hay không. 
        + cú pháp: <type> <credentials>.
        + trong đó, giá trị phổ biến nhất của type là basic.
        + credentials: là thông tin server sử dụng để kiểm tra xem client có hợp lệ hay không.
        + cấu trúc của credentials: toBase64(username:password), trong đó:
                -    username là tên client dùng để đăng nhập
                - password là mật khẩu đăng nhập
                - hàm toBase64 sẽ chuyển chuỗi kết hợp của username và password thành chuỗi ở dạng Base64
    - Trường Host: tên miền hoặc địa chỉ IP của server
    - Trường user-Agent: thể hiện thông tin về loại phần mềm và phiên bản client.
    - Trường cookie: Thông tin được gửi từ server đến client và được lưu trữ trên máy tính của client. Cookie được sử dụng để lưu trữ các thông tin như đăng nhập, thiết lập ngôn ngữ, lịch sử duyệt web, v.v. Nhờ đó, server có thể nhận biết và tương tác với client một cách cá nhân hóa.
    - Trường Cache-Control: là một "HTTP header" được sử dụng để chỉ định các chính sách cache (caching policy) của trình duyệt trong cả yêu cầu (request) của máy khách (client) và phản hồi (response) của máy chủ (server). Các chính sách bao gồm cách tài nguyên (resource) được lưu vào bộ nhớ cache, nơi lưu trữ tài nguyên và thời gian tồn tại (time to live) tối đa trước khi hết hạn.
        + "Cache-control" được chia thành các chỉ thị (directive), các chỉ thị phổ biến nhất được trình bày chi tiết như sau:
            - Cache-Control: Max-Age : tính bằng giây, lượng thời gian cần thiết để bản sao được lưu trong bộ nhớ cache của tài nguyên hết hạn. Sau khi hết hạn, trình duyệt phải làm mới phiên bản tài nguyên của mình bằng cách gửi một yêu cầu khác tới máy chủ.
            Ví dụ: cache-control:max-age = 120 có nghĩa là tài nguyên trả về có giá trị trong 120 giây, sau đó trình duyệt phải yêu cầu phiên bản mới hơn.
            - Cache-control:No-cache: có nghĩa là trình duyệt có thể lưu phản hồi vào bộ nhớ cache, nhưng trước tiên phải gửi yêu cầu xác thực đến máy chủ gốc.
            - Cache-control:No-store: có nghĩa là các trình duyệt không được phép lưu phản hồi vào bộ nhớ cache và phải lấy phản hồi đó từ máy chủ mỗi khi được yêu cầu. Thiết lập này thường được sử dụng cho dữ liệu nhạy cảm, chẳng hạn như thông tin.

6. Response headers:
        - Accept ranges: range-unit:
Khi server gửi về client header này thì server muốn cho client biết rằng server chấp nhận gửi về cho client từng phần dữ liệu của resource chứ không nhất thiết phải là toàn bộ nội dung của resource.
Giá trị của range-unit có thể là byte hoặc none. Nếu là none thì nghĩa là server không có hỗ trợ về từng phần, client sẽ phải tải hết toàn bộ dữ liệu về.
        - Location: header này được sử dụng để chuyển hướng (redirect). Với status code là 301 hoặc 302.
        - Proxy-Authenticate: Cấu trúc của 1 proxy authenticate là: 1#challenge. 
        Ví dụ: 
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c58f460a39fc4a0ed1a6ae501e5aa4ad.png)

trong đó tham số realm là bắt buộc, còn gọi là protection space. 
Ví dụ:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b9cba2fae3cb60b567adb5a4b9111685.png)
    - Khi đó các request đến vietnam và singapore ta sẽ sử dụng realm là Asia và tương tự với unitedkingdom là EU.
    - Lưu ý: realm phân biết hoa và thường, như Asia # asia.



 -  Content-Length: server thông báo cho phía client về dung lượng của gói tin 
 - Content - Type: cho biết thông tin về định dạng của văn bản.
 - Content-Encoding: trả về một định dạng mã hóa nội dung.
 - Etag: header này dùng để lưu trữ bộ nhớ trong cache, ví dụ: 
         - Etag: "pub1259380237;gz"
         Khi server gửi header này cho phía client thì trình duyệt sẽ lưu lại giá trị này. Lần sau nếu như còn truy cập tiếp thì trình duyệt sẽ gửi HTTP 
         - If-None-Match: "pub1259380237;gz"
        Nếu như giá trị của header này phù hợp với server thì client nhận status code 304. Lúc này trình duyệt sẽ load nội dung từ trong bộ nhớ cache mà không cần nhờ tới server.
- Expires: thông báo cho client biết nội dung này có hiệu lực trong bao lâu kể từ lúc server phản hồi.
- Last-modified: lần cuối cùng đoạn văn bản được chỉnh sửa.
- Pragma: Cho phép trình duyệt có được lưu vào trong bộ nhớ cache không.
- Set-cookie: web server sẽ gửi cookie cho phía client và phía client sẽ gửi cookie này lại cho web server trong các lần truy cập tiếp theo.
_ Server: cung cấp thông tin về server và hệ điều hành được sử dụng.


7. URL

URL là viết tắt của từ Uniform Resource Locator, có nghĩa là định vị tài nguyên thống nhất. Ở đây bạn có thể hiểu rằng URL chính là địa chỉ của một tài nguyên duy nhất ở trên web. Mỗi một URL hợp lệ có thể trỏ đến một tài nguyên duy nhất như hình ảnh, video, trang html, file PDF,...
URL có thể chứa nhiều thành phần khác nhau như hostname ánh xạ tới địa chỉ IP của một tài nguyên cụ thể trên internet. Cùng với đó là hàng loạt thông tin bổ sung để thông báo cho trình duyệt và máy chủ cách xử lý mọi thứ.
- Cấu trúc của một URL:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e08aa35bf548ff94127031fdcbe3d2ed.png)

    - scheme: là giao thức http hoặc https.
    - Tiếp theo là phần authority sau dấu // và kết thúc bằng dấu /
    - Port (cổng): 80 là dịch vụ web 
    - Path: bắt đầu từ kí tự /(slash) 
        Ví dụ: https://example.vn/class/login
        thì path sẽ là: /class/login 
    - Query: 
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d9d3cefbcdedcabe8c11afa0179ab248.png)
    Ở ví dụ này ta có 2 query đó là name=ferret và org=standar. Các query được ngăn cách bởi dấu &.
    - Fragment: được gọi là hash. Được dùng với mục đích tham chiếu tới các phần của resource tại URL.
    Ví dụ 1 tài liệu html có 3 heading, ta muốn trỏ đến đúng heading số 3 thì ta sẽ thêm heading3 ở phần fragment này. 
    
8. Cookies
Cookies trên trình duyệt web có ý nghĩa khác hoàn toàn. Đây là những file được trang web tạo ra để lưu lại các thông tin về hoạt động duyệt web của người dùng.
Cookie có thể được phần làm 2 loại chính:
-  Session cookies (phiên cookie): giữ lại ở trình duyệt và sẽ bị xóa bỏ khi đóng trình duyệt. Khi cửa sổ trình duyệt mới được mở lại, người dùng sẽ phải cung cấp lại các chứng thực của mình.
- Persistent cookise (coookie liên tục): giữ ở trình duyệt cho tới khi hết hạn hoặc được xóa một cách thủ công. Các trang web sẽ ghi nhớ các chứng thực ngay cả khi người dùng đóng trình duyệt.

Cấu trúc của một cookie:
- Name: Tên cookie k phân biệt chữ hoa và chữ thường. 
- Value: giá trị được lưu trữ trong cookie.
- Domain: là domain mà cookies chúng ta hợp lệ. Mọi thứ được gửi hoặc được sử dụng từ domain sẽ kèm theo cookies.
- Path: đường dẫn được chỉ định trong domain, nơi mà cookies sẽ được gửi đến server.
- Expiration: Đây là dấu thời gian, nó cho biết lúc nào cookies sẽ bị xóa. Mặc định thì tất cả cookies sẽ bị xóa khi tắt trình duyệt.
- Secure Flag: cờ an toàn, với mục đích chỉ gửi cookies nếu kết nối SSL được sử dụng. Ví dụ: khi gửi request tới https://www.vietcombank.com.vn thì nên gửi kèm thông tin cookies, còn tới http://www.vietcombank.com.vn thì không.

9. Status codes
Mỗi thông báo phản hồi HTTP phải chứa mã trạng thái ở dòng đầu tiên, cho biết kết quả của yêu cầu. Các mã trạng thái được chia thành năm nhóm:
    - 1xx: Information (Thông tin): Khi nhận được những mã như vậy tức là request đã được server tiếp nhận và quá trình xử lý request đang được tiếp tục.
    - 2xx: Success (Thành công): Khi nhận được những mã như vậy tức là request đã được server tiếp nhận, hiểu và xử lý thành công
    -   3xx: Redirection (Chuyển hướng): Mã trạng thái này cho biết client cần có thêm action để hoàn thành request
    -    4xx: Client Error (Lỗi Client): Nó nghĩa là request chứa cú pháp không chính xác hoặc không được thực hiện.
    -    5xx: Server Error (Lỗi Server): Nó nghĩa là Server thất bại với việc thực hiện một request nhìn như có vẻ khả thi.

Có rất nhiều mã trạng thái cụ thể, nhiều mã chỉ được sử dụng trong những trường hợp đặc biệt. Dưới đây là các mã trạng thái mà bạn có nhiều khả năng gặp phải nhất khi tấn công một ứng dụng web:
- 100 continue: Phản hồi tạm thời này cho biết rằng mọi thứ tới hiện tại vẫn ổn và phía client nên tiếp tục yêu cầu hay bỏ qua phản hồi nếu yêu cầu đã hoàn tất.
- 200 OK: 
GET: Tài nguyên đã được tìm nạp và được truyền trong nội dung thông điệp.
HEAD: Các header thực thể nằm trong nội dung thông điệp.
PUT hoặc POST: Tài nguyên mô tả kết quả của hành động được truyền trong nội dung thông điệp.
TRACE: Nội dung thông điệp chứa thông báo yêu cầu khi máy chủ nhận được.
- 201 Created: Yêu cầu đã thành công và kết quả là một tài nguyên mới đã được tạo. Đây thường là phản hồi được gửi sau các yêu cầu POST hoặc một số yêu cầu PUT.
- 301 Moved Permanently: URL của tài nguyên được yêu cầu đã được thay đổi vĩnh viễn. URL mới được đưa ra trong phần phản hồi.
- 302 Found: Code phản hồi này có nghĩa là URI của tài nguyên được yêu cầu đã được thay đổi tạm thời. Những thay đổi khác trong URI có thể được thực hiện trong tương lai. Do đó, chính URI này sẽ được client sử dụng trong các yêu cầu trong tương lai.
- 304 Not Modified: Code này được sử dụng cho mục đích caching. Nó cho client biết rằng phản hồi chưa được điều chỉnh, nên client có thể tiếp tục sử dụng cùng phiên bản phản hồi trong bộ nhớ cache.
- 400 Bad Request: Máy chủ không thể hiểu yêu cầu do cú pháp không hợp lệ.
- 401 Unauthorized: Cho dù quy chuẩn HTTP chỉ định “unauthorized” (không có thẩm quyền), nhưng nó có nghĩa phản hồi này là “unauthenticated” (chưa được xác thực). Có nghĩa là, client phải các tự xác thực chính mình để nhận được phản hồi đã yêu cầu.
- 403 Forbidden: Client không có quyền truy cập vào phần nội dung, nghĩa là nó không được phép, vì vậy máy chủ từ chối cung cấp tài nguyên được yêu cầu. Không giống như 401, danh tính của client đã được máy chủ nhận biết.
- 404 Not found: chỉ ra rằng tài nguyên được yêu cầu không tồn tại.
- 405 Method Not Allowed cho biết rằng phương thức được sử dụng trong yêu cầu không được hỗ trợ cho URL đã chỉ định. Ví dụ: bạn có thể nhận được mã trạng thái này nếu bạn cố gắng sử dụng phương thức PUT khi nó không được hỗ trợ.
- 413 Payload Too Large: Thực thể yêu cầu lớn hơn giới hạn do máy chủ xác định, máy chủ có thể đóng kết nối hoặc trả về trường header Retry-After.
- 414 URI Too Long: URI được yêu cầu bởi client dài hơn mức máy chủ muốn thông dịch.
- 500 Internal Server Error: cho biết máy chủ đã gặp phải sự cố lỗi khi thực hiện yêu cầu. Điều này thường xảy ra khi bạn gửi thông tin đầu vào không mong muốn gây ra lỗi chưa được xử lý ở đâu đó trong quá trình xử lý của ứng dụng. Bạn nên xem kỹ lại toàn bộ nội dung phản hồi của máy chủ về bất kỳ chi tiết nào cho thấy bản chất của lỗi.
- 503 Service Unavailable: Máy chủ hiện tại không có sẵn (hiện đang quá tải hoặc bị down để bảo trì). Đây chỉ là trạng thái tạm thời.

10. HTTP proxy
Về cơ bản, proxy HTTP có thể được mô tả như một bộ lọc nội dung hiệu suất cao mà lưu lượng truy cập đi qua để tiếp cận bạn. Nói cách khác, nó đóng vai trò trung gian giữa trình duyệt máy khách và máy chủ web đích. Sau đó, bất kỳ lưu lượng truy cập nào được xử lý thông qua máy chủ sẽ xuất hiện như thể nó đến từ địa chỉ IP chuyên dụng của proxy thay vì địa chỉ mà thiết bị của bạn được liên kết.
- Khi bạn gửi một yêu cầu đến một máy chủ, trước tiên nó sẽ đến proxy dưới dạng văn bản thuần túy.
- Proxy xử lý yêu cầu và gửi một yêu cầu mới, che địa chỉ IP của bạn bằng chính nó.
- Trang web nhận được yêu cầu và gửi phản hồi đến máy chủ proxy.
- Cuối cùng, máy chủ proxy của bạn chuyển tiếp dữ liệu này trở lại cho bạn.

Dưới đây là ba loại proxy HTTP mà bạn có thể bắt gặp. Sự khác biệt chính giữa chúng nằm ở mức độ ẩn danh mà chúng cung cấp:
- Public proxy: Là dạng proxy miễn phí được cung cấp công khai cho người dùng. Vì là loại proxy miễn phí, nó thường không đảm bảo tính bảo mật và tốc độ truyền tải dữ liệu tốt nhất. Bên cạnh đó, các địa chỉ IP của public proxy thường bị chặn và bị giới hạn trong việc truy cập nhiều trang web.
- Shared proxy: Là dạng proxy được chia sẻ giữa nhiều người dùng, vì vậy nó cũng được gọi là semi-dedicated proxy. Khi sử dụng shared proxy, nhiều người dùng sẽ chia sẻ địa chỉ IP của proxy đó, do đó tốc độ truyền tải dữ liệu có thể bị giảm. Tuy nhiên, do được chia sẻ, giá cả của shared proxy thường thấp hơn so với elite proxy.
- Elite proxy: Là dạng proxy cao cấp, cung cấp tính bảo mật cao và tốc độ truyền tải dữ liệu nhanh. Nó được gọi là độc quyền (exclusive) proxy, vì chỉ có một người dùng được sử dụng địa chỉ IP của proxy đó.
Elite proxy được sử dụng để bảo vệ thông tin cá nhân và tránh bị giám sát khi truy cập vào các trang web. Tuy nhiên, giá cả của elite proxy thường rất cao và không phù hợp với người dùng thông thường.

- Ưu điểm của proxy:
    - Tăng cường bảo mật - các quy tắc phát hiện giao thức bất thường có thể được đặt để xác định và từ chối các gói đáng ngờ, theo cách này bảo vệ máy chủ web của bạn khỏi các cuộc tấn công đến từ mạng bên ngoài.
    -  Thiết lập quyền riêng tư – một số chọn sử dụng proxy để bảo vệ địa chỉ IP thực của họ vì nhiều lý do bảo mật. Giống như proxy thông thường, proxy HTTP cũng có thể che dấu địa chỉ IP của bạn.
    -   Hạn chế nội dung – các công ty có thể hạn chế nội dung đi vào mạng của họ. Có thể thiết lập proxy HTTP để hạn chế nội dung dựa trên tên miền hoặc tên đường dẫn, tên tệp hoặc phần mở rộng xuất hiện trong URL.
    -   Bỏ qua các hạn chế của trang web mục tiêu – điều này đặc biệt phù hợp với việc quét web và thu thập dữ liệu web. Proxy HTTP được sử dụng để tạo tiêu đề yêu cầu HTTP chứa thông tin về trình duyệt tạo yêu cầu.

- Hạn chế:
    - Không hỗ trợ các giao thức khác: HTTP proxy chỉ hỗ trợ các giao thức liên quan đến HTTP và HTTPS. Điều này có nghĩa là nó không thể được sử dụng cho các giao thức khác như FTP hay SMTP.
    -    Bảo mật yếu: Mặc dù HTTP proxy có thể được cấu hình để bảo vệ các thông tin đăng nhập và dữ liệu nhạy cảm, nhưng nó vẫn có những điểm yếu về bảo mật. Các thông tin mật khẩu của người dùng có thể bị lộ do các tấn công đánh cắp thông tin.
    -    Tốc độ truyền tải dữ liệu chậm: Mỗi lần sử dụng HTTP proxy để truy cập Internet, thời gian đáp ứng sẽ bị chậm hơn so với truy cập trực tiếp. Điều này có thể dẫn đến sự giảm hiệu suất và tốc độ truyền tải dữ liệu.
    -    Không hỗ trợ đầy đủ cho các ứng dụng: HTTP proxy không thể hỗ trợ hoàn toàn cho các ứng dụng cụ thể. Ví dụ, nếu một ứng dụng đang sử dụng một giao thức khác với HTTP và HTTPS, thì nó sẽ không thể được sử dụng với HTTP proxy.
    
11. HTTP authenticate
HTTP authentication – còn được gọi là cơ chế xác thực HTTP giúp người dùng xác minh danh tính. Nó là một cơ chế bảo mật kiểm tra xem người dùng có đủ điều kiện truy cập web hay không. Khi máy khách và máy chủ giao tiếp với nhau, dựa vào thành phần HTTP, máy chủ sẽ yêu cầu thông tin đăng nhập để xác thực. Vậy nên có thể nói, việc xác thực web sẽ thông qua tiêu chuẩn HTTP bảo đảm an toàn cho người dùng.

Khi truy cập bằng chế độ bảo mật, HTTP thông qua cơ chế xác thực đảm bảo sự an toàn. Có rất nhiều sơ đồ xác thực được sử dụng ở đây, các cái tên phổ biến như:

- HTTP Authentication Schemes: còn được gọi là lược đồ xác thực HTTP. Máy chủ đưa ra những lược đồ xác thực khác nhau cho người dùng lựa chọn. Chúng đều là những phương pháp dùng trên web cho độ an toàn cao.
Basic authentication (xác thực cơ bản): còn được gọi là mô hình thử thách – phản hồi. Máy chủ yêu cầu xác thực và máy khách cung cấp tên người dùng, mật khẩu. Đó là cơ chế xác thực một yếu tố và thông tin được trao đổi ở định dạng văn bản rõ ràng.
- Digest authentication (xác thực thông báo): loại này an toàn hơn xác thực cơ bản. Cũng với quy trình xác thực giống nhau nhưng nó có thêm giá trị nonce và thuật toán MD5 để mã hóa. Từ đó tăng cường bảo mật khi xác thực danh tính người dùng.
- Bearer authentication (xác thực đa yếu tố): xác thực dựa trên mã thông báo. Nó có thêm một lớp bổ sung và bảo mật cấp với mã thông báo để xác thực thông tin nhận được từ người dùng.
- NTLM (New Technology LAN Manager – quản lý mạng LAN theo công nghệ mới). Đây là một giao thức bảo mật của Windows xác thực danh tính người dùng mà không cần thông tin đăng nhập và truy cập vào tài nguyên.
- Negotiate authentication (đàm phán xác thực): là phiên bản nâng cấp của NTLM. Nó sử dụng giao thức Kerberos làm nhà cung cấp xác thực một cách nhanh chóng và an toàn.


