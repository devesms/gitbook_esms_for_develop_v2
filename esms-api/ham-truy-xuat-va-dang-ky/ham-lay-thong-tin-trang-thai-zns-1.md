---
description: >-
  API kiểm tra trạng thái tin nhắn Zalo, bao gồm thông tin kết quả và mã lỗi
  được trả về.
hidden: true
---

# Hàm kiểm tra trạng thái tin nhắn Zalo

{% hint style="warning" %}
**Lưu ý:** Giới hạn tốc độ gọi api này là 100 requests/giây.
{% endhint %}

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/QueryZnsStatus/](https://rest.esms.vn/MainService.svc/json/QueryZnsStatus/)<br>

* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>



```json
curl --location 'https://rest.esms.vn/MainService.svc/json/QueryZnsStatus/' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey": "{{ApiKey}}",
    "SecretKey": "{{SecretKey}}",
    "SmsId": "2d00b834cc1d488081ba7ec308da0ec40918238965",
    "SmsType": "25"
}'
```

* **Cấu trúc body của request:**

<table><thead><tr><th width="167">Tham số</th><th width="126">Kiểu dữ liệu </th><th width="134" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey của tài khoản.</td></tr><tr><td>SmsId</td><td>string</td><td>true</td><td>SmsId hệ thống trả về từ mỗi hàm gửi tin nhắn.</td></tr><tr><td>SmsType</td><td>string</td><td>true</td><td>Loại tin nhắn. Api này chỉ cho phép lấy trạng thái của hai loại sau:<br>24: Zalo ưu tiên<br>25: Zalo bình thường</td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```json
{
    "CodeResult": "100",
    "Data": {
        "ErrorInfo": "0",
        "FinalStatus": "1",
        "SMSID": "59e0c764219c49119063db4468f257fb221",
        "SendFailed": 0,
        "SendStatus": 5,
        "SendSuccess": 1,
        "TotalPrice": 330.0,
        "TotalReceiver": 1,
        "TotalSent": 1,
        "ZaloMsgId": "6dc7499c9ef6baaee3e1"
    }
}
```

**Request hợp lệ.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th width="204">Thuộc tính</th><th width="166">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Kết quả của Request.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông báo kết quả trả về.</td></tr><tr><td>Data</td><td>string</td><td>Thông tin trạng thái của tin nhắn Zalo .</td></tr></tbody></table>

* **Cấu trúc thuộc tính từng object trong Data:**

<table><thead><tr><th width="174">Thuộc tính</th><th width="171">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>ErrorInfo</td><td>string</td><td>Thời gian thiết bị của người dùng nhận được thông báo ZNS.</td></tr><tr><td>FinalStatus</td><td>string</td><td>Mô tả trạng thái thông báo. Các giá trị trả về:<br>-1: Tin nhắn không tồn tại<br>0: Tin nhắn đã được gửi lên máy chủ Zalo nhưng chưa được chuyển đến điện thoại của người dùng<br>1: Tin nhắn đã được chuyển đến điện thoại của người dùng</td></tr><tr><td>SMSID</td><td>int</td><td>Trạng thái của thông báo ZNS.</td></tr><tr><td>SendFailed</td><td></td><td></td></tr><tr><td>SendStatus</td><td></td><td></td></tr><tr><td>SendSuccess</td><td></td><td></td></tr><tr><td>TotalPrice</td><td></td><td></td></tr><tr><td>TotalReceiver</td><td></td><td></td></tr><tr><td>TotalSent</td><td></td><td></td></tr><tr><td>ZaloMsgId</td><td></td><td></td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#cab8ca81-d83a-46e5-ab19-b58f29a6f656)**.**
