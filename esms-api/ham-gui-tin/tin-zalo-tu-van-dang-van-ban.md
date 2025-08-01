# Tin Zalo Tư vấn dạng văn bản

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/SendZaloFollowerMessage\_V4\_post\_json/](http://rest.esms.vn/MainService.svc/json/SendZaloFollowerMessage_V5_post_json/)

* **Content Type:** <mark style="color:orange;">text/plain</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location 'https://rest.esms.vn/mainservice.svc/json/SendZaloFollowerMessage_V4_post_json/' \
--header 'Content-Type: application/json' \
--data '{
   "ApiKey":"{{ApiKey}}",
   "SecretKey":"{{SecretKey}}",
   "OAID":"{{OAID}}",
   "User_id":"{{User_id}}",
   "Content":"Tin Zalo Tư vấn dạng văn bản",
   "RequestId": "96accf59-0c41-4bc7-a5c4-4a466c2e41c2",
   "CallbackUrl":{{CallbackUrl}}"
}'
```



* **Cấu trúc body của request:**

<table><thead><tr><th width="125">Tham số</th><th width="123">Kiểu dữ liệu </th><th width="134" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey eSMS cung cấp.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey eSMS cung cấp.</td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này. <br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>User_id</td><td>string</td><td>true</td><td>Userid cần gửi đến, đây là userid của zalo.</td></tr><tr><td>Content</td><td>string</td><td>true</td><td>Tiêu đề của ảnh<br>Giới hạn tối đa là 2.000 ký tự</td></tr><tr><td>RequestId</td><td>string</td><td>false</td><td>ID đối tác truyền sang để chặn trùng và đối soát khi cần.<br>Độ dài tối đa 50 ký tự.<br><strong>Mỗi RequestId truyền sang có hiệu lực chặn trong 24h.</strong></td></tr><tr><td>CallbackUrl</td><td>string</td><td>false</td><td>eSMS sẽ trả về kết quả của tin nhắn này.<br>Xem body mẫu <a href="https://samplefordevelopers.esms.vn/#cd0e23a3-5aa5-4198-a8bb-be0d8e450df9">ở đây</a>.<br>Xem chi tiết <a href="../callback-url.md">ở đây</a>.</td></tr></tbody></table>

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

<table><thead><tr><th width="156.199951171875">Thuốc tính </th><th width="145.6666259765625">Kiểu dữ liệu </th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Request được gửi đến ESMS thành công.<br><br><strong>Lưu ý:</strong> Mã phản hồi <strong>100</strong> chỉ xác nhận rằng yêu cầu đã được gửi thành công đến hệ thống ESMS, <strong>không phản ánh việc tin nhắn đã được gửi đến số điện thoại người nhận hay chưa</strong>.<br>Để theo dõi trạng thái cuối cùng của tin nhắn, quý khách vui lòng truyền thêm tham số <strong>CallbackUrl</strong>; hệ thống ESMS sẽ tự động gửi phản hồi (callback) đến địa chỉ này khi có trạng thái cuối của tin.</td></tr><tr><td>SMSID</td><td>string</td><td>ID tin nhắn do esms trả về.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi)</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#c0e00f1f-0c1f-4be1-8aac-f730d14e0e29)**.**
