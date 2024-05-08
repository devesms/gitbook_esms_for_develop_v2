# Hàm gửi tin nhắn Zalo dạng X-Form

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/SendMultipleMessage\_V4\_post/](https://rest.esms.vn/MainService.svc/json/SendMultipleMessage\_V4\_post/)

* **Content Type:** <mark style="color:orange;">application/x-www-form-urlencoded</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

{% code overflow="wrap" %}
```
curl --location 'https://rest.esms.vn/MainService.svc/json/SendMultipleSMSBrandname' \
--header 'Content-Type: text/plain' \
--data '<RQST>
<APIKEY>{{APIKEY}}</APIKEY>
<SECRETKEY>{{SECRETKEY}}</SECRETKEY>
<CONTENT>{{CONTENT}}</CONTENT>
<SMSTYPE>1</SMSTYPE>
<BRANDNAME>{{BRANDNAME}}</BRANDNAME>
<CONTACTS>
<CUSTOMER><PHONE>{{PHONE}}</PHONE></CUSTOMER>
<CUSTOMER><PHONE>{{PHONE}}</PHONE></CUSTOMER>
<CUSTOMER><PHONE>{{PHONE}}</PHONE></CUSTOMER>
<CUSTOMER><PHONE>{{PHONE}}</PHONE></CUSTOMER>
<CUSTOMER><PHONE>{{PHONE}}</PHONE></CUSTOMER>
</CONTACTS>
</RQST>'
```
{% endcode %}

* **Cấu trúc body của request:**

<table><thead><tr><th width="143">Tham số</th><th width="152">Kiểu dữ liệu</th><th width="130" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>Phone</td><td>string</td><td>true</td><td>Số điện thoại người nhận.</td></tr><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này. <br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>Content</td><td>string</td><td>true</td><td>Nội dung tin nhắn sẽ được gửi full content.<br>Lưu ý: Khi gửi dạng tin nhắn này khách hàng vui lòng liên hệ cho nhân viên kinh doanh để được hỗ trợ về content.</td></tr><tr><td>Smstype</td><td>string</td><td>true</td><td>Loại tin nhắn:<br>24: Zalo ưu tiên.<br>25: Zalo bình thường.</td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```
{
    "CodeResult": "100",
    "CountRegenerate": 0,
    "SMSID": "d8e0f1f0702544b2acb456ca9ccfd111250"
}
```

**Request hợp lệ.**
{% endtab %}

{% tab title="101" %}
```
{
    "CodeResult": "101",
    "CountRegenerate": 0,
    "ErrorMessage": "Authorize Failed"
}
```

**Sai thông tin ApiKey/SecretKey.**
{% endtab %}

{% tab title="789" %}
```
{
    "CodeResult": "789",
    "CountRegenerate": 0,
    "ErrorMessage": "TemplateId is not config"
}
```

**Template chưa được cấu hình cho OA ID bạn đang sử dụng.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th>Thuộc tính</th><th width="158">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Mã trả về.</td></tr><tr><td>SMSID</td><td>string</td><td>ID tin nhắn do esms trả về.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi).</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu của các ngôn ngữ ở link:**</mark>_ [**Code mẫu**](https://samplefordevelopers.esms.vn/#2d996c73-a5c2-45ca-973e-d18aabb960c7) **.**
