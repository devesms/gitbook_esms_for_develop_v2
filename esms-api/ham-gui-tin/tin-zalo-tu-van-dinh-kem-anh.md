# Tin Zalo Tư vấn đính kèm ảnh

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/SendZaloFollowerMessage\_V5\_post\_json/](http://rest.esms.vn/MainService.svc/json/SendZaloFollowerMessage_V5_post_json/)

* **Content Type:** <mark style="color:orange;">text/plain</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location 'http://rest.esms.vn/MainService.svc/json/SendZaloFollowerMessage_V5_post_json/' \
--header 'Content-Type: text/plain' \
--header 'Cookie: ASP.NET_SessionId=asfgp2dj1kt4kbg1yzuo35ky; ASP.NET_SessionId=5xcbl12ska5q5wocug3chmjz' \
--data '{
    "ApiKey": "{{ApiKey}}",
    "SecretKey": "{{SecretKey}}",
    "OAID": "{{OAID}}",
    "CallbackUrl": "{{CallbackUrl}}", 
    "Payload": {
        "recipient": {
            "user_id": "{{user_id}}"
        },
        "message": {
            "text": "{{text}}",
            "attachment": {
                "type": "template",
                "payload": {
                    "template_type": "media",
                    "elements": [
                        {
                            "media_type": "image",
                            "url": "{{url}}"
                        }
                    ]
                }
            }
        }
    }
}'
```



* **Cấu trúc body của request:**

<table><thead><tr><th width="135">Tham số</th><th width="109">Kiểu dữ liệu </th><th width="136" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey eSMS cung cấp.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey eSMS cung cấp.</td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này. <br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>User_id</td><td>string</td><td>true</td><td>Userid cần gửi đến, đây là userid của zalo.</td></tr><tr><td>text</td><td>string</td><td>false</td><td>Tiêu đề của ảnh<br> Giới hạn tối đa là 2.000 ký tự</td></tr><tr><td>url</td><td>string</td><td>true</td><td>Link hình ảnh, chấp nhận link đuôi PNG và JPG<br>Dung lượng tối đa: 1MB<br><br></td></tr><tr><td>CallbackUrl</td><td>string</td><td>false</td><td>eSMS sẽ trả về kết quả của tin nhắn này.<br>Xem body mẫu <a href="https://samplefordevelopers.esms.vn/#cd0e23a3-5aa5-4198-a8bb-be0d8e450df9">ở đây</a>.<br>Xem chi tiết <a href="../callback-url.md">ở đây</a>.</td></tr></tbody></table>

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

| Thuốc tính   | Kiểu dữ liệu  | Mô tả                             |
| ------------ | ------------- | --------------------------------- |
| CodeResult   | string        | Mã trả về.                        |
| SMSID        | string        | ID tin nhắn do esms trả về.       |
| ErrorMessage | string        | Thông tin lỗi trả về (nếu có lỗi) |

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#c0e00f1f-0c1f-4be1-8aac-f730d14e0e29)**.**
