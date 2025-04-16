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

<table><thead><tr><th width="131.66668701171875">Tham số</th><th width="112.800048828125">Kiểu dữ liệu </th><th width="136.8665771484375" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>text</td><td></td><td>true</td><td>Tiêu đề của button<br>Giới hạn tối đa là 2.000 ký tự</td></tr><tr><td>attachment</td><td></td><td>true</td><td>Attachment cần gửi.</td></tr></tbody></table>

**Cấu trúc thuộc tính message.attachment**

<table><thead><tr><th width="133.800048828125">Tham số</th><th width="111.800048828125">Kiểu dữ liệu </th><th width="137.933349609375" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>type</td><td></td><td>true</td><td><p>Loại attachment. <br><br>Giá trị nhận vào bắt buộc:</p><ul><li><code>type</code> = template</li></ul></td></tr><tr><td>payload</td><td></td><td>true</td><td>Dữ liệu của action. </td></tr></tbody></table>

**Cấu trúc thuộc tính message.attachment.payload**

<table><thead><tr><th width="134.86669921875">Tham số</th><th width="110.7999267578125">Kiểu dữ liệu </th><th width="139" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>buttons</td><td>array</td><td>true</td><td><p>Tittle: mô tả của action.<br></p><p>Default_action <br>- Type oa.open.url: Url sẽ được mở trong ứng dụng Zalo khi người quan tâm bấm vào action <br>- Type oa.open.sms: Khi người quan tâm click vào action, cửa sổ sms trên điện thoại của người quan tâm sẽ được mở với 2 thông tin sẵn có là phone code và nội dung tin nhắn trong data. <br>- Type oa.query.hide: Payload là một chuỗi ký tự ví dụ “#eSMS”. Khi người quan tâm bấm vào action, hệ thống sẽ gửi một tin nhắn có nội dung chứa trong data từ người quan tâm đến Official Account. Tin nhắn này sẽ bị ẩn trên cửa sổ chat trên máy của người quan tâm. <br>- Type oa.query.show: Payload là một chuỗi ký tự ví dụ “#eSMS”. Khi người quan tâm bấm vào action, hệ thống sẽ gửi một tin nhắn có nội dung chứa trong data từ người quan tâm đến Official Account. Tin nhắn này sẽ hiện trên cửa sổ chat trên máy của người quan tâm. <br>- Type oa.open.phone: Khi người quan tâm click vào action, cửa sổ call trên điện thoại của người quan tâm sẽ được mở với thông tin số điện thoại là giá trị của phone_code.</p></td></tr></tbody></table>

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

| Thuốc tính   | Kiểu dữ liệu  | Mô tả                             |
| ------------ | ------------- | --------------------------------- |
| CodeResult   | string        | Mã trả về.                        |
| SMSID        | string        | ID tin nhắn do esms trả về.       |
| ErrorMessage | string        | Thông tin lỗi trả về (nếu có lỗi) |

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#c0e00f1f-0c1f-4be1-8aac-f730d14e0e29)**.**
