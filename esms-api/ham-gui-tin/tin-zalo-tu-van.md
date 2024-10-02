# Tin Zalo tư vấn

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/SendZaloFollowerMessage\_V5\_post\_json/](http://rest.esms.vn/MainService.svc/json/SendZaloFollowerMessage\_V5\_post\_json/)

* **Content Type:** <mark style="color:orange;">text/plain</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location 'https://rest.esms.vn/MainService.svc/json/SendZaloFollowerMessage_V5_post_json/' \
--header 'Content-Type: text/plain' \
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
                    "buttons": [
                        {
                            "title": "{{title}}",
                            "payload": {
                                "url": "{{url}}"
                            },
                            "type": "oa.open.url"
                        },
                        {
                            "title": "{{title}}",
                            "type": "oa.query.show",
                            "payload": "{{payload}}"
                        },
                        {
                            "title": "{{title}}",
                            "type": "oa.query.hide",
                            "payload": "{{payload}}"
                        },
                        {
                            "title": "{{title}}",
                            "type": "oa.open.sms",
                            "payload": {
                                "content": "{{content}}",
                                "phone_code": "{{phone_code}}"
                            }
                        },
                        {
                            "title": "{{title}}",
                            "type": "oa.open.phone",
                            "payload": {
                                "phone_code": "{{phone_code}}"
                            }
                        }
                    ]
                }
            }
        }
    }
}'
```



* **Cấu trúc body của request:**

<table><thead><tr><th width="166">Tham số</th><th width="123">Kiểu dữ liệu </th><th width="140" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey eSMS cung cấp.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey eSMS cung cấp.</td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này. <br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>User_id</td><td>string</td><td>true</td><td>Userid cần gửi đến, đây là userid của zalo.</td></tr><tr><td>Content</td><td>string</td><td>true</td><td>Nội dung tin nhắn<br>Lưu ý: Khi gửi dạng tin nhắn này khách hàng vui lòng liên hệ cho nhân viên kinh doanh để được hỗ trợ về content.</td></tr><tr><td>Template_type</td><td>string</td><td>true</td><td><p>Loại template:<br></p><p>-Với template gửi thông báo theo mẫu đính kèm ảnh, giá trị nhận vào là:</p><ul><li><code>template_type</code> = media</li></ul><p>-Với template gửi thông báo theo mẫu yêu cầu thông tin người dùng, giá trị nhận vào là:</p><ul><li><code>template_type</code> = request_user_info</li></ul><p>-Với template gửi thông báo theo mẫu văn bản thì không cần truyền tham số này.<br><br></p></td></tr><tr><td>Elements</td><td>string</td><td>true</td><td><p></p><ul><li>Tittle: mô tả của action.</li><li>Default_action<br>- Type oa.open.url: Url sẽ được mở trong ứng dụng Zalo khi người quan tâm bấm vào action<br>- Type oa.open.sms: Khi người quan tâm click vào action, cửa sổ sms trên điện thoại của người quan tâm sẽ được mở với 2 thông tin sẵn có là phone code và nội dung tin nhắn trong data.<br>- Type oa.query.hide: Payload là một chuỗi ký tự ví dụ “#eSMS”. Khi người quan tâm bấm vào action, hệ thống sẽ gửi một tin nhắn có nội dung chứa trong data từ người quan tâm đến Official Account. Tin nhắn này sẽ bị ẩn trên cửa sổ chat trên máy của người quan tâm.<br>- Type oa.query.show: Payload là một chuỗi ký tự ví dụ “#eSMS”. Khi người quan tâm bấm vào action, hệ thống sẽ gửi một tin nhắn có nội dung chứa trong data từ người quan tâm đến Official Account. Tin nhắn này sẽ hiện trên cửa sổ chat trên máy của người quan tâm.<br>- Type oa.open.phone: Khi người quan tâm click vào action, cửa sổ call trên điện thoại của người quan tâm sẽ được mở với thông tin số điện thoại là giá trị của phone_code. </li></ul></td></tr><tr><td>CallbackUrl</td><td>string</td><td>false</td><td>eSMS sẽ trả về kết quả của tin nhắn này.<br>Xem body mẫu <a href="https://samplefordevelopers.esms.vn/#cd0e23a3-5aa5-4198-a8bb-be0d8e450df9">ở đây</a>.<br>Xem chi tiết <a href="../callback-url.md">ở đây</a>.</td></tr></tbody></table>

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
