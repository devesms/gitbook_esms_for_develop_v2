---
description: Hàm cho phép bạn gọi API check code xem đã sử dụng, hết hạn.
---

# Hàm check code

## HTTP request

\
<mark style="color:green;">**`GET`**</mark>  <mark style="color:blue;">https://rest.esms.vn/MainService.svc/json/CheckCodeGen\_V4\_get?ApiKey=\{{ApiKey\}}\&SecretKey=\{{SecretKey\}}\&Phone=\{{{Phone\}}\&Code=\{{Code\}}</mark>

\
**Response Type:** <mark style="color:orange;">application/json</mark>

{% code overflow="wrap" %}
```json
curl --location --globoff 'https://rest.esms.vn/MainService.svc/json/CheckCodeGen_V4_get?ApiKey={{ApiKey}}&SecretKey={{SecretKey}}&Phone={{{Phone}}&Code={{Code}}'
```
{% endcode %}

* **Cấu trúc body của request:**

<table><thead><tr><th width="130">Tham số</th><th width="129">Kiểu dữ liệu</th><th width="139" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr><tr><td>Phone</td><td>string</td><td>true</td><td>Số điện thoại người nhận code.</td></tr><tr><td>Code</td><td>string</td><td>true</td><td>Mã code cần check.</td></tr></tbody></table>

* **Response:**

{% tabs %}
{% tab title="100" %}
```json
{
 "CodeResult": "100",
 "CountRegenerate": 0,
 "ErrorMessage": "0901888484, Content: Success!"
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

<table><thead><tr><th width="234">Thuốc tính </th><th width="165">Kiểu dữ liệu </th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Mã trả về.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi).</td></tr><tr><td>Content</td><td>string</td><td>Trạng thái của code.</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#62b4ccfb-c812-44f3-9cf5-e8c5b99e7b06)**.**
