# Hàm kiểm tra chất lượng OA

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/ZNS/GetQuality/](https://rest.esms.vn/MainService.svc/json/ZNS/GetQuality/)\


* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location 'https://rest.esms.vn/MainService.svc/json/ZNS/GetQuality/' \
--header 'Content-Type: application/json' \
--data '{
 "ApiKey": "{{ApiKey}}",
 "SecretKey": "{{SecretKey}}",
 "OAID": "{{OAID}}"
}'
```

* **Cấu trúc body request:**

<table><thead><tr><th width="142">Tham số</th><th width="133">Kiểu dữ liệu</th><th width="148" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey của tài khoản.</td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. <br>Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này.<br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```json
{
    "CodeResult": "100",
    "ErrorMessage": "success",
    "Oa7dayQuality": "HIGH",
    "OaCurrentQuality": "MEDIUM"
}
```

**Request hợp lệ.**
{% endtab %}

{% tab title="101" %}
```json
{
    "CodeResult": "101",
    "ErrorMessage": "Authorize Failed"
}
```

**Sai thông tin ApiKey/SecretKey.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th width="183">Thuốc tính</th><th width="159">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>Oa7dayQuality</td><td>string</td><td><p>Chất lượng gửi thông báo ZNS trong 7 ngày gần nhất của OA. Các giá trị trả về:</p><p></p><ul><li>HIGH - Mức độ chất lượng tốt.</li><li>MEDIUM - Mức độ chất lượng trung bình.</li><li>LOW - Mức độ chất lượng kém.</li><li>UNDEFINED - Mức độ chất lượng OA chưa được xác định (trường hợp OA không gửi thông báo ZNS nào trong khung thời gian đánh giá).</li></ul></td></tr><tr><td>OaCurrentQuality</td><td>string</td><td><p>Chất lượng gửi thông báo ZNS trong 48 giờ gần nhất của OA. Các giá trị trả về:</p><ul><li>HIGH - Mức độ chất lượng tốt .</li><li>MEDIUM - Mức độ chất lượng trung bình .</li><li>LOW - Mức độ chất lượng kém .</li><li>UNDEFINED - Mức độ chất lượng OA chưa được xác định (trường hợp OA không gửi thông báo ZNS nào trong khung thời gian đánh giá).</li></ul></td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu của các ngôn ngữ ở link:**</mark>_ [**Code mẫu**](https://samplefordevelopers.esms.vn/#b03f9576-0e10-4061-bdd0-4cecc82ef6c5) **.**
