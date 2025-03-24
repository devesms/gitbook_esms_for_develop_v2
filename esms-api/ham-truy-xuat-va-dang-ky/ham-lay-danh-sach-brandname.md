# Hàm lấy danh sách Brandname

## HTTP request

\
<mark style="color:green;">**`GET`**</mark> [https://rest.esms.vn/MainService.svc/json/GetListBrandname/\{{ApiKey\}}/\{{SecretKey\}}](https://rest.esms.vn/MainService.svc/json/GetListBrandname/%7B%7BApiKey%7D%7D/%7B%7BSecretKey%7D%7D)

* **Response Type:** <mark style="color:orange;">application/json</mark>

{% code overflow="wrap" %}
```json
curl --location --globoff 'https://rest.esms.vn/MainService.svc/json/GetListBrandname/{{ApiKey}}/{{SecretKey}}'
```
{% endcode %}

* **Câu trúc body của request:**

<table><thead><tr><th width="158.20001220703125">Tham số</th><th width="152">Kiểu dữ liệu</th><th width="134" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```json
{
    "CodeResponse": "100",
    "ListBrandName": [
        {
            "Brandname": "Baotrixemay",
            "Type": 2
        },
        {
            "Brandname": "QC_ONLINE",
            "Type": 1
        },
        {
            "Brandname": "BAT DONG SAN GIA TOT",
            "Type": 23
        }
    ]
}
```

Request hợp lệ.
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

**Cấu trúc body của response:**

<table><thead><tr><th width="181.4000244140625">Thuộc tính</th><th width="189.7999267578125">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td> CodeResponse</td><td>string</td><td>Mã trả về.</td></tr><tr><td>ListBrandName</td><td>array</td><td>Danh sách brandname hiện đang kích hoạt ở tài khoản.</td></tr></tbody></table>

**Cấu trúc thuộc tính từng object ListBrandName**

<table><thead><tr><th width="185">Thuộc tính</th><th width="190.60009765625">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>Brandname</td><td>string</td><td>Tên brandname.</td></tr><tr><td>Type</td><td>string</td><td>Loại brandname<br><br>1: brandname quảng cáo.<br>2: brandname CSKH.<br>23: brandname Viber.</td></tr></tbody></table>



* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#3133a801-03e9-4e81-8de1-ac27549fb966)**.**
