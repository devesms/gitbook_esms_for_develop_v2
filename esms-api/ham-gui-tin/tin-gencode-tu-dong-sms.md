# Tạo và gửi mã xác thực tự động bằng tin nhắn SMS

Để đáp ứng nhu cầu của người dùng về việc tự động tạo mã xác thực và gửi qua tin nhắn thương hiệu (SMS Brandname), chúng tôi đã thiết kế hai API: GENCODE để tạo mã và CHECKCODE để kiểm tra mã, giúp tối ưu hóa quy trình xác thực.

GENCODE: Tạo mã xác thực, mã OTP, mã tham chiếu hoặc mã giao dịch theo yêu cầu của hệ thống.

CHECKCODE: Kiểm tra xem mã đã tạo có hợp lệ hay không, giúp xác minh tính đúng đắn và đảm bảo an toàn khi sử dụng.



* [x] **GENCODE: tạo và gửi mã xác thực tự động**

<mark style="color:green;">**`GET`**</mark> [https://rest.esms.vn/MainService.svc/json/SendMessageAutoGenCode\_V4\_get?Phone={Phone}\&ApiKey={ApiKey}\&SecretKey={SecretKey}\&TimeAlive={TimeAlive}\&NumCharOfCode={NumCharOfCode}\&Brandname={Brandname}\&Type=2\&message={Content}](http://rest.esms.vn/MainService.svc/json/SendMessageAutoGenCode_V4_get?Phone={Phone}\&ApiKey={ApiKey}\&SecretKey={SecretKey}\&TimeAlive={TimeAlive}\&NumCharOfCode={NumCharOfCode}\&Brandname={Brandname}\&Type=2\&message={Content})\


* **Response Type:** <mark style="color:orange;">application/json</mark>

{% code overflow="wrap" %}
```json
curl --location --globoff 'https://rest.esms.vn/MainService.svc/json/SendMessageAutoGenCode_V4_get?Phone={{Phone}}&ApiKey={{ApiKey}}&SecretKey={{SecretKey}}&TimeAlive={{TimeAlive}}&NumCharOfCode={{NumCharOfCode}}&Brandname={{Brandname}}&Type=2&message={{Content}}&IsNumber={{IsNumber}}'
```
{% endcode %}

* **Cấu trúc body của request:**

<table><thead><tr><th width="183">Tham số</th><th width="117">Kiểu dữ liệu </th><th width="147" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>Phone</td><td>string</td><td>true</td><td>Số điện thoại nhận tin.</td></tr><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr><tr><td>TimeAlive</td><td>string</td><td>false</td><td>Thời gian hiệu lực của mã code. <br>Đơn vị tính: Phút. <br>Giới hạn từ 2 phút đến 15 phút.</td></tr><tr><td>NumCharOfCode</td><td>string</td><td>false</td><td>Số lượng ký tự của mã code. Mặc định khi không truyền là 6 ký tự.</td></tr><tr><td>Brandname</td><td>string</td><td>true</td><td>Tên Brandname (tên công ty hay tổ chức khi gửi tin sẽ hiển thị trên tin nhắn đó). <br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>Type</td><td>string</td><td>true</td><td>2: Gửi chăm sóc khách hàng.</td></tr><tr><td>message</td><td>string</td><td>true</td><td>Nội dung tin nhắn<br>Thay thế mã code OTP bằng {OTP}<br>- Ví dụ: <br>Muốn nhận tin nhắn về máy với nội dung:<br>"686868 la ma xac minh dang ky Baotrixemay cua ban". Thì ở mục message truyền: "{OTP} la ma xac minh dang ky Baotrixemay cua ban".</td></tr><tr><td>IsNumber</td><td>string</td><td>false</td><td>0: code chứa chữ và số.<br>1: code chỉ chứa số.</td></tr></tbody></table>

***

* **Response:**&#x20;

{% tabs %}
{% tab title="100" %}
```json
{
    "CodeResult": "100",
    "CountRegenerate": 0,
    "SMSID": "d533459ee42b2b9525ba9eabf6a8156"
}
```

**Request hợp lệ.**
{% endtab %}

{% tab title="101" %}
```json
{
    "CodeResult": "101",
    "CountRegenerate": 0,
    "ErrorMessage": "Authorize Failed"
}
```

**Sai thông tin ApiKey/SecretKey.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th width="199">Thuốc tính </th><th width="160">Kiểu dữ liệu </th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Mã trả về.</td></tr><tr><td>SMSID</td><td>string</td><td>ID tin nhắn do esms trả về.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi).</td></tr></tbody></table>

* [x] **CHECKCODE: Kiểm tra xem mã đã tạo có hợp lệ hay không**

<mark style="color:green;">**`GET`**</mark> [https://rest.esms.vn/MainService.svc/json/CheckCodeGen\_V4\_get?ApiKey=\{{ApiKey\}}\&SecretKey=\{{SecretKey\}}\&Phone=\{{{Phone\}}\&Code=\{{Code\}}](https://rest.esms.vn/MainService.svc/json/CheckCodeGen_V4_get?ApiKey=\{{ApiKey\}}\&SecretKey=\{{SecretKey\}}\&Phone=\{{{Phone\}}\&Code=\{{Code\}})

* **Response Type:** <mark style="color:orange;">application/json</mark>

{% code overflow="wrap" %}
```
curl --location --globoff 'https://rest.esms.vn/MainService.svc/json/CheckCodeGen_V4_get?ApiKey={{ApiKey}}&SecretKey={{SecretKey}}&Phone={{{Phone}}&Code={{Code}}'
```
{% endcode %}

* **Cấu trúc body của request:**

<table><thead><tr><th>Tham số</th><th width="187">Kiểu dữ liệu</th><th data-type="checkbox">Tính bắt buộc</th><th width="277">Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr><tr><td>Phone</td><td>string</td><td>true</td><td>Số điện thoại người nhận code.</td></tr><tr><td>Code</td><td>string</td><td>true</td><td>Mã code cần check.</td></tr></tbody></table>

* **Response:**

{% tabs %}
{% tab title="100" %}
```
{
 "CodeResult": "100",
 "CountRegenerate": 0,
 "ErrorMessage": "0901888484, Content: Success!"
}
```

**Request hợp lệ.**
{% endtab %}

{% tab title="101" %}
```
{
    "CodeResult": "101",
    "CountRegenerate": 0,
    "ErrorMessage": "Authorize Failed"
}
```

**Sai thông tin ApiKey/SecretKey.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th>Thuộc tính</th><th width="164">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Mã trả về.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi).</td></tr><tr><td>Content</td><td>string</td><td>Trạng thái của code.</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#a3a8616e-f2bc-4ad4-8f41-b5affda6c85d)**.**
