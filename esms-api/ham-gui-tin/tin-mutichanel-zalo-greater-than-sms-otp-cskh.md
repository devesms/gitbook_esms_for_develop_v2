---
description: >-
  Giải pháp Multi-Channel Messaging API cho phép bạn gửi tin nhắn đến khách hàng
  bằng tin ZNS và tự động gửi tin SMS nếu tin ZNS gửi thất bại.
---

# Tin nhắn đa kênh: Zalo => SMS OTP/CSKH

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
    "Phone": "0901888484",
    "Channels": [
        "zalo",
        "sms"
    ],
    "Data": [
        {
            "TempID": "205644",
            "Params": [
                "686868"
            ],
            "OAID": "4097311281936189049",
            "campaignid": "Gửi OTP",
            "CallbackUrl": "https://esms.vn/webhook/",
            "RequestId": "c82cd356-bf49-4113-9466-65a7f6359c97",
            "Sandbox":"0"
        },
        {
            "Content": "686868 la ma xac minh dang ky Baotrixemay cua ban",
            "IsUnicode": "0",
            "SmsType": "2",
            "Brandname": "Baotrixemay",
            "CallbackUrl": "https://esms.vn/webhook/",
            "RequestId": "c82cd356-bf49-4113-9466-65a7f6359c98",
            "Sandbox":"0"
        }
    ]
}'
```
{% endcode %}

* **Cấu trúc body của request:**

<table><thead><tr><th width="122.13330078125">Tham số</th><th width="135">Kiểu dữ liệu</th><th width="123.5333251953125" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey </td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr><tr><td>Phone</td><td>string</td><td>true</td><td>Số điện thoại nhận tin.</td></tr><tr><td>Channels</td><td>string</td><td>true</td><td>Các kênh đa kênh<br><strong>Giá trị này không thay đổi.</strong><br><strong>Không thay đổi thứ tự, không bỏ bớt kênh.</strong></td></tr><tr><td>Data</td><td>array</td><td>true</td><td>Cấu hình gửi tin của kênh ZNS và SMS.</td></tr></tbody></table>

**Cấu trúc thuộc tính Data\[0]**

<table><thead><tr><th width="122.7777099609375">Tham số</th><th width="133.3333740234375">Kiểu dữ liệu</th><th width="127.6666259765625" data-type="checkbox">Tinh bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>TempID</td><td>string</td><td>true</td><td>Template của Zalo OA mà khách hàng đăng kí với eSMS.</td></tr><tr><td>Params</td><td>array</td><td>true</td><td><p>Giá trị cần truyền cho các biến trong Template *Lưu ý:</p><ol><li>Các tham số truyền vào phải đúng thứ tự như template bạn đăng ký.</li><li>Nếu tham số trùng nhau chỉ cần truyền vào một tham số.</li></ol></td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này. <strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>campaignid</td><td>string</td><td>false</td><td>Tên chiến dịch gửi tin, tối đa 254 ký tự</td></tr><tr><td>CallbackUrl</td><td>string</td><td>false</td><td>Hàm gửi tin này sẽ truyền link callback riêng cho từng loại tin nhắn. URL nhận kết quả gửi tin. <br>Xem body mẫu ZNS <a href="https://samplefordevelopers.esms.vn/#b98ca55e-3001-4446-b5bb-a4ab86127b0b">ở đây</a>. <br>Xem body mẫu SMS <a href="https://samplefordevelopers.esms.vn/#20f85e1f-3d9e-4ff4-bc4f-8d9c9edbc88a">ở đây</a>. <br>Xem chi tiết <a href="https://developers-v2.esms.vn/esms-api/callback-url">ở đây</a>.</td></tr><tr><td>RequestId</td><td>string</td><td>false</td><td>ID đối tác truyền sang để chặn trùng và đối soD đối tác truyền sang để chặn trùng và đối soát khi cần.<br>Độ dài tối đa 50 ký tự.<br><strong>Mỗi RequestId truyền sang có hiệu lực chặn trong ngày.</strong></td></tr><tr><td>Sandbox</td><td>string</td><td>false</td><td>1: Tin gửi ở môi trường test, dùng để kiểm tra kết nối và các thông số tích hợp, không về tin nhắn, không trừ tiền.<br>0: Tin gửi ở môi trường bình thường, có về tin nhắn.</td></tr></tbody></table>

***

**Cấu trúc thuộc tính Data\[1]**

<table><thead><tr><th width="127.22222900390625">Tham số</th><th width="137.5555419921875">Kiểu dữ liệu</th><th width="124.5555419921875" data-type="checkbox">Tinh bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>Content</td><td>string</td><td>true</td><td>Nội dung tin nhắn.</td></tr><tr><td>IsUnicode</td><td>string</td><td>false</td><td>Gửi tin nhắn có dấu<br>0: Gửi tin không dấu.<br>1: Gửi tin nhắn có dấu.</td></tr><tr><td>SmsType</td><td>string</td><td>true</td><td>2: Tin CSKH</td></tr><tr><td>Brandname</td><td>string</td><td>true</td><td>Tên Brandname (tên công ty hay tổ chức khi gửi tin sẽ hiển thị trên tin nhắn đó). <br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>CallbackUrl</td><td>string</td><td>false</td><td>Hàm gửi tin này sẽ truyền link callback riêng cho từng loại tin nhắn. URL nhận kết quả gửi tin. <br>Xem body mẫu ZNS <a href="https://samplefordevelopers.esms.vn/#b98ca55e-3001-4446-b5bb-a4ab86127b0b">ở đây</a>. <br>Xem body mẫu SMS <a href="https://samplefordevelopers.esms.vn/#20f85e1f-3d9e-4ff4-bc4f-8d9c9edbc88a">ở đây</a>. <br>Xem chi tiết <a href="https://developers-v2.esms.vn/esms-api/callback-url">ở đây</a>.</td></tr><tr><td>RequestId</td><td>string</td><td>false</td><td>ID đối tác truyền sang để chặn trùng và đối soát khi cần.</td></tr><tr><td>Sandbox</td><td>string</td><td>false</td><td>1: Tin gửi ở môi trường test, dùng để kiểm tra kết nối và các thông số tích hợp, không về tin nhắn, không trừ tiền.<br>0: Tin gửi ở môi trường bình thường, có về tin nhắn.</td></tr></tbody></table>

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
