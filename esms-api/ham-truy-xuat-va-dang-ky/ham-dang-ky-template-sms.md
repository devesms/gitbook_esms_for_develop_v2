---
description: Đây là hàm dùng để đăng ký template SMS chăm sóc khách hàng.
---

# Hàm đăng ký template SMS

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/SubServicePreviewJson/](https://rest.esms.vn/MainService.svc/json/SubServicePreviewJson/)<br>

* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location 'https://rest.esms.vn/MainService.svc/json/SubServicePreviewJson/' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey": "{{ApiKey}}",
    "AssetsUrl": "{{AssetsUrl}}",
    "Brandname": "{{Brandname}}",
    "CallbackUrl": "{{CallbackUrl}}",
    "Content": "{{Content}}",
    "IsUnicode": "{{IsUnicode}}",
    "CustomerEmail": "{{CustomerEmail}}",
    "CustomerName": "{{CustomerName}}",
    "CustomerPhone": "{{CustomerPhone}}",
    "SecretKey": "{{SecretKey}}",
    "ServiceType": 2,
    "SmsType": {{SmsType}}
}'
```

* **Cấu trúc body của request:**

<table><thead><tr><th width="167">Tham số</th><th width="126">Kiểu dữ liệu </th><th width="134" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey của tài khoản.</td></tr><tr><td>Content</td><td>string</td><td>true</td><td>Nội dung mẫu của template cần đăng ký<br>Ví dụ: {<strong>Biến</strong>:<strong>Số lượng ký tự mong muốn</strong>}</td></tr><tr><td>AssetsUrl</td><td>string</td><td>false</td><td>Là đường dẫn để tài 1 tài liệu nào đó ở server của đối tác. tài liệu này phục vụ cho việc xác thực đăng ký.</td></tr><tr><td>Brandname</td><td>string</td><td>true</td><td>BrandName cần đăng ký template (lưu ý: Brandname này phải được add vào tài khoản thì mới đăng ký được)</td></tr><tr><td>IsUnicode</td><td>string</td><td>false</td><td>Đăng ký nội dung có dấu<br>1: Có dấu<br>0: Không dấu</td></tr><tr><td>CustomerEmail</td><td>string</td><td>false</td><td>Email tài khoản KH cuối cần đăng ký brandname.</td></tr><tr><td>CustomerName</td><td>string</td><td>false</td><td>Số điện thoại KH cuối cần Đăng ký brandname.</td></tr><tr><td>CustomerPhone</td><td>string</td><td>false</td><td>CustomerPhone.</td></tr><tr><td>ServiceType</td><td>string</td><td>true</td><td>ServiceType = 2 là đăng ký Template CSKH hoặc Cố định giá rẻ.</td></tr><tr><td>SmsType</td><td>string</td><td>true</td><td>2: khi đăng ký template CSKH .<br>8: khi đăng ký template Cố định giá rẻ.</td></tr><tr><td>CallbackUrl</td><td>string</td><td>false</td><td>Sẽ nhận kết quả trả về của eSMS sau khi yêu cầu đăng ký template. <br>0: Đăng ký thất bại.<br>1: eSMS tiếp nhận thành công.<br>2: Đăng ký thành công.</td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```json
{
    "CodeResult": "100",
    "ErrorMessage": "ViHAT is moderating your template",
    "ServicePreviewId": 52353
}
```

**Request hợp lệ.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th width="204">Thuốc tính</th><th width="166">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Kết quả của Request.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông báo kết quả trả về.</td></tr><tr><td>ServicepreviewId</td><td>string</td><td>ID template yêu cầu đăng ký.</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#12f5e80f-025c-4c9c-9c9c-b42622ea8af2)**.**
