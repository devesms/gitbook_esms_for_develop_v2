---
hidden: true
---

# Hàm lấy danh sách Zalo Followers

## HTTP request&#x20;

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/ZNS/GetFollowers/](https://rest.esms.vn/MainService.svc/json/ZNS/GetFollowers/)\


* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location 'https://rest.esms.vn/MainService.svc/json/ZNS/GetFollowers/' \
--header 'Content-Type: application/json' \
--data '{
 "ApiKey":"{{ApiKey}}",
 "SecretKey":"{{SecretKey}}",
 "OAID":"{{OAID}}",
 "Offset": {{Offset}},
 "Count": {{Count}}
}'
```

* **Cấu trúc body của request:**

<table><thead><tr><th width="143">Tham số</th><th width="129">Kiểu dữ liệu</th><th width="152" data-type="checkbox">Tính băt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey của tài khoản.</td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. <br>Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này.<br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>Offset</td><td>string</td><td>true</td><td>Lấy bắt đầu từ đánh giá thứ bao nhiêu.</td></tr><tr><td>Limit</td><td>string</td><td>true</td><td>Số lượng đánh giá cần xem.</td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```json
{
    "CodeResult": "100",
    "ErrorMessage": "success",
    "Followers": [
        {
            "User_Id": "7800378501923859642"
        },
        {
            "User_Id": "4176617840488517388"
        },
        {a
            "User_Id": "7000997455428487634"
        },
        {
            "User_Id": "5889364632581220929"
        }
    ],
    "Total": 208
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

<table><thead><tr><th width="168">Thuốc tính</th><th width="183">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>Followers</td><td>string</td><td>Danh sách UserId Zalo follow OA.</td></tr><tr><td>Total</td><td>string</td><td>Tổng UserId follow OA.</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#eff6317f-9595-43ed-9950-102dc8b5c95e)**.**
