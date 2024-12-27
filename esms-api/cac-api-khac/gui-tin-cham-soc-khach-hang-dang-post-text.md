---
description: >-
  API dùng để gửi tin Quảng cáo đến khách hàng. Mỗi request tối thiểu 30 số để
  được duyệt tin và tối đa 5000 số.
---

# Gửi tin chăm sóc khách hàng dạng POST TEXT

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/SendMultipleMessage\_V4](https://rest.esms.vn/MainService.svc/json/SendMultipleMessage_V4)

* **Content Type:** <mark style="color:orange;">application/text/plain</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```
curl --location 'https://rest.esms.vn/MainService.svc/json/SendMultipleMessage_V4/' \
--header 'Content-Type: text/plain' \
--data '<RQST>
<APIKEY><{{ApiKey}}</APIKEY>
<SECRETKEY>{{SecretKey}}</SECRETKEY>
<CONTENT>{{Content}}</CONTENT>
<SMSTYPE>2</SMSTYPE>
<BRANDNAME>{{Brandname}}</BRANDNAME>
<SENDDATE>{{senddate}}</SENDDATE>
<CALLBACKURL>{{callbackUrl}}}</CALLBACKURL>
<CONTACTS>
<CUSTOMER><PHONE>{{Phone}}</PHONE></CUSTOMER>
</CONTACTS>
</RQST>'
```

* **Cấu trúc body của request:**

<table><thead><tr><th width="167">Tham số</th><th width="149">Định nghĩa</th><th width="141" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>APIKEY</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SECRETKEY</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr><tr><td>CONTENT</td><td>string</td><td>true</td><td>Nội dung tin nhắn.</td></tr><tr><td>SMSTYPE</td><td>string</td><td>true</td><td>Loại tin nhắn<br>1: Tin quảng cáo.</td></tr><tr><td>BRANDNAME</td><td>string</td><td>true</td><td>Tên Brandname (tên công ty hay tổ chức khi gửi tin sẽ hiển thị trên tin nhắn đó). <br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>PHONE</td><td>string</td><td>true</td><td>Số điện thoại nhận tin nhắn.</td></tr><tr><td>SENDDATE</td><td>string</td><td>false</td><td>Thời gian hẹn gửi của tin. <br>Không truyền khi tin muốn tin nhắn gửi đi liền.<br>Định dạng: yyyy-mm-dd hh:MM:ss</td></tr><tr><td>CALLBACKURL</td><td>string</td><td>false</td><td>URL nhận kết quả gửi tin. <br>Xem body mẫu <a href="https://samplefordevelopers.esms.vn/#eeaca8c5-ef65-4fed-ac2e-697d0360327b">ở đây</a>. <br>Xem chi tiết <a href="https://developers-v2.esms.vn/esms-api/callback-url">ở đây</a>.</td></tr></tbody></table>

***

* **Response:**

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

{% tab title="107" %}
```
{
    "CodeResult": "107",
    "CountRegenerate": 0,
    "ErrorMessage": "Each request has at least 30 numbers to be approved"
}
```

**Tạo tin không thành công. Mỗi request phải có ít nhất 30 số điện thoại hợp lệ.**
{% endtab %}

{% tab title="124" %}
```
{
    "CodeResult": "124",
    "CountRegenerate": 0,
    "ErrorMessage": "Request exist 1"
}
```

**Trùng RequestId. Mỗi RequestId chỉ được gửi cho 1 request.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th width="225">Thuộc tính</th><th width="194">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Mã trả về.</td></tr><tr><td>SMSID</td><td>string</td><td>ID tin nhắn do esms trả về.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi).</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#850974b9-12cf-46f5-946c-e8e15aa3585b)**.**
