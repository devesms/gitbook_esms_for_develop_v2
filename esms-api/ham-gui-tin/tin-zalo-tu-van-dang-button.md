# Tin Zalo Tư vấn dạng button

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/SendZaloFollowerMessage\_V5\_post\_json/](http://rest.esms.vn/MainService.svc/json/SendZaloFollowerMessage_V5_post_json/)

* **Content Type:** <mark style="color:orange;">text/plain</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

{% code overflow="wrap" %}
```json

curl --location --request POST 'https://rest.esms.vn/MainService.svc/json/SendZaloFollowerMessage_V5_post_json/' \
--header 'Content-Type: text/plain' \
--data-raw '{
    "ApiKey": "{{ApiKey}}",
    "SecretKey": "{{SecretKey}}",
    "OAID": "{{OAID}}",
    "Payload": {
        "recipient": {
            "user_id": "{{user_id}}"
        },
        "message": {
            "text": "Chào mừng bạn đến với hệ thống eSMS. Đây là tin nhắn zalo dạng button.",
            "attachment": {
                "type": "template",
                "payload": {
                    "buttons": [
                        {
                            "title": "Link url",
                            "payload": {
                                "url": "https://developers.esms.vn/esms-api/ham-gui-tin/tin-zalo-tu-van-dang-button"
                            },
                            "type": "oa.open.url"
                        },
                        {
                            "title": "QUERY SHOW",
                            "type": "oa.query.show",
                            "payload": "#callback_data"
                        },
                        {
                            "title": "QUERY HIDE",
                            "type": "oa.query.hide",
                            "payload": "#callback_data"
                        },
                        {
                            "title": "OPEN SMS",
                            "type": "oa.open.sms",
                            "payload": {
                                "content": "Cảm ơn quý khách đã sử dụng dịch vụ của chúng tôi. Chúc quý khách một ngày mới tốt lành!",
                                "phone_code": "0901888484"
                            }
                        },
                        {
                            "title": "OPEN PHONE",
                            "type": "oa.open.phone",
                            "payload": {
                                "phone_code": "0901888484"
                            }
                        }
                    ]
                }
            }
        }
    }
}'

// Truyền \r\n để gửi nội dung xuống dòng
```
{% endcode %}

* **Cấu trúc body của request:**

<table><thead><tr><th width="135">Tham số</th><th width="109">Kiểu dữ liệu </th><th width="136" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey eSMS cung cấp.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey eSMS cung cấp.</td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này. <br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>CallbackUrl</td><td>string</td><td>false</td><td>eSMS sẽ trả về kết quả của tin nhắn này.<br>Xem body mẫu <a href="https://samplefordevelopers.esms.vn/#cd0e23a3-5aa5-4198-a8bb-be0d8e450df9">ở đây</a>.<br>Xem chi tiết <a href="../callback-url.md">ở đây</a>.</td></tr><tr><td>SendDate</td><td>string</td><td>false</td><td>Thời gian hẹn gửi của tin.<br>Không truyền khi tin muốn tin nhắn gửi đi liền.<br>Định dạng: yyyy-mm-dd hh:MM:ss</td></tr><tr><td>Payload</td><td>Object</td><td>true</td><td>Chứa nội dung cần gửi</td></tr></tbody></table>

***

**Cấu trúc thuộc tính recipient**

<table><thead><tr><th width="131.66668701171875">Tham số</th><th width="109.800048828125">Kiểu dữ liệu </th><th width="140.066650390625" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>user_id</td><td>string</td><td>true</td><td>ID của người nhận.</td></tr></tbody></table>

**Cấu trúc thuộc tính message**

<table><thead><tr><th width="131.66668701171875">Tham số</th><th width="112.800048828125">Kiểu dữ liệu </th><th width="136.8665771484375" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>text</td><td>string</td><td>true</td><td>Tiêu đề của button<br>Giới hạn tối đa là 2.000 ký tự</td></tr><tr><td>attachment</td><td>Object</td><td>true</td><td>Attachment cần gửi.</td></tr></tbody></table>

**Cấu trúc thuộc tính message.attachment**

<table><thead><tr><th width="133.800048828125">Tham số</th><th width="111.800048828125">Kiểu dữ liệu </th><th width="137.933349609375" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>type</td><td>string</td><td>true</td><td><p>Loại attachment. <br><br>Giá trị nhận vào bắt buộc:</p><ul><li><code>type</code> = template</li></ul></td></tr><tr><td>payload</td><td>Object</td><td>true</td><td>Dữ liệu của action. <br>Cấu trúc của payload phải phù hợp với từng loại action và được cho ở bảng bên dưới</td></tr></tbody></table>

**Cấu trúc payload cho các loại action được hỗ trợ**

<table><thead><tr><th width="139.13330078125">Giá trị type</th><th width="184.4000244140625">Kiểu dữ liệu của payload</th><th>Giá trị payload và kết quả khi người quan tâm bấm vào</th></tr></thead><tbody><tr><td>oa.open.url</td><td>string</td><td><p>Data là một Url sẽ được mở trong ứng dụng Zalo khi người quan tâm bấm vào button. Ví dụ: </p><p><code>{</code><br>    <code>"title": "OPEN URL",</code><br>    <code>"payload" : {</code><br>    <code>"url": "https://developers.zalo.me/"</code><br>    <code>},</code><br>    <code>"type": "oa.open.url"</code><br><code>}</code></p><ul><li><strong>Chú ý:</strong> Giới hạn cho thuộc tính "title" là 100 kí tự.</li></ul></td></tr><tr><td>oa.query.show</td><td>string</td><td><p>Data là một chuỗi ký tự ví dụ “#callback_data”. Khi người quan tâm bấm vào button, hệ thống sẽ gửi một tin nhắn có nội dung chứa trong data từ người quan tâm đến Official Account. Tin nhắn này sẽ hiện trên cửa sổ chat trên máy của người quan tâm. Ví dụ: <br><code>{</code><br>    <code>"title": "QUERY SHOW",</code><br>    <code>"type": "oa.query.show",</code><br>    <code>"payload": "#callback_data"</code><br><code>}</code></p><ul><li><p><strong>Chú ý:</strong></p><ul><li>Giới hạn cho thuộc tính "title" là 100 kí tự.</li><li>Giới hạn cho thuộc tính "payload" là 1000 kí tự.</li></ul></li></ul></td></tr><tr><td>oa.query.hide</td><td>string</td><td><p>Data là một chuỗi ký tự ví dụ “#callback_data”. Khi người quan tâm bấm vào button, hệ thống sẽ gửi một tin nhắn có nội dung chứa trong data từ người quan tâm đến Official Account. Tin nhắn này sẽ bị ẩn trên cửa sổ chat trên máy của người quan tâm. Ví dụ: </p><p><code>{</code><br>    <code>"title": "QUERY HIDE",</code><br>    <code>"type": "oa.query.hide",</code><br>    <code>"payload": "#callback_data"</code><br><code>}</code></p><ul><li><p><strong>Chú ý:</strong></p><ul><li>Giới hạn cho thuộc tính "title" là 100 kí tự.</li><li>Giới hạn cho thuộc tính "payload" là 1000 kí tự.</li></ul></li></ul></td></tr><tr><td>oa.open.sms</td><td>object</td><td><p>Data đối tượng json chứa 2 thuộc tính “content” và “phoneCode”. Ví dụ: </p><p><code>{</code><br>    <code>"title": "OPEN SMS",</code><br>    <code>"type": "oa.open.sms",</code><br>    <code>"payload": {</code><br>    <code>"content":"alo",</code><br>    <code>"phone_code":"84919018791"</code><br>    <code>}</code><br><code>}</code></p><p>Khi người quan tâm click vào button, cửa sổ sms trên điện thoại của người quan tâm sẽ được mở với 2 thông tin sẵn có là phone code và nội dung tin nhắn trong data.</p><ul><li><p><strong>Chú ý:</strong></p><ul><li>Giới hạn cho thuộc tính "title" là 100 kí tự.</li><li>Thuộc tính "content" có giới hạn là 160 kí tự.</li></ul></li></ul></td></tr><tr><td>oa.open.phone</td><td>object</td><td><p>Data số điện thoại sẽ nhập vào khi bật ứng dụng gọi điện, ví dụ: </p><p><code>{</code><br>    <code>"title": "OPEN PHONE",</code><br>    <code>"type": "oa.open.phone",</code><br>    <code>"payload":{</code><br>    <code>"phone_code":"84919018791"</code><br>    }<br>}</p><p>Khi người quan tâm click vào button, cửa sổ call trên điện thoại của người quan tâm sẽ được mở với thông tin sẵn có là phone number trong data.</p><ul><li><strong>Chú ý:</strong> Giới hạn cho thuộc tính "title" là 100 kí tự.</li></ul></td></tr></tbody></table>

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
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th width="149.79998779296875">Thuốc tính </th><th width="119.7999267578125">Kiểu dữ liệu </th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Request được gửi đến ViHAT thành công.<br><br><strong>Lưu ý:</strong> Mã phản hồi <strong>100</strong> chỉ xác nhận rằng yêu cầu đã được gửi thành công đến hệ thống ESMS, <strong>không phản ánh việc tin nhắn đã được gửi đến số điện thoại người nhận hay chưa</strong>.<br>Để theo dõi trạng thái cuối cùng của tin nhắn, quý khách vui lòng truyền thêm tham số <strong>CallbackUrl</strong>; hệ thống ESMS sẽ tự động gửi phản hồi (callback) đến địa chỉ này khi có trạng thái cuối của tin.</td></tr><tr><td>SMSID</td><td>string</td><td>ID tin nhắn do esms trả về.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi)</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#c0e00f1f-0c1f-4be1-8aac-f730d14e0e29)**.**
