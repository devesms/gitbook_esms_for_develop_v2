---
description: >-
  Đây là hàm cơ bản đầu tiên mà bạn nên thử, hàm giúp bạn lấy về số dư trong tài
  khoản của bạn.
---

# Hàm lấy số dư tài khoản



## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [http://rest.esms.vn/MainService.svc/json/GetBalance\_json](http://rest.esms.vn/MainService.svc/json/GetBalance\_json)\


* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location 'http://rest.esms.vn/MainService.svc/json/GetBalance_json' \
--header 'Content-Type: application/json' \
--data '{
"ApiKey":"{{ApiKey}}",
"SecretKey":"{{SecretKey}}"
}'
```

* **Cấu trúc body của request:**

<table><thead><tr><th width="145">Tham số</th><th width="140">Kiểu dữ liệu</th><th data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey của tài khoản.</td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```json
{
    "Balance": 36693,
    "CodeResponse": "100",
    "UserID": 9999
}
```

**Request hợp lệ.**
{% endtab %}

{% tab title="101" %}


```json
{
    "Balance": 0,
    "CodeResponse": "101",
    "ErrorMessage": "Authorize Failed"
}
```

**Sai thông tin ApiKey/SecretKey.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

| Thuộc tính   | Kiểu dữ liệu | Mô tả                           |
| ------------ | ------------ | ------------------------------- |
| Balance      | string       | Số dư tài khoản chính.          |
| CodeResponse | string       | Mã trả về.                      |
| UserID       | string       | Id user tài khoản của hệ thống. |

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#571b0b39-3ce0-4102-817c-132beb05c7d8)**.**
