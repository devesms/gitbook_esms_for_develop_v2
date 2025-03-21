---
description: >-
  Hàm lấy danh sách SĐT của một tin nhắn đã gửi (dựa trên SmsID hệ thống trả về)
  kèm theo trạng thái gửi (SĐT đó đã gửi thành công chưa?). Lưu ý: Chỉ lấy dữ
  liệu các tin trong vòng 7 ngày gần nhất.
---

# Hàm kiểm tra chi tiết từng số trong tin nhắn

## HTTP request

\
<mark style="color:green;">**`GET`**</mark> [https://rest.esms.vn/MainService.svc/json/GetSmsReceiverStatus\_get?ApiKey=\{{ApiKey\}}\&SecretKey=\{{SecretKey\}}\&RefId=\{{SMSID\}}](http://rest.esms.vn/MainService.svc/json/GetSmsReceiverStatus_get?ApiKey=\{{ApiKey\}}\&SecretKey=\{{SecretKey\}}\&RefId=\{{SMSID\}})

* **Response Type:** <mark style="color:orange;">application/json</mark>

{% code overflow="wrap" %}
```
curl --location --globoff 'https://rest.esms.vn/MainService.svc/json/GetSmsReceiverStatus_get?ApiKey={{ApiKey}}&SecretKey={{SecretKey}}&RefId={{SMSID}}'
```
{% endcode %}

* **Cấu trúc body của request:**

<table><thead><tr><th width="139">Tham số</th><th width="131">Kiểu dữ liệu</th><th width="149" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey eSMS cung cấp.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey eSMS cung cấp.</td></tr><tr><td>RefId</td><td>string</td><td>true</td><td>SmsId hệ thống trả về từ mỗi hàm gửi tin nhắn.</td></tr></tbody></table>

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

**Cấu trúc body của response:**

<table><thead><tr><th width="145.99993896484375">Thuộc tính</th><th width="151.39990234375">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Mã trả về.</td></tr><tr><td>ReceiverList</td><td>object</td><td>Chi tiết từng số trong tin nhắn.</td></tr></tbody></table>

**Cấu trúc thuộc tính ReceiverList**

<table><thead><tr><th width="145">Thuộc tính</th><th width="154.5999755859375">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>IsSent</td><td>string</td><td>Trạng thái đi tin:<br>true: tin đã được gửi.<br>false: tin chưa được gửi.</td></tr><tr><td>NetworkName</td><td>string</td><td>Nhà mạng của số điện thoại.</td></tr><tr><td>Phone</td><td>string</td><td>Số điện thoại.</td></tr><tr><td>Retry</td><td>string</td><td>Số lần gửi lại tin nhắn.</td></tr><tr><td>SentResult</td><td>string</td><td>Kết quả tin nhắn:<br>True: Gửi thành công.<br>False: Gửi thất bại.</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#1c1433bf-69be-4882-87d4-dd0c686f565c)**.**
