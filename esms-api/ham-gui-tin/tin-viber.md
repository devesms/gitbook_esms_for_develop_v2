---
description: Cho phép bạn gửi tin nhắn đến số điện thoại đang sử dụng Viber.
---

# Tin Viber



<figure><img src="../../.gitbook/assets/hình lên viber.png" alt=""><figcaption><p>Hình mẫu tin nhắn Viber</p></figcaption></figure>

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/Send\_Multiple\_Sms\_OTT/](http://rest.esms.vn/MainService.svc/json/Send\_Multiple\_Sms\_OTT/)



* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

{% code overflow="wrap" %}
```json
curl --location 'https://rest.esms.vn/MainService.svc/json/Send_Multiple_Sms_OTT/' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey": "{{ApiKey}}",
    "SecretKey": "{{SecretKey}}",
    "Brandname": "{{Brandname}}",
    "SmsType": "23",
    "Content": "{{Content}}",
    "OttImgUrl": "{{OttImgUrl}}",
    "OttLabel": "{{OttLabel}}",
    "OttUrl": "{{OttUrl}}",
    "Phones": [
        "{{Phone1}}","{{Phone2}}","{{Phone3}}"
    ],
    "IsSandBox": "{{IsSandBox}}",
    "CallbackUrl": "{{CallbackUrl}}"
}'
```
{% endcode %}

* **Cấu trúc body của request:**

<table><thead><tr><th width="175">Tham số</th><th width="148">Kiểu dữ liệu</th><th width="143" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản</td></tr><tr><td>Brandname</td><td>string</td><td>true</td><td>Tên Brandname (tên công ty hay tổ chức khi gửi tin sẽ hiển thị trên tin nhắn đó). Chú ý: sẽ phải đăng ký trước khi sử dụng.</td></tr><tr><td>SmsType</td><td>number</td><td>true</td><td>Loại tin nhắn<br>23: Tin nhắn OTT Viber.</td></tr><tr><td>Content</td><td>string</td><td>true</td><td>Nội dung gửi đến người nhận</td></tr><tr><td>OttImgUrl</td><td>string</td><td>false</td><td>Đường dẫn hình ảnh.</td></tr><tr><td>OTTLabel</td><td>string</td><td>false</td><td>Tên nút.</td></tr><tr><td>OttUrl</td><td>string</td><td>false</td><td>Đường dẫn tên nút.</td></tr><tr><td>Phones</td><td>string</td><td>true</td><td>Số điện thoại người nhận.</td></tr><tr><td>IsSandBox</td><td>number</td><td>false</td><td>1: Tin gửi ở môi trường test, dùng để kiểm tra kết nối và các thông số tích hợp, không về tin nhắn, không trừ tiền.<br>0: Tin gửi ở môi trường bình thường, có về tin nhắn.</td></tr><tr><td>CallbackUrl</td><td>string</td><td>false</td><td>URL nhận kết quả gửi tin. <br>Xem body mẫu <a href="https://samplefordevelopers.esms.vn/#6acfe1fc-8601-4bce-9549-65bf17f279b1">ở đây</a>. <br>Xem chi tiết <a href="https://developers-v2.esms.vn/esms-api/callback-url">ở đây</a>.</td></tr></tbody></table>

* <mark style="color:yellow;">**`Lưu ý:`**</mark> Tin nhắn Viber có bốn kiểu nội dung để lựa chọn như sau:\
  \- <mark style="color:green;">**Kiểu Văn bản - Ảnh- Nút**</mark> => Khi request truyền các tham số: Content, OttImgUrl, OttUrl, OTTLabel.\
  \- <mark style="color:green;">**Kiểu Văn bản - Nút**</mark> => Khi request truyền các tham số: Content, OttUrl, OTTLabel.\
  \- <mark style="color:green;">**Kiểu Ảnh**</mark> => Khi request truyền các tham số: OttImgUrl.\
  \- <mark style="color:green;">**Kiểu Văn bản**</mark> => Khi request truyền các tham số: Content.

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

{% tab title="104" %}
```json
{
    "CodeResult": "104",
    "CountRegenerate": 0,
    "ErrorMessage": "Brand name code is not exist"
}
```

**Brandname truyền chưa đúng hoặc chưa được active.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

| Thuộc tính   | Kiểu dữ liệu | Mô tả                              |
| ------------ | ------------ | ---------------------------------- |
| CodeResult   | string       | Mã trả về.                         |
| SMSID        | string       | ID tin nhắn do esms trả về.        |
| ErrorMessage | string       | Thông tin lỗi trả về (nếu có lỗi). |

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#9a4ce369-8f02-43cb-9693-f2e9ab827af3)**.**
