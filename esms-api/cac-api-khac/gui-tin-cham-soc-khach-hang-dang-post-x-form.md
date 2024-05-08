# Gửi tin chăm sóc khách hàng dạng POST X-Form

## HTTP request

\
<mark style="color:yellow;">**POST**</mark> [https://rest.esms.vn/MainService.svc/json/SendMultipleMessage\_V4\_post/](https://rest.esms.vn/MainService.svc/json/SendMultipleMessage\_V4\_post/)

* **Content Type:** <mark style="color:orange;">application/x-www-form-urlencoded</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```
curl --location 'https://rest.esms.vn/MainService.svc/json/SendMultipleMessage_V4_post/' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'Phone={{Phone}}' \
--data-urlencode 'Content={{Content}}' \
--data-urlencode 'Apikey={{ApiKey}}' \
--data-urlencode 'SecretKey={{SecretKey}}' \
--data-urlencode 'SmsType=2' \
--data-urlencode 'Brandname={{Brandname}}'
```

* **Cấu trúc body của request:**

<table><thead><tr><th width="165">Tham số</th><th width="158">Kiểu dữ liệu </th><th width="137" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>Phone</td><td>string</td><td>true</td><td>Số điện thoại nhận tin.</td></tr><tr><td>Content</td><td>string</td><td>true</td><td>Nội dung tin nhắn.</td></tr><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr><tr><td>SmsType</td><td>number</td><td>true</td><td>Loại tin nhắn<br>2: Tin CSKH.</td></tr><tr><td>Brandname</td><td>string</td><td>true</td><td>Tên Brandname (tên công ty hay tổ chức khi gửi tin sẽ hiển thị trên tin nhắn đó). <br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr></tbody></table>

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

{% tab title="Untitled" %}
```json
{
  "error": "Invalid request"
}
```

**Kiểm tra lại thông tin kết nối hoặc liên hệ bộ phận chăm sóc khách hàng để được hỗ trợ khi gặp lỗi này.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th width="190">Thuộc tính</th><th width="228">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Mã trả về.</td></tr><tr><td>SMSID</td><td>string</td><td>ID tin nhắn do esms trả về.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi).</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#850974b9-12cf-46f5-946c-e8e15aa3585b)**.**

