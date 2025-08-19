# Tạo và gửi mã xác thực tự động đa kênh: Zalo => SMS

Không giống như API tạo và gửi mã xác thực tự động qua tin nhắn SMS, API tạo và gửi mã tự động đa kênh mang lại nhiều lợi ích hơn, giúp người dùng tối ưu chi phí bằng cách lựa chọn kênh gửi phù hợp, đồng thời cải thiện trải nghiệm nhận mã với nội dung sinh động, trực quan hơn trên ứng dụng Zalo.

GENCODE: Tạo mã xác thực/mã OTP tự động, sau đó ưu tiên gửi qua ứng dụng Zalo, khi tin nhắn gửi qua Zalo thất bại sẽ tự động chuyển sang tin nhắn SMS với cùng một mã.

Các trường hợp thường gặp nhất khi gửi Zalo thất bại: số điện thoại người dùng không đăng ký zalo, Zalo OA không chưa mua gói duy trì,...

CHECKCODE: Kiểm tra xem mã đã tạo có hợp lệ hay không, giúp xác minh tính đúng đắn và đảm bảo an toàn khi sử dụng.

{% hint style="warning" %}
**Lưu ý:**

* Quý khách cần đăng ký Zalo OA, template Zalo, brandname CSKH và template brandname CSKH trước khi sử dụng.
* Khi có nhu cầu sử dụng API này, quý khách vui lòng gửi các thông tin sau đây cho bộ phận kinh doanh để cấu hình gửi: OAID, templateID zalo, brandname CSKH, template brandname CSKH.
{% endhint %}

* [x] **GENCODE: tạo và gửi mã xác thực tự động**

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/SendMessageAutoGenCode\_V5](http://rest.esms.vn/MainService.svc/json/SendMessageAutoGenCode_V5)

* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

{% code overflow="wrap" %}
```json
curl --location 'https://rest.esms.vn/MainService.svc/json/SendMessageAutoGenCode_V5' \
--header 'Content-Type: application/json' \
--data '{
     "ApiKey": "{{ApiKey}}",
     "Phone": "0901888484",
     "TimeAlive": "2",
     "SecretKey": "{{SecretKey}}",
     "MultiChannelTempId": "22575",
     "TypeId":"2"
}'
```
{% endcode %}

* **Cấu trúc body của request:**

<table><thead><tr><th width="207">Tham số</th><th width="124">Kiểu dữ liệu </th><th width="143" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>Phone</td><td>string</td><td>true</td><td>Số điện thoại nhận tin.</td></tr><tr><td>TimeAlive</td><td>string</td><td>true</td><td>Thời gian hiệu lực của mã code. <br>Đơn vị tính: Phút. <br>Giới hạn từ 2 phút đến 15 phút.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr><tr><td>MultiChannelTempId</td><td>string</td><td>true</td><td>Id do ViHAT cung cấp. Khi muốn sử dụng hàm này tài khoản của bạn phản có OA ZNS và brandname. Bạn cung cấp tempid của ZNS và template của tin SMS cho nhân viên kinh doanh để tạo MultiChannelTempId.</td></tr><tr><td>TypeId</td><td>string</td><td>true</td><td>1: Chỉ tạo ra mã Code.<br>2: Tạo ra và gửi tin nhắn về máy.</td></tr></tbody></table>

***

* Response:&#x20;

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

| Thuốc tính   | Kiểu dữ liệu  | Mô tả                             |
| ------------ | ------------- | --------------------------------- |
| CodeResult   | string        | Mã trả về.                        |
| SMSID        | string        | ID tin nhắn do esms trả về.       |
| ErrorMessage | string        | Thông tin lỗi trả về (nếu có lỗi) |

* [x] **CHECKCODE: Kiểm tra xem mã đã tạo có hợp lệ hay không**

<mark style="color:green;">**`GET`**</mark> [https://rest.esms.vn/MainService.svc/json/CheckCodeGen\_V4\_get?ApiKey=\{{ApiKey\}}\&SecretKey=\{{SecretKey\}}\&Phone=\{{{Phone\}}\&Code=\{{Code\}}](https://rest.esms.vn/MainService.svc/json/CheckCodeGen_V4_get?ApiKey=\{{ApiKey\}}\&SecretKey=\{{SecretKey\}}\&Phone=\{{{Phone\}}\&Code=\{{Code\}})

* **Response Type:** <mark style="color:orange;">application/json</mark>

{% code overflow="wrap" %}
```
curl --location --globoff 'https://rest.esms.vn/MainService.svc/json/CheckCodeGen_V4_get?ApiKey={{ApiKey}}&SecretKey={{SecretKey}}&Phone=0901888484&Code=1NTTJ6'
```
{% endcode %}

* **Cấu trúc body của request:**

<table><thead><tr><th>Tham số</th><th width="136">Kiểu dữ liệu</th><th data-type="checkbox">Tính bắt buộc</th><th width="270">Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr><tr><td>Phone</td><td>string</td><td>true</td><td>Số điện thoại người nhận code.</td></tr><tr><td>Code</td><td>string</td><td>true</td><td>Mã code cần check.</td></tr></tbody></table>

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

{% tab title="117" %}
```
{
    "CodeResult": "117",
    "CountRegenerate": 0,
    "ErrorMessage": "0901888484, Content: 1NTTJ6 Code Invalid"
}
```

**Mã code đã được sử dụng hoặc hết thời gian hiệu lực.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th width="146.60003662109375">Thuộc tính</th><th width="124">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Request được gửi đến ESMS thành công.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi).</td></tr><tr><td>Content</td><td>string</td><td>Trạng thái của code.</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#3ccbb0ef-9dec-4574-96db-397674952f88)**.**
