# Hàm lấy danh sách Brandname

## HTTP request

\
<mark style="color:green;">**`GET`**</mark> [https://rest.esms.vn/MainService.svc/json/GetListBrandname/\{{ApiKey\}}/\{{SecretKey\}}](https://rest.esms.vn/MainService.svc/json/GetListBrandname/%7B%7BApiKey%7D%7D/%7B%7BSecretKey%7D%7D)

* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location --globoff 'https://rest.esms.vn/MainService.svc/json/GetListBrandname/{{ApiKey}}/{{SecretKey}}'
```

* **Câu trúc body của request:**

<table><thead><tr><th>Tham số</th><th width="152">Kiểu dữ liệu</th><th width="134" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr></tbody></table>

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

* **Cấu trúc body của response:**

| Thuộc tính    | Kiểu dữ liệu | Mô tả                                                                                           |
| ------------- | ------------ | ----------------------------------------------------------------------------------------------- |
|  CodeResponse | string       | Mã trả về.                                                                                      |
| Brandname     | string       | Tên brandname.                                                                                  |
| Type          | string       | <p>Loại brandname:<br>1: brandname quảng cáo.<br>2: brandname CSKH.<br>23: brandname Viber.</p> |

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#3133a801-03e9-4e81-8de1-ac27549fb966)**.**
