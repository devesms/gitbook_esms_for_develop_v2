---
description: >-
  Hàm lấy danh sách SĐT của một tin nhắn đã gửi (dựa trên SmsID hệ thống trả về)
  kèm theo trạng thái gửi (SĐT đó đã gửi thành công chưa?). Lưu ý: Chỉ lấy dữ
  liệu các tin trong vòng 7 ngày gần nhất.
---

# Hàm kiểm tra chi tiết từng số trong tin nhắn

## HTTP request

\
<mark style="color:green;">**`GET`**</mark> [http://rest.esms.vn/MainService.svc/json/GetSmsReceiverStatus\_get?ApiKey=\{{ApiKey\}}\&SecretKey=\{{SecretKey\}}\&RefId=\{{SMSID\}}](http://rest.esms.vn/MainService.svc/json/GetSmsReceiverStatus\_get?ApiKey=\{{ApiKey\}}\&SecretKey=\{{SecretKey\}}\&RefId=\{{SMSID\}})

* **Response Type:** <mark style="color:orange;">application/json</mark>

```
curl --location --globoff 'https://rest.esms.vn/MainService.svc/json/GetSmsReceiverStatus_get?ApiKey={{ApiKey}}&SecretKey={{SecretKey}}&RefId={{SMSID}}'
```

* **Cấu trúc body của request:**

<table><thead><tr><th width="139">Tham số</th><th width="131">Kiểu dữ liệu</th><th width="149" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr><tr><td>RefId</td><td>string</td><td>true</td><td>SmsId hệ thống trả về từ mỗi hàm gửi tin nhắn.</td></tr></tbody></table>



***

* **Response:**

{% tabs %}
{% tab title="100" %}
```json
{
    "CodeResult": "100",
    "ReceiverList": [
        {
            "IsSent": true,
            "NetworkName": "Viettel",
            "Phone": "0901888484",
            "Retry": 0,
            "SentResult": true
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
    "ErrorMessage": "Authorize Failed"
}
```

**Sai thông tin ApiKey/SecretKey.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

| Thuộc tính  | Kiểu dữ liệu | Mô tả                                                                            |
| ----------- | ------------ | -------------------------------------------------------------------------------- |
| IsSent      | string       | <p>Trạng thái đi tin:<br>true: tin đã được gửi.<br>false: tin chưa được gửi.</p> |
| NetworkName | string       | Nhà mạng của số điện thoại.                                                      |
| Phone       | string       | Số điện thoại.                                                                   |
| Retry       | string       | Số lần gửi lại tin nhắn.                                                         |
| SentResult  | string       | <p>Kết quả tin nhắn:<br>True: Gửi thành công.<br>False: Gửi thất bại.</p>        |

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#1c1433bf-69be-4882-87d4-dd0c686f565c)**.**
