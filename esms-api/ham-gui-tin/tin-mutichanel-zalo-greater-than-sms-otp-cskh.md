---
description: >-
  Giải pháp Multi-Channel Messaging API cho phép bạn gửi tin nhắn đến khách hàng
  bằng tin ZNS và tự động gửi tin SMS nếu tin ZNS gửi thất bại.
---

# Gửi đa kênh: ZNS => SMS

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/MultiChannelMessage/](https://rest.esms.vn/MainService.svc/json/MultiChannelMessage/)\


* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

{% code overflow="wrap" %}
```json
curl --location 'https://rest.esms.vn/MainService.svc/json/MultiChannelMessage/' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey": "{{ApiKey}}",
    "SecretKey": "{{SecretKey}}",
    "Phone": "{{Phone}}",
    "Channels": [
        "zalo",
        "sms"
    ],
    "Data": [
        {
            "TempID": "{{TempID}}",
            "Params": ["{{param1}}","{{param2}}","{{param3}}"],
            "OAID": "{{OAID}}",
            "campaignid": "{{campaignid}}",
            "CallbackUrl": "{{CallbackUrl}}",
            "RequestId":"{{RequestId}}",
            "Sandbox":"{{Sandbox}}"
        },
        {
            "Content": "{{Content}}",
            "IsUnicode": "{{IsUnicode}}",
            "SmsType": "{{SmsType}}",
            "Brandname": "{{Brandname}}",
            "CallbackUrl": "{{CallbackUrl}}",
            "Sandbox":"{{Sandbox}}"
        }
    ]
}'
```
{% endcode %}

* **Cấu trúc body của request:**

<table><thead><tr><th width="152">Tham số</th><th width="135">Kiểu dữ liệu</th><th width="147" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey </td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr><tr><td>Phone</td><td>string</td><td>true</td><td>Số điện thoại nhận tin.</td></tr><tr><td>Params</td><td>string</td><td>true</td><td><p></p><p>Giá trị cần truyền cho các biến trong Template *Lưu ý:</p><ol><li>Các tham số truyền vào phải đúng thứ tự như template bạn đăng ký.</li><li>Nếu tham số trùng nhau chỉ cần truyền vào một tham số.</li></ol></td></tr><tr><td>TempID</td><td>string</td><td>true</td><td>Template của Zalo OA mà khách hàng đăng kí với eSMS.</td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này. <br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>RequestId</td><td>string</td><td>false</td><td>ID Tin nhắn của đối tác, dùng để kiểm tra ID này đã được hệ thống esms tiếp nhận trước đó hay chưa. <br>Ví dụ: RequestId=123456</td></tr><tr><td>campaignid</td><td>string</td><td>false</td><td>Tên chiến dịch gửi tin, tối đa 254 ký tự</td></tr><tr><td>RequestId</td><td>string</td><td>false</td><td>ID đối tác truyền sang để chặn trùng và đối soát khi cần.</td></tr><tr><td>CallbackUrl</td><td>string</td><td>false</td><td>Hàm gửi tin này sẽ truyền link callback riêng cho từng loại tin nhắn. <br>URL nhận kết quả gửi tin. <br>Xem body mẫu ZNS <a href="https://samplefordevelopers.esms.vn/#b98ca55e-3001-4446-b5bb-a4ab86127b0b">ở đây</a>. <br>Xem body mẫu SMS <a href="https://samplefordevelopers.esms.vn/#20f85e1f-3d9e-4ff4-bc4f-8d9c9edbc88a">ở đây</a>.<br>Xem chi tiết <a href="https://developers-v2.esms.vn/esms-api/callback-url">ở đây</a>.</td></tr><tr><td>Content</td><td>string</td><td>true</td><td>Nội dung tin nhắn.</td></tr><tr><td>IsUnicode</td><td>string</td><td>false</td><td>Gửi tin nhắn có dấu<br>0: Gửi tin không dấu.<br>1: Gửi tin nhắn có dấu.</td></tr><tr><td>SmsType </td><td>string</td><td>true</td><td>2: Tin CSKH</td></tr><tr><td>Brandname</td><td>string</td><td>true</td><td>Tên Brandname (tên công ty hay tổ chức khi gửi tin sẽ hiển thị trên tin nhắn đó). <br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>Sandbox</td><td>string</td><td>false</td><td>1: Tin gửi ở môi trường test, dùng để kiểm tra kết nối và các thông số tích hợp, không về tin nhắn, không trừ tiền.<br>0: Tin gửi ở môi trường bình thường, có về tin nhắn.</td></tr></tbody></table>

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

* **Cấu trúc trả về của response:**

| Thuộc tính   | Kiểu dữ liệu | Mô tả                                                                                             |
| ------------ | ------------ | ------------------------------------------------------------------------------------------------- |
| CodeResult   | string       | Mã trả về.                                                                                        |
| SMSID        | string       | ID của tin nhắn mới được tạo ra trên hệ thống eSMS. Dùng ID này để query lấy trạng thái tin nhắn. |
| ErrorMessage | string       | Thông tin lỗi trả về (nếu có lỗi).                                                                |

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu của các ngôn ngữ ở link:**</mark>_ [**Link Code mẫu .**](https://samplefordevelopers.esms.vn/#621e424e-1e47-4215-8d8a-21ef56f017b9)
