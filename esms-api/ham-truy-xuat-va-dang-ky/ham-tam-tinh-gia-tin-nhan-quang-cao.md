# Hàm tạm tính giá tin nhắn quảng cáo

## HTTP request&#x20;

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/SummaryMultipleSMSBrandname/](https://rest.esms.vn/MainService.svc/json/SummaryMultipleSMSBrandname/)

* **Content Type:** <mark style="color:orange;">text/plain</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```
curl --location 'https://rest.esms.vn/MainService.svc/json/SummaryMultipleSMSBrandname/' \
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
<CUSTOMER><PHONE>{{PHONE}}</PHONE></CUSTOMER>
</CONTACTS>
</RQST>'
```

* **Cấu trúc body của request:**

<table><thead><tr><th width="187">Thuốc tính</th><th width="146">Kiểu dữ liệu</th><th width="137" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>APIKEY</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SECRETKEY</td><td>string</td><td>true</td><td>SecretKey của tài khoản.</td></tr><tr><td>CONTENT</td><td>string</td><td>true</td><td>Nội dung tin nhắn.</td></tr><tr><td>SMSTYPE</td><td>string</td><td>true</td><td>Loại tin nhắn<br><br>1: Loại tin Quảng cáo</td></tr><tr><td>BRANDNAME</td><td>string</td><td>true</td><td>Tên thương hiệu.</td></tr><tr><td>PHONE</td><td>string</td><td>true</td><td>Số điện thoại nhận tin.</td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```json
{
    "CodeResult": "100",
    "ErrorMessage": "success",
    "TotalPrice": 1691300.0000,
    "TotalReceiver": 2997
}
```

**Request hợp lệ.**
{% endtab %}

{% tab title="101" %}
```json
{
    "CodeResult": "101",
    "CountRegenerate": 0,
    "ErrorMessage": "Authorize Failed"
}
```

**Sai thông tin ApiKey/SecretKey.**
{% endtab %}

{% tab title="104" %}
```json
{
    "CodeResult": "104",
    "ErrorMessage": "Brand name code is not exist"
}
```

**Brandname truyền chưa đúng hoặc chưa được active.**
{% endtab %}
{% endtabs %}

**Cấu trúc body của response:**

<table><thead><tr><th width="181">Thuốc tính</th><th width="153">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td> CodeResult</td><td>string</td><td>Mã trả về.</td></tr><tr><td> ErrorMessage</td><td>string</td><td>Nội dung thông báo.</td></tr><tr><td>TotalPrice</td><td>string</td><td>Tổng tiền tin.</td></tr><tr><td>TotalReceiver</td><td>string</td><td>Tổng số điện thoại nhận tin.</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman**</mark>**:**_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#938df6e6-b2fb-45b0-a036-2852f508cf74)**.**
