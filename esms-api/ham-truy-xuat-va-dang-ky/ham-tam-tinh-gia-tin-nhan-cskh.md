# Hàm tạm tính giá tin nhắn CSKH

## HTTP request

\
<mark style="color:green;">**`GET`**</mark> [https://rest.esms.vn/MainService.svc/json/SummaryMultipleMessage\_V4\_get?Phone=\{{Phone\}}\&Content=\{{Content\}}\&ApiKey=\{{ApiKey\}}\&SecretKey=\{{SecretKey\}}\&SmsType=2\&BrandName=\{{BrandName\}}](https://rest.esms.vn/MainService.svc/json/SummaryMultipleMessage_V4_get?Phone=\{{Phone\}}\&Content=\{{Content\}}\&ApiKey=\{{ApiKey\}}\&SecretKey=\{{SecretKey\}}\&SmsType=2\&BrandName=\{{BrandName\}})

* **Response Type:** <mark style="color:orange;">application/json</mark>

{% code overflow="wrap" %}
```
curl --location 'https://rest.esms.vn/MainService.svc/json/SummaryMultipleMessage_V4_get?Phone=0901888484&Content=456756756%20la%20ma%20xac%20minh%20dang%20ky%20Baotrixemay%20cua%20ban&ApiKey={{ApiKey}}&SecretKey={{SecretKey}}&SmsType=2&BrandName=Baotrixemay'
```
{% endcode %}

* **Cấu trúc body của request:**

<table><thead><tr><th width="184">Tham số</th><th width="137">Kiểu dữ liệu</th><th width="154" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey của tài khoản.</td></tr><tr><td>Brandname</td><td>string</td><td>true</td><td>Tên thương hiệu.</td></tr><tr><td>SmsType</td><td>string</td><td>true</td><td>Loại tin nhắn, SmsType = 2: Loại tin chăm sóc khách hàng.</td></tr><tr><td>Phone</td><td>string</td><td>true</td><td>Số điện thoại nhận tin.</td></tr><tr><td>Content</td><td>string</td><td>true</td><td>Nội dung tin nhắn.</td></tr><tr><td>IsUnicode</td><td>string</td><td>false</td><td>Nội dung có chứ Unicode:<br>0: Nội dung không dấu.<br>1: Nội dung có dấu.</td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```json
{
    "CodeResult": "100",
    "ErrorMessage": "success",
    "TotalPrice": 850,
    "TotalReceiver": 1
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

{% tab title="104" %}
```
{
    "CodeResult": "104",
    "ErrorMessage": "Brand name code is not exist"
}
```

**Brandname truyền chưa đúng hoặc chưa được active.**
{% endtab %}
{% endtabs %}

**Cấu trúc body của response:**

| Thuộc tính    | Kiểu dữ liệu | Mô tả                        |
| ------------- | ------------ | ---------------------------- |
|  CodeResult   | string       | Mã trả về.                   |
|  ErrorMessage | string       | Nội dung thông báo.          |
| TotalPrice    | string       | Tổng tiền tin.               |
| TotalReceiver | string       | Tổng số điện thoại nhận tin. |

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#b80773ed-fabf-49ee-bb78-c5eefe447d74)**.**
