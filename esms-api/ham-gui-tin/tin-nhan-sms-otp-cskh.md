---
description: 'LƯU Ý QUAN TRỌNG:'
icon: comment-sms
---

# Tin nhắn SMS OTP/CSKH (Khuyên Dùng)

* **Liên hệ nhân viên chăm sóc khách hàng nếu muốn gửi tên thương hiêu và nội dung riêng của bạn.**
* **Nội dung (Content) tin nhắn test phải đúng như request mẫu, đổi nội dung tin sẽ thất bại.**
* **Thay đổi giá trị Brandname và Content ở request mẫu có thể tin nhắn không gửi được nếu chưa được đăng ký với nhà mạng.**
* Đổi giá trị CODE ở nội dung để test nhiều tin, tránh bị nhà mạng chặn tin spam.

## HTTP request

<mark style="color:yellow;">**`POST`**</mark> **https://rest.esms.vn/MainService.svc/json/SendMultipleMessage\_V4\_post\_json/**

* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location --request POST 'https://rest.esms.vn/MainService.svc/json/SendMultipleMessage_V4_post_json/' \
--header 'Content-Type: application/json' \
--data-raw '{
   "ApiKey": "APIKEYCUABAN",
   "Content": "CODE la ma xac minh dang ky Baotrixemay cua ban",
   "Phone": "0901888484",
   "SecretKey": "SECRETKEYCUABAN",
   "Brandname": "Baotrixemay",
   "SmsType": "2",
   "IsUnicode": "0",
   "campaignid": "Cảm ơn sau mua hàng tháng 7",
   "RequestId": "c82cd356-bf49-4113-9466-65a7f6359c96",
   "CallbackUrl": "https://esms.vn/webhook/"
// Brandname và Content trên dùng để thử nghiệm. Chỉ gửi được với nội dung này, thay đổi sẽ sai mẫu và tin nhắn không được gửi.
// CODE có thể tùy chỉnh, tối đa 8 ký tự gồm số hoặc chữ. Ví dụ: 2803 la ma xac minh dang ky Baotrixemay cua ban
// Mỗi số điện thoại và Content giống nhau chỉ được phép gửi một tin trong 5 phút. Hãy thay đổi số điện thoại hoặc Content để thử nghiệm các tin nhắn liên tiếp.
// Cần dùng Brandname/Content khác, hãy liên hệ nhân viên kinh doanh tại https://esms.vn/ (thông tin ở bên phải màn hình sau khi đăng nhập).
}'
```

* **Cấu trúc body của request:**&#x20;

<table><thead><tr><th width="148">Tham số</th><th width="136">Kiểu dữ liệu</th><th width="134" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey eSMS cung cấp.</td></tr><tr><td>Content</td><td>string</td><td>true</td><td>Nội dung tin nhắn.</td></tr><tr><td>Phone</td><td>string</td><td>true</td><td>Số điện thoại nhận tin nhắn.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey eSMS cung cấp.</td></tr><tr><td>Brandname</td><td>string</td><td>true</td><td>Tên Brandname (tên công ty hay tổ chức khi gửi tin sẽ hiển thị trên tin nhắn). <strong>Chú ý: Phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>SmsType</td><td>string</td><td>true</td><td>Loại tin nhắn ID 2 là CSKH.</td></tr><tr><td>IsUnicode</td><td>string</td><td>false</td><td><p>Gửi nội dung có dấu:<br>1: Có dấu.</p><p>0: Không dấu.</p></td></tr><tr><td>Sandbox</td><td>string</td><td>false</td><td>1: Tin gửi ở môi trường test, dùng để kiểm tra kết nối và các thông số tích hợp, không về tin nhắn, không trừ tiên. <br>0: Tin gửi ở môi trường bình thường, có về tin nhắn.</td></tr><tr><td>RequestId</td><td>string</td><td>false</td><td>ID đối tác truyền sang để chặn trùng và đối soát khi cần.<br>Độ dài tối đa 50 ký tự.<br><strong>Mỗi RequestId truyền sang có hiệu lực chặn trong ngày.</strong></td></tr><tr><td>SendDate</td><td>string</td><td>false</td><td>Thời gian hẹn gửi của tin. <br>Không truyền khi tin muốn tin nhắn gửi đi liền.<br>Định dạng: yyyy-mm-dd hh:MM:ss</td></tr><tr><td>campaignid</td><td>string</td><td>false</td><td>Tên chiến dịch.</td></tr><tr><td>CallbackUrl</td><td>string</td><td>false</td><td>URL nhận kết quả gửi tin. <br>Xem body mẫu <a href="https://samplefordevelopers.esms.vn/#20f85e1f-3d9e-4ff4-bc4f-8d9c9edbc88a">ở đây</a>.<br>Xem chi tiết <a href="../callback-url.md">ở đây</a>.</td></tr></tbody></table>



***

* **Response**

{% tabs %}
{% tab title="100" %}
```json
{
    "CodeResult": "100",
    "CountRegenerate": 0,
    "SMSID": "d533459ee42b2b9525ba9eabf6a8156"
}
```

**Request hợp lệ.**
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

{% tab title="124" %}
```json
{
    "CodeResult": "124",
    "CountRegenerate": 0,
    "ErrorMessage": "Request exist 1",
    "SendStatus": "5"
}
```

**RequestId đã tồn tại.**
{% endtab %}

{% tab title="146" %}
{% code overflow="wrap" %}
```json
{
  "CodeResult": "146",
  "CountRegenerate": 0,
  "ErrorMessage": "Sai template Brandname CSKH",
  "SMSID": "3f5ec8c71c4a4ccea311f731dfeaa133156"
}
```
{% endcode %}

**Template CSKH chưa được đăng ký.**
{% endtab %}

{% tab title="99" %}
```json
{
  "error": "Invalid request"
}
```

**Kiểm tra lại thông tin kết nối hoặc liên hệ bộ phận chăm sóc khách hàng để được hỗ trợ khi gặp lỗi này.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

| Thuộc tính   | Kiểu dữ liệu | Mô tả                              |
| ------------ | ------------ | ---------------------------------- |
| CodeResult   | string       | Mã trả về.                         |
| SMSID        | string       | ID tin nhắn do esms trả về.        |
| ErrorMessage | string       | Thông tin lỗi trả về (nếu có lỗi). |

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#850974b9-12cf-46f5-946c-e8e15aa3585b)**.**

