---
description: >-
  Hàm giúp bạn kiểm tra trạng thái của tin nhắn đã gửi đi. Lưu ý: Chỉ lấy dữ
  liệu các tin trong vòng 7 ngày gần nhất.
---

# Hàm kiểm tra tin nhắn theo SMSID

## HTTP request

\
<mark style="color:green;">**`GET`**</mark> [https://rest.esms.vn/MainService.svc/json/GetSendStatus?RefId=\{{SMSID\}}\&ApiKey=\{{ApiKey\}}\&SecretKey=\{{SecretKey\}}](https://rest.esms.vn/MainService.svc/json/GetSendStatus?RefId=\{{SMSID\}}\&ApiKey=\{{ApiKey\}}\&SecretKey=\{{SecretKey\}})

* **Response Type:** <mark style="color:orange;">application/json</mark>



```json
curl --location --globoff 'http://rest.esms.vn/MainService.svc/json/GetSendStatus?RefId={{SMSID}}&ApiKey={{ApiKey}}&SecretKey={{SecretKey}}'
```

* **Câu trúc body của request:**

<table><thead><tr><th width="139">Tham số</th><th width="129">Kiểu dữ liệu </th><th width="155" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>RefId</td><td>string</td><td>true</td><td>SmsId hệ thống trả về từ mỗi hàm gửi tin nhắn.</td></tr><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```
{
    "CodeResponse": "100",
    "SMSID": "434a124c-7818-4f45-bdf2-7f7b07fff210100",
    "SendFailed": 0,
    "SendStatus": 5,
    "SendSuccess": 1,
    "TotalPrice": 850.0000,
    "TotalReceiver": 1,
    "TotalSent": 1
}
```

**Request hợp lệ.**
{% endtab %}

{% tab title="101" %}
```json
{
    "CodeResponse": "101",
    "SMSID": "47756317-0cbe-494a-9d02-c85703a1baff20"
}
```

**Sai thông tin ApiKey/SecretKey.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th width="174">Thuộc tính</th><th width="155">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResponse</td><td>string</td><td>Mã trả về.</td></tr><tr><td>SMSID</td><td>string</td><td>SmsId kiểm tra.</td></tr><tr><td>SendFailed</td><td>string</td><td>Số lượng tin thất bại.</td></tr><tr><td>SendStatus</td><td>string</td><td>Trạng thái tin nhắn<br>1: Chờ Duyệt<br>2: Chờ gửi.<br>5: Đã gửi xong.</td></tr><tr><td>SendSuccess</td><td>string</td><td>Số lượng tin thành công.</td></tr><tr><td>TotalPrice</td><td>string</td><td>Tổng tiền của đơn.</td></tr><tr><td>TotalReceiver</td><td>string</td><td>Số lượng người nhận.</td></tr><tr><td>TotalSent</td><td>string</td><td>Số lượng gửi.</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#17b5d3c2-11b8-4748-ad0a-442a42d43532)**.**
