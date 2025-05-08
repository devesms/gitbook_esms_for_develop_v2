# Hàm tạm tính giá tin Zalo

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/SummaryZaloMessage\_V4\_post\_json/](https://rest.esms.vn/MainService.svc/json/SummaryZaloMessage_V4_post_json/)\


* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

{% code overflow="wrap" %}
```json
curl --location 'https://rest.esms.vn/MainService.svc/json/SummaryZaloMessage_V4_post_json/' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey": "{{ApiKey}}",
    "SecretKey": "{{SecretKey}}",
    "Phone": "0901888484",
    "Params": [
        "Anh",
        "2506007899",
        "02/05/2024",
        "360.000"
    ],
    "TempID": "200975",
    "OAID": "4097311281936189049"
}'
```
{% endcode %}

* **Cấu trúc body request:**

<table><thead><tr><th width="146">Tham số</th><th width="132">Kiểu dữ liệu </th><th width="143" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey của tài khoản.</td></tr><tr><td>Phone</td><td>string</td><td>true</td><td>Số điện thoại nhận tin.</td></tr><tr><td>Params</td><td>string</td><td>true</td><td><p></p><p>Nội dung gửi đến người nhận <br><strong>*Lưu ý:</strong></p><ol><li><strong>Các tham số truyền vào phải đúng thứ tự như template bạn đăng ký.</strong></li><li><strong>Nếu tham số trùng nhau chỉ cần truyền vào một tham số.</strong></li></ol></td></tr><tr><td>TempID</td><td>string</td><td>true</td><td>Template của Zalo OA mà khách hàng đăng kí với eSMS.</td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. <br>Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này.<br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```
{
    "CodeResult": "100",
    "ErrorMessage": "success",
    "TotalPrice": 660.0000,
    "TotalReceiver": 1
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

**Câu trúc body response:**

<table><thead><tr><th width="194">Thuốc tính</th><th width="189">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Mã trả về.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi).</td></tr><tr><td>TotalPrice</td><td>string</td><td>Tổng tiền tạm tính.</td></tr><tr><td>TotalReceiver</td><td>string</td><td>Tổng số điện thoại nhận tin.</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#a1b040da-0c02-4e53-b1da-c14e254a197d)**.**
