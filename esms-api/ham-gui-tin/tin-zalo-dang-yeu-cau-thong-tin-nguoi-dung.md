# Tin Zalo dạng yêu cầu thông tin người dùng

## HTTP request

\
<mark style="color:yellow;">**POST**</mark> [https://rest.esms.vn/MainService.svc/json/SendZaloFollowerMessage\_V5\_post\_json/](http://rest.esms.vn/MainService.svc/json/SendZaloFollowerMessage\_V5\_post\_json/)



* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location 'https://rest.esms.vn/MainService.svc/json/SendZaloFollowerMessage_V5_post_json/' \
--header 'Content-Type: application/json' \
--data '{
"ApiKey": "{{ApiKey}}",
"SecretKey": "{{SecretKey}}",
"OAID": "{{OAID}}",
"CallbackUrl":"{{CallbackURL}}",
    "Payload": {
        "recipient": {
            "user_id": "{{UserID}}"
        },
        "message": {
            "attachment": {
                "type": "template",
                "payload": {
                    "template_type": "request_user_info",
                    "elements": [
                        {
                            "title": "{{Title}}",
                            "subtitle": "{{Subtitle}}",
                            "image_url": "{{ImageURL}}"
                        }
                    ]
                }
            }
        }
    }
}'
```



* **Cấu trúc body của request:**

<table><thead><tr><th width="135">Tham số</th><th width="120">Kiểu dữ liệu</th><th width="152" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này. <br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>User_id</td><td>string</td><td>true</td><td>Userid cần gửi đến, đây là userid của zalo.</td></tr><tr><td>Title</td><td>string</td><td>true</td><td>Tiêu đề hiển thị của template.<br>Lưu ý: Hỗ trợ tối đa 100 ký tự.</td></tr><tr><td>Subtitle</td><td>string</td><td>true</td><td>Tiêu đề phụ của template.<br>Lưu ý: Hỗ trợ tối đa 500 ký tự.</td></tr><tr><td>ImageUrl</td><td>string</td><td>true</td><td>Link hình ảnh, chấp nhận link đuôi PNG và JPG.</td></tr><tr><td>CallbackUrl</td><td></td><td>false</td><td>URL nhận kết quả gửi tin. <br>Xem body mẫu <a href="https://samplefordevelopers.esms.vn/#aabcd08e-e84a-4e9a-9598-c894af957d5b">ở đây</a>. <br>Xem chi tiết <a href="https://developers-v2.esms.vn/esms-api/callback-url">ở đây</a>.</td></tr></tbody></table>

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
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th width="189">Thuốc tính</th><th width="160">Kiểu dữ liệu </th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Mã trả về.</td></tr><tr><td>SMSID</td><td>string</td><td>ID tin nhắn do esms trả về.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi).</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [_**Link code mẫu**_](https://samplefordevelopers.esms.vn/#a8181709-4215-4375-bdb3-3e6c5a0a23c4)_**.**_
