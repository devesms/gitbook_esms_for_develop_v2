---
description: Đây là hàm dùng để đăng ký template ZNS
---

# Hàm đăng ký template Zalo

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/RegisZNSTemplateJson/](https://rest.esms.vn/MainService.svc/json/RegisZNSTemplateJson/)<br>

* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>



```json
curl --location 'https://rest.esms.vn/MainService.svc/json/RegisZNSTemplateJson/' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey":"{{ApiKey}}",
    "SecretKey":"{{SecretKey}}",
    "Content":"{{Content}}",
    "ImageUrl":"{{ImageUrl}}",
    "CTA1":"{{CTA1}}",
    "CTA2":"{{CTA2}}",
    "OAID":"{{OAID}}",
    "SmsType":"{{SmsType}}",
    "CallbackUrl":"{{CallbackUrl}}"
}'
```

* **Cấu trúc body của request:**

<table><thead><tr><th width="163">Tham số</th><th width="130">Kiểu dữ liệu </th><th width="148" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey của tài khoản.</td></tr><tr><td>Content</td><td>string</td><td>true</td><td>Nội dung mẫu của template cần đăng ký.</td></tr><tr><td>ImageURL</td><td>string</td><td>true</td><td>Link hình ảnh LOGO OA, chấp nhận link đuôi PNG, kích thước 400x69, tách nền màu nền đen hoặc trắng.</td></tr><tr><td>CTA 1</td><td>string</td><td>false</td><td>Link CTA thứ nhất.</td></tr><tr><td>CTA 2</td><td>string</td><td>false</td><td>Link CTA thứ hai.</td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này. <br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>SmsType</td><td>string</td><td>true</td><td>24: khi đăng ký template zalo ưu tiên.<br>25: khi đăng ký template zalo bình thường.</td></tr><tr><td>CallbackUrl</td><td>string</td><td>false</td><td>Link nhận trạng thái template đăng ký<br>0: Đăng ký thất bại.<br>1: eSMS tiếp nhận thành công.<br>2: Đăng ký thành công.</td></tr></tbody></table>

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

<table><thead><tr><th width="205">Thuốc tính</th><th width="160">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Kết quả của Request.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông báo kết quả trả về.</td></tr><tr><td>ServicepreviewId</td><td>string</td><td>ID template yêu cầu đăng ký.</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#f25701ff-8ce7-4c5d-bca6-c7eafd158977)**.**
