# Hàm lấy danh sách Zalo OA

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/ZNS/GetListZOA/](https://rest.esms.vn/MainService.svc/json/ZNS/GetListZOA/)

* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location 'https://rest.esms.vn/MainService.svc/json/ZNS/GetListZOA/' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey": "{{ApiKey}}",
    "SecretKey": "{{SecretKey}}"
}'
```

* **Cấu trúc body trong request:**

<table><thead><tr><th width="162">Tham số</th><th width="136">Kiểu dữ liệu</th><th width="143" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey của tài khoản.</td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```json
{
    "CodeResult": "100",
    "ErrorMessage": "success",
    "ZOAList": [
        {
            "OAID": "745830328927467685",
            "OAName": "Hệ thống ESMS Marketing"
        },
        {
            "OAID": "4097311281936189049",
            "OAName": "SVoucher"
        }
    ]
}   
```

**Request hợp lệ.**
{% endtab %}

{% tab title="101" %}
```json
{
    "CodeResult": "101",
    "ErrorMessage": "Authorize Failed."
}
```

**Sai thông tin ApiKey/SecretKey.**
{% endtab %}
{% endtabs %}

**Cấu trúc body của response:**

<table><thead><tr><th width="165.800048828125">Thuốc tính</th><th width="168.60009765625">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Mã trả về.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi).</td></tr><tr><td>ZOAList</td><td>object</td><td>Danh sách OA đang hoạt động của tài khoản.</td></tr></tbody></table>

**Cấu trúc thuộc tính ZOAList**

<table><thead><tr><th width="168">Thuốc tính</th><th width="165">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>OAID</td><td>string</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. <br>Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này.<br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>OAName</td><td>string</td><td>Tên của OA.</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#cb86e533-d5cc-40cd-844f-465c8cb8dc38)**.**
