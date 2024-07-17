# Tin nhắn Zalo

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/SendZaloMessage\_V5\_post/](http://rest.esms.vn/MainService.svc/json/SendZaloMessage\_V5\_post/)

* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

{% code overflow="wrap" %}
```json
curl --location 'https://rest.esms.vn/MainService.svc/json/SendZaloMessage_V5_post/' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey": "{{ApiKey}}",
    "SecretKey": "{{SecretKey}}",
    "OAID": "{{OAID}}",
    "Phone": "{{Phone}}",
    "TempData": [
        {
            "key": "{{key1}}",
            "value": "{{value1}}"
        },
        {
            "key": "{{key2}}",
            "value": "{{value2}}"
        }
    ],
    "SendDate": "{{SendDate}}",
    "TempID": "{{TempID}}",
    "campaignid": "{{Campaignid}}",
    "Sandbox": "{{Sandbox}}",
    "CallbackUrl": "{{CallbackUrl}}"
}'
```
{% endcode %}

* **Cấu trúc body của request:**

<table><thead><tr><th width="152">Tham số</th><th width="229">Kiểu dữ liệu</th><th width="137" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>Phone</td><td>string</td><td>true</td><td>Số điện thoại người nhận.</td></tr><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey eSMS cung cấp.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey eSMS cung cấp.</td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này. <br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>TempData</td><td>string</td><td>true</td><td>Bao gồm tên biến và giá trị biến trong Template:<br>key: Tên biến (bắt buộc phải giống trong Template đã đăng ký).<br>value: Giá trị biến.</td></tr><tr><td>SendDate</td><td>string</td><td>false</td><td>Thời gian hẹn gửi của tin. <br>Không truyền khi tin muốn tin nhắn gửi đi liền.<br>Định dạng: yyyy-mm-dd hh:MM:ss.</td></tr><tr><td>TempID </td><td>string</td><td>true</td><td>Template của Zalo OA mà khách hàng đăng kí với eSMS.</td></tr><tr><td>campaignid</td><td>string</td><td>false</td><td>Tên chiến dịch gửi tin, tối đa 254 ký tự.</td></tr><tr><td>Sandbox</td><td>string</td><td>false</td><td>1: Tin gửi ở môi trường test, dùng để kiểm tra kết nối và các thông số tích hợp, không về tin nhắn, không trừ tiền.<br>0: Tin gửi ở môi trường bình thường, có về tin nhắn.</td></tr><tr><td>CallbackUrl</td><td>string</td><td>false</td><td>URL nhận kết quả gửi tin.<br>Xem body mẫu <a href="https://samplefordevelopers.esms.vn/#b98ca55e-3001-4446-b5bb-a4ab86127b0b">ở đây</a><strong>.</strong> <br>Xem chi tiết <a href="../callback-url.md">ở đây</a><strong>.</strong></td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```json
{
    "CodeResult": "100",
    "CountRegenerate": 0,
    "SMSID": "d8e0f1f0702544b2acb456ca9ccfd111250"
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

{% tab title="789" %}
```json
{
    "CodeResult": "789",
    "CountRegenerate": 0,
    "ErrorMessage": "TemplateId is not config"
}
```

**Template chưa được cấu hình cho OA ID bạn đang sử dụng.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th width="195">Thuộc tính</th><th width="156">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Mã trả về.</td></tr><tr><td>SMSID</td><td>string</td><td>ID của tin nhắn mới được tạo ra trên hệ thống eSMS. Dùng ID này để query lấy trạng thái tin nhắn.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi).</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu của các ngôn ngữ ở link**</mark>_<mark style="color:yellow;">:</mark> [**Link code mẫu .**](https://samplefordevelopers.esms.vn/#2d996c73-a5c2-45ca-973e-d18aabb960c7)
