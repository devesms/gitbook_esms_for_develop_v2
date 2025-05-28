# Tin Zalo Tư vấn dạng yêu cầu thông tin người dùng

## HTTP request

\
<mark style="color:yellow;">**POST**</mark> [https://rest.esms.vn/MainService.svc/json/SendZaloFollowerMessage\_V5\_post\_json/](http://rest.esms.vn/MainService.svc/json/SendZaloFollowerMessage_V5_post_json/)



* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location 'https://rest.esms.vn/MainService.svc/json/SendZaloFollowerMessage_V5_post_json/' \
--header 'Content-Type: application/json' \
--data '{
"ApiKey": "{{ApiKey}}",
"SecretKey": "{{SecretKey}}",
"OAID": "{{OAID}}",
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
                            "title": "OA Chatbot",
                            "subtitle": "Đang yêu cầu thông tin từ bạn",
                            "image_url": "https://minio.esms.vn/blogimg/agent-1/BlogImg/full_cccc34d4-3a46-4644-8613-1b226203c5d5.png"
                        }
                    ]
                }
            }
        }
    }
}'
```

* **Cấu trúc body của request:**

<table><thead><tr><th width="135">Tham số</th><th width="120">Kiểu dữ liệu</th><th width="152" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này. <br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>CallbackUrl</td><td>string</td><td>false</td><td>URL nhận kết quả gửi tin. <br>Xem body mẫu <a href="https://samplefordevelopers.esms.vn/#aabcd08e-e84a-4e9a-9598-c894af957d5b">ở đây</a>. <br>Xem chi tiết <a href="https://developers-v2.esms.vn/esms-api/callback-url">ở đây</a>.</td></tr><tr><td>SendDate</td><td>string</td><td>false</td><td>Thời gian hẹn gửi của tin.<br>Không truyền khi tin muốn tin nhắn gửi đi liền.<br>Định dạng: yyyy-mm-dd hh:MM:ss</td></tr><tr><td>Payload</td><td>Object</td><td>true</td><td>Chứa nội dung cần gửi</td></tr></tbody></table>

**Cấu trúc thuộc tính recipient**

<table><thead><tr><th width="141.26666259765625">Tham số</th><th width="115.2666015625">Kiểu dữ liệu</th><th width="152.199951171875" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>user_id</td><td>string</td><td>true</td><td>ID của người nhận.</td></tr></tbody></table>

**Cấu trúc thuộc tính message**

<table><thead><tr><th width="140.199951171875">Tham số</th><th width="118.466796875">Kiểu dữ liệu</th><th width="146.933349609375" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>attachment</td><td>Object</td><td>true</td><td>Chứa payload của attachment muốn gửi</td></tr><tr><td>type</td><td>string</td><td>true</td><td><p>Loại attachment.<br></p><p>Giá trị nhận vào bắt buộc:</p><ul><li><code>type</code> = template</li></ul></td></tr></tbody></table>

**Cấu trúc thuộc tính message.attachment**

<table><thead><tr><th width="141.26666259765625">Tham số</th><th width="117.400146484375">Kiểu dữ liệu</th><th width="145.8665771484375" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>title</td><td>string</td><td>true</td><td>Tiêu đề hiển thị của template<br>Lưu ý: Hỗ trợ tối đa 100 ký tự</td></tr><tr><td>subtitle</td><td>string</td><td>true</td><td>Tiêu đề phụ của template<br>Lưu ý: Hỗ trợ tối đa 500 ký tự</td></tr><tr><td>image_url</td><td>string</td><td>true</td><td>Đường dẫn đến ảnh.</td></tr></tbody></table>



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

<table><thead><tr><th width="146.33331298828125">Thuốc tính</th><th width="122.6666259765625">Kiểu dữ liệu </th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Request được gửi đến ESMS thành công.<br><br><strong>Lưu ý:</strong> Mã phản hồi <strong>100</strong> chỉ xác nhận rằng yêu cầu đã được gửi thành công đến hệ thống ESMS, <strong>không phản ánh việc tin nhắn đã được gửi đến số điện thoại người nhận hay chưa</strong>.<br>Để theo dõi trạng thái cuối cùng của tin nhắn, quý khách vui lòng truyền thêm tham số <strong>CallbackUrl</strong>; hệ thống ESMS sẽ tự động gửi phản hồi (callback) đến địa chỉ này khi có trạng thái cuối của tin.</td></tr><tr><td>SMSID</td><td>string</td><td>ID tin nhắn do esms trả về.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi).</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [_**Link code mẫu**_](https://samplefordevelopers.esms.vn/#a8181709-4215-4375-bdb3-3e6c5a0a23c4)_**.**_
