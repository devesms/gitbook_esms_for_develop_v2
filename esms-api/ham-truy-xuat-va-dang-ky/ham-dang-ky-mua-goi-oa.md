---
description: Đây là hàm dùng để đăng ký mua gói OA
---

# Hàm đăng ký mua gói OA

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/RegisOAPackageJson/](https://rest.esms.vn/MainService.svc/json/RegisOAPackageJson/)<br>

* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location 'https://rest.esms.vn/MainService.svc/json/RegisOAPackageJson/' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey":"{{ApiKey}}",
    "SecretKey":"{{SecretKey}}",
    "Dateactive":"{{Dateactive}}",
    "Duaration":"{{Duaration}}",
    "OAID":"{{OAID}}",
    "Package":{{Package}}
}'
```

* **Cấu trúc body của request:**

<table><thead><tr><th width="157">Tham số </th><th width="129">Kiểu dữ liệu </th><th width="154" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey của tài khoản.</td></tr><tr><td>Dateactive</td><td>string</td><td>true</td><td><p>Ngày kích hoạt OA:</p><p>Định dạng yyyy- mm - dd</p></td></tr><tr><td>Duaration</td><td>string</td><td>true</td><td>Thời gian gia hạn gói OA.</td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này. <br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>Package</td><td>string</td><td>true</td><td>Gói OA<br>- 1: Gói dùng thử<br>- 2: Gói nâng cao<br>- 3: Gói premium</td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```
{
    "CodeResult": "100",
    "ErrorMessage": "ViHAT is censoring trademark ownership",
    "ServicePreviewId": 52330
}
```

**Request hợp lệ.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th>Thuộc tính</th><th width="194">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Kết quả của Request.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông báo kết quả trả về.</td></tr><tr><td>ServicepreviewId</td><td>string</td><td>ID đăng ký OA phía eSMS.</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#f6fc7a5b-a326-4e4b-b7b1-0023151354f0)**.**
