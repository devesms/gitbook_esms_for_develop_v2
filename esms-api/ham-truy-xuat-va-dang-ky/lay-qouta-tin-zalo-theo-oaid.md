# Lấy quota tin zalo theo OAID

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/ZNS/GetQuota/](https://rest.esms.vn/MainService.svc/json/ZNS/GetQuota/)<br>

* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location 'https://rest.esms.vn/MainService.svc/json/ZNS/GetQuota/' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey": "{{ApiKey}}",
    "SecretKey": "{{SecretKey}}",
    "OAID": "4097311281936189049"
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
    "DailyQuota": 5000,
    "DailyQuotaPromotion": 0,
    "EstimatedNextMonthPromotionQuota": 425,
    "MonthlyPromotionQuota": 403,
    "RemainingMonthlyPromotionQuota": 403,
    "RemainingQuota": 4992,
    "RemainingQuotaPromotion": 0
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

**Cấu trúc body của response:**

<table><thead><tr><th width="262.4000244140625">Thuộc tính</th><th width="137.800048828125">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Mã trả về.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi).</td></tr><tr><td>DailyQuota</td><td>int</td><td>Số thông báo ZNS OA được gửi trong 1 ngày.<br>Lưu ý: Hạn mức gửi ZNS mỗi ngày của OA sẽ tự động được điều chỉnh dựa theo chất lượng và nhu cầu gửi.</td></tr><tr><td>DailyQuotaPromotion</td><td>int</td><td>Số tin ZNS hậu mãi OA được gửi trong ngày.</td></tr><tr><td>EstimatedNextMonthPromotionQuota</td><td>int</td><td>Số tin ZNS hậu mãi dự kiến mà OA có thể gửi trong tháng tiếp theo.</td></tr><tr><td>MonthlyPromotionQuota</td><td>int</td><td>Số tin ZNS hậu mãi OA được gửi trong tháng.</td></tr><tr><td>RemainingMonthlyPromotionQuota</td><td>int</td><td>Số tin ZNS hậu mãi còn lại OA được gửi trong tháng.</td></tr><tr><td>RemainingQuota</td><td>int</td><td>Số thông báo ZNS OA được gửi trong ngày còn lại.</td></tr><tr><td>RemainingQuotaPromotion</td><td>int</td><td>Số tin ZNS hậu mãi còn lại OA được gửi trong ngày.</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#f7a3f3f8-3bb2-4b53-af42-66afe6966a69)**.**
