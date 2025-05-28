# Tin Zalo Tư vấn đính kèm ảnh

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/SendZaloFollowerMessage\_V5\_post\_json/](http://rest.esms.vn/MainService.svc/json/SendZaloFollowerMessage_V5_post_json/)

* **Content Type:** <mark style="color:orange;">text/plain</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location 'https://rest.esms.vn/MainService.svc/json/SendZaloFollowerMessage_V5_post_json/' \
--header 'Content-Type: text/plain' \
--data '{
    "ApiKey": "{{ApiKey}}",
    "SecretKey": "{{SecretKey}}",
    "OAID": "{{OAID}}", 
    "Payload": {
        "recipient": {
            "user_id": "{{user_id}}"
        },
        "message": {
            "text": "Tin Zalo Tư vấn đính kèm ảnh",
            "attachment": {
                "type": "template",
                "payload": {
                    "template_type": "media",
                    "elements": [
                        {
                            "media_type": "image",
                            "url": "https://minio.esms.vn/blogimg/agent-1/BlogImg/full_3f8df17c-2d15-4ecb-b9fd-3bcc9cb0d97b.png"
                        }
                    ]
                }
            }
        }
    }
}'

// Truyền \r\n để gửi nội dung xuống dòng
```



* **Cấu trúc body của request:**

<table><thead><tr><th width="135">Tham số</th><th width="109">Kiểu dữ liệu </th><th width="136" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey eSMS cung cấp.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey eSMS cung cấp.</td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này. <br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>CallbackUrl</td><td>string</td><td>false</td><td>eSMS sẽ trả về kết quả của tin nhắn này.<br>Xem body mẫu <a href="https://samplefordevelopers.esms.vn/#cd0e23a3-5aa5-4198-a8bb-be0d8e450df9">ở đây</a>.<br>Xem chi tiết <a href="../callback-url.md">ở đây</a>.</td></tr><tr><td>SendDate</td><td>string</td><td>false</td><td>Thời gian hẹn gửi của tin.<br>Không truyền khi tin muốn tin nhắn gửi đi liền.<br>Định dạng: yyyy-mm-dd hh:MM:ss</td></tr><tr><td>Payload</td><td>Object</td><td>true</td><td>Chứa nội dung cần gửi</td></tr></tbody></table>

***

**Cấu trúc thuộc tính recipient**

<table><thead><tr><th width="136.99993896484375">Tham số</th><th width="113.888916015625">Kiểu dữ liệu </th><th width="139.5555419921875" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>user_id</td><td>string</td><td>true</td><td>ID của người nhận.</td></tr></tbody></table>

**Cấu trúc thuộc tính message**

<table><thead><tr><th width="143.22216796875">Tham số</th><th width="119.7777099609375">Kiểu dữ liệu </th><th width="125.5555419921875" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>text</td><td>string</td><td>true</td><td>Tiêu đề của ảnh<br>Giới hạn tối đa là 2.000 ký tự</td></tr><tr><td>attachment</td><td>Object</td><td>true</td><td>Attachment cần gửi.</td></tr></tbody></table>

**Cấu trúc thuộc tính message.attachment**

<table><thead><tr><th width="142.33331298828125">Tham số</th><th width="127.7777099609375">Kiểu dữ liệu </th><th width="126.8887939453125" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>type</td><td>string</td><td>true</td><td><p>Loại attachment.<br>Giá trị nhận vào bắt buộc:</p><ul><li><code>type</code> = template</li></ul></td></tr><tr><td>payload</td><td>Object</td><td>true</td><td>Chứa payload của attachment muốn gửi.</td></tr></tbody></table>

**Cấu trúc thuộc tính message.attachment.payload**

<table><thead><tr><th width="147">Tham số</th><th width="127.111083984375">Kiểu dữ liệu </th><th width="125.77783203125" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>template_type</td><td>string</td><td>true</td><td><p>Loại template<br>Với template gửi thông báo theo mẫu đính kèm ảnh, giá trị nhận vào là:</p><ul><li><code>template_type</code> = media</li></ul></td></tr><tr><td>elements</td><td>array</td><td>true</td><td>Các đối tượng của template.<br><strong>Lưu ý:</strong> Cấu trúc element thay đổi tùy theo loại template. <br>Với template media, danh sách element bao gồm tối đa 1 phần tử.</td></tr></tbody></table>

#### Cấu trúc thuộc tính message.attachment.payload.element <a href="#cau-truc-thuoc-tinh-messageattachmentpayloadelement" id="cau-truc-thuoc-tinh-messageattachmentpayloadelement"></a>

<table><thead><tr><th width="143.22216796875">Tham số</th><th width="127.7777099609375">Kiểu dữ liệu </th><th width="134" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>media_type</td><td>string</td><td>true</td><td><p>Loại media.</p><p></p><p>Các giá trị nhận vào:</p><ul><li>image: ảnh tĩnh</li><li>gif: ảnh động</li></ul></td></tr><tr><td>url</td><td>string</td><td>true</td><td><p>Đường dẫn đến ảnh<br>Các định dạng ảnh hỗ trợ: jpg và png<br>Dung lượng tối đa: 1MB<br><br><strong>Lưu ý:</strong></p><ul><li>kích thước ảnh tối ưu 16:9 và vùng safe zone 14:9</li></ul></td></tr></tbody></table>

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

<table><thead><tr><th width="145.53326416015625">Thuốc tính </th><th width="115.4000244140625">Kiểu dữ liệu </th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Request được gửi đến ViHAT thành công.<br><br><strong>Lưu ý:</strong> Mã phản hồi <strong>100</strong> chỉ xác nhận rằng yêu cầu đã được gửi thành công đến hệ thống ESMS, <strong>không phản ánh việc tin nhắn đã được gửi đến số điện thoại người nhận hay chưa</strong>.<br>Để theo dõi trạng thái cuối cùng của tin nhắn, quý khách vui lòng truyền thêm tham số <strong>CallbackUrl</strong>; hệ thống ESMS sẽ tự động gửi phản hồi (callback) đến địa chỉ này khi có trạng thái cuối của tin.</td></tr><tr><td>SMSID</td><td>string</td><td>ID tin nhắn do esms trả về.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi)</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#c0e00f1f-0c1f-4be1-8aac-f730d14e0e29)**.**
