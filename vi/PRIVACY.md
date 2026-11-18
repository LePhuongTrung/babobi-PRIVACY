# Chính sách quyền riêng tư — BabiBo

BabiBo do Le Phuong Trung phát triển.

_Cập nhật lần cuối: 18 tháng 11 năm 2026_

BabiBo là app tài chính cá nhân cho iPhone. Đây không phải app cho iPad. Người
phát hành app không vận hành dịch vụ nào nhận sổ của bạn. Không có tài khoản
BabiBo, không có thống kê, không có báo cáo sự cố, không có mã quảng cáo, và
không có SDK bên thứ ba nào tự gửi dữ liệu về.

Một số tính năng có gửi dữ liệu ra khỏi máy, tới công ty bạn chọn hoặc tới
trang mà tính năng đó phải truy cập. Trang này nói phần nào rời máy, bằng cách
nào, vì sao, ai nhận (kể cả nhà cung cấp AI), giữ bao lâu, và cách bạn dừng
hoặc xóa.

## Phần nằm trên máy

Mọi thứ sổ biết — tài khoản, số dư, giao dịch, danh mục, ngân sách, khoản nắm
giữ, ảnh hóa đơn, và tên đã học từ hóa đơn — nằm trong một file cơ sở dữ liệu
bên trong vùng chứa của app trên máy bạn.

File đó nằm trong bản sao lưu của máy. Nếu bạn bật iCloud Backup, một bản đã
mã hóa đi cùng phần còn lại của điện thoại. Bản đó là việc giữa bạn và Apple.
Chúng tôi không đọc được.

Bạn có thể xuất file bất cứ lúc nào từ **Cài đặt → Dữ liệu**, và nhập vào
BabiBo trên máy khác. Bản khôi phục không mang phiên ngân hàng: khóa ký nằm
trên điện thoại đã tạo phiên đó, và bạn kết nối ngân hàng lại trên điện thoại
mới.

Xóa app là xóa file này. Trong đó có khóa API Gemini đã lưu, tên sản phẩm đã
học, giá đã lưu, và logo đã lưu tạm.

Chúng tôi không dùng dữ liệu này để quảng cáo hay theo dõi, và chúng tôi không
bao giờ nhận một bản sao.

## Ngân hàng của bạn, qua Enable Banking

Tùy chọn, trên iPhone, Mac, và server do bạn tự chạy. Không có gì được gửi cho
đến khi bạn đăng ký ứng dụng của chính bạn với Enable Banking và kết nối một
ngân hàng.

**Dữ liệu.** Số dư, sao kê (các giao dịch), và mã định danh tài khoản mà ngân
hàng trả về, kể cả IBAN khi ngân hàng gửi.

**Cách gửi.** App hỏi Enable Banking, Enable Banking hỏi ngân hàng của bạn,
rồi ghi câu trả lời vào file trên máy. Mã ứng dụng và khóa riêng nằm trên máy
bạn. Trên iPhone, sau khi một ngân hàng đã kết nối, app nhờ iOS đánh thức app
vào buổi sáng — hướng tới 07:15, và bỏ qua lần kéo nếu một lần đồng bộ đã
thành công trong sáu giờ vừa rồi — rồi tải sao kê lại. iOS có thể bỏ qua giờ
đó. Lần kéo chỉ chạy khi Background App Refresh đang bật cho BabiBo.

**Vì sao.** Để điền sổ. Nếu bạn đã cho phép thông báo, điện thoại cũng đăng
một bản tóm tắt khi có giao dịch mới. Thông báo đó được tạo trên máy. Nó không
được gửi cho chúng tôi.

**Ai nhận.** Enable Banking và ngân hàng của bạn. Không phải chúng tôi. Họ làm
gì với dữ liệu thì theo điều khoản của họ và sự đồng ý bạn đưa khi đăng ký và
khi bạn chấp thuận ngân hàng.

**Giữ bao lâu, và cách dừng.** Bản trong app còn đến khi bạn xóa tài khoản.
Xóa một tài khoản thì xóa giao dịch của tài khoản đó, và khi đó là tài khoản
cuối trên kết nối thì xóa cả kết nối, nên lần kéo buổi sáng không còn gì để
hỏi. Enable Banking và ngân hàng giữ những gì điều khoản của họ yêu cầu.
Chúng tôi không xóa được bản của họ. Rút sự đồng ý tại ngân hàng của bạn, hoặc
trong ứng dụng Enable Banking mà bạn đã đăng ký.

## Google Gemini

Tùy chọn, và chỉ trên iPhone. Không có yêu cầu nào được gửi cho đến khi bạn
lưu một khóa trong **Cài đặt → Hóa đơn**.

**Dữ liệu.** Tên món viết tắt in trên hóa đơn, và tên cửa hàng. Không phải ảnh,
không phải số tiền, không phải ngày, và không phải phần còn lại của sổ. Một
yêu cầu tiếp theo có thể gửi các từ danh mục đã lưu trên điện thoại — những từ
như "gà", không kèm cửa hàng, số tiền, hay ngày — để xếp chúng vào một danh
sách cố định các nhóm sản phẩm.

**Cách gửi.** Bạn tạo khóa tại [Google AI Studio](https://aistudio.google.com)
và lưu trong Cài đặt. App sau đó gọi API Gemini của Google
(`generativelanguage.googleapis.com`) bằng khóa đó. Một nhãn đã được trả lời
một lần thì được giữ trên điện thoại và không gửi lại.

**Vì sao.** Để đổi một chữ viết tắt trên hóa đơn thành tên sản phẩm và danh
mục, rồi ghi lại vào file trên máy.

**Ai nhận.** Google, theo điều khoản Gemini API áp dụng cho khóa bạn tạo.
Chúng tôi không nhận đoạn chữ đó. Google là nhà cung cấp AI của tính năng này.

**Giữ bao lâu, và cách dừng.** Google giữ theo những điều khoản đó. Chúng tôi
không đặt khoảng thời gian đó, và chúng tôi không có bản sao trên server của
mình. Kết quả đọc nằm trong cơ sở dữ liệu trên máy đến khi bạn xóa app.
**Cài đặt → Hóa đơn → Retirer** xóa khóa khỏi điện thoại và dừng các yêu cầu
sau đó. Nút đó có nhãn Retirer. Việc này không xóa những lần đọc đã lưu trên
điện thoại, và không xóa những gì Google đã nhận. Hãy xóa hoặc đổi khóa trong
Google AI Studio nếu bạn muốn Google ngừng chấp nhận khóa đó.

## Yahoo Finance

**Dữ liệu.** Một mã chứng khoán, chẳng hạn `CW8.PA`. Khi bạn tìm một chứng
khoán, là chữ bạn đã gõ. Không phải số lượng, không phải giá trị, và không
phải tên tài khoản.

**Cách gửi.**

- Trên iPhone, một lần làm mới sổ hỏi Yahoo giá của mỗi khoản nắm giữ có mã.
  Lưu một mã thì hỏi ngay. Ô tìm hỏi khi bạn tìm. App không làm việc này trong
  lần kéo nền buổi sáng.
- Trên Mac, và trên server bạn tự chạy, Yahoo chỉ được dùng nếu bạn đặt nhà
  cung cấp giá là Yahoo. Mặc định là tắt, và các bản đó khi ấy không gửi yêu
  cầu báo giá nào.

Yêu cầu đi tới `query1.finance.yahoo.com`. Không có khóa API. Kết nối cũng
mang địa chỉ mạng và user agent, như mọi yêu cầu HTTPS. App không thêm tên và
không thêm mã tài khoản.

**Vì sao.** Để hiện giá, và trên iPhone, để tìm mã khớp với chữ bạn đã gõ.

**Ai nhận.** Yahoo. Không phải chúng tôi.

**Giữ bao lâu, và cách dừng.** Giá được ghi vào file trên máy và còn đến khi
bạn xóa app. Yahoo giữ nhật ký của họ theo chính sách quyền riêng tư của
Yahoo. Chúng tôi không có tài khoản Yahoo nào để xóa các nhật ký đó. Trên
iPhone, xóa khoản nắm giữ để dừng các yêu cầu giá tiếp theo cho khoản đó, và
đừng tìm nếu bạn không muốn chữ được gửi. Trên Mac và trên server của bạn, đặt
nhà cung cấp giá về `none`.

## Trang web của cửa hàng

Chỉ iPhone. Bật theo mặc định.

**Dữ liệu.** Không có trường nào của sổ được gắn vào yêu cầu. App tải `https://`
cộng với tên miền của cửa hàng, rồi tải biểu tượng mà trang đó nêu. Yêu cầu
trông như trình duyệt hỏi địa chỉ đó: chính địa chỉ, địa chỉ mạng của điện
thoại, và user agent của trình duyệt. Cookie không được lưu và cũng không được
gửi.

**Cách gửi.** Khi **Cài đặt → Danh mục và cửa hàng → Logo cửa hàng** đang bật,
và cửa hàng có trang đã biết hoặc trang bạn đã gõ. Ảnh được yêu cầu lần đầu
nó cần đến.

**Vì sao.** Để vẽ biểu tượng của cửa hàng đó. Không có gì khác.

**Ai nhận.** Trang web của cửa hàng đó, và bên lưu trữ trang. Không phải một
dịch vụ logo, và không phải chúng tôi.

**Giữ bao lâu, và cách dừng.** Ảnh nằm trong bộ nhớ tạm của app đến khi iOS
xóa bộ nhớ tạm hoặc bạn xóa app. Một trang không có biểu tượng dùng được sẽ
không bị hỏi lại trong bảy ngày. Nhật ký của trang là của trang; chúng tôi
không xóa được. Tắt **Logo cửa hàng** để dừng các yêu cầu mới.

## Server của chính bạn

Tùy chọn. Nếu bạn trỏ BabiBo tới một server bạn tự chạy, app đọc và ghi sổ ở
đó. Máy đó là của bạn. Xóa địa chỉ server trong Cài đặt để dừng. Xóa những gì
server đã lưu trên máy đó.

## Face ID

Nếu bạn bật khóa app, BabiBo nhờ iOS xác minh bạn. iOS trả lời có hoặc không.
Sinh trắc của bạn không bao giờ vào app, và không được gửi cho ai.

## Trẻ em

BabiBo không hướng tới trẻ em.

## Thay đổi

Mọi thay đổi của chính sách này được commit lên
<https://github.com/LePhuongTrung/babobi-PRIVACY>, nơi lịch sử là công khai.

Trang này là tiếng Việt. Cùng một chính sách bằng tiếng Anh là PRIVACY.md ở
thư mục gốc. Các ngôn ngữ khác của app nằm trong thư mục mang mã ngôn ngữ.

## Liên hệ

Không có tài khoản BabiBo để xóa, vì chúng tôi không giữ tài khoản. Xóa app là
xóa file trên máy. Với dữ liệu một bên nhận đã có, dùng cách trong mục của bên
nhận ở trên.

Câu hỏi: <babibo.support@lephuongtrung.id.vn>
