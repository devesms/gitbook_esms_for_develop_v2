# Lấy Qouta tin Zalo theo OAID

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/ZNS/GetQuota/](https://rest.esms.vn/MainService.svc/json/ZNS/GetQuota/)\


* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location 'https://rest.esms.vn/MainService.svc/json/ZNS/GetQuota/' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey": "{{ApiKey}}",
    "SecretKey": "{{SecretKey}}",
    "OAID": "{{OAID}}"
}'
```

* **Câu trúc body của request:**

<table><thead><tr><th width="151">Tham số</th><th width="134">Kiểu dữ liệu </th><th width="141" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey của tài khoản.</td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. <br>Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này.<br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```
{
    "CodeResult": "100",
    "ErrorMessage": "success",
    "DailyQuota": 500,
    "RemainingQuota": 500
}
```

**Request hợp lệ.**
{% endtab %}

{% tab title="101" %}
```
{
    "CodeResult": "101",
    "ErrorMessage": "Authorize Failed"
}
```

**Sai thông tin ApiKey/SecretKey.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th width="184">Thuộc tính</th><th width="157">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>DailyQuota</td><td>string</td><td>Tổng số tin được gửi trong ngày.</td></tr><tr><td>RemainingQuota</td><td>string</td><td>Số tin còn lại.</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#f7a3f3f8-3bb2-4b53-af42-66afe6966a69)**.**
