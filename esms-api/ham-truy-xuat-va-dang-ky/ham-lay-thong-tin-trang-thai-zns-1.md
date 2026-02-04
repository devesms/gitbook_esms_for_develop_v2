---
description: >-
  API kiểm tra trạng thái tin nhắn Zalo, bao gồm thông tin kết quả gửi và mã lỗi
  của tin nhắn.
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

<table><thead><tr><th width="140.8887939453125">Thuộc tính</th><th width="125.111083984375">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Kết quả của Request.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông báo kết quả trả về.</td></tr><tr><td>Data</td><td>string</td><td>Thông tin trạng thái của tin nhắn Zalo .</td></tr></tbody></table>

* **Cấu trúc thuộc tính từng object trong Data:**

<table><thead><tr><th width="174">Thuộc tính</th><th width="128.333251953125">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>ErrorInfo</td><td>string</td><td><p>Mã kết quả xử lý gửi tin nhắn.</p><p>Giá trị trả về:</p><ul><li>0: Tin nhắn gửi thành công.</li><li>1001: Tin nhắn trả trạng thái thất bại do khách hàng không online để nhận tin  trong thời gian quy định.</li><li>null: Tin nhắn chưa được gửi.</li><li>Các giá trị khác: Thể hiện mã lỗi từ hệ thống Zalo, vui lòng tham khảo bảng mã lỗi Zalo để biết ý nghĩa chi tiết.</li></ul></td></tr><tr><td>FinalStatus</td><td>string</td><td><p>Mô tả trạng thái tin nhắn đã có kết quả cuối cùng hay chưa. </p><p>Các giá trị trả về:<br>1: Đã có trạng thái cuối<br>0: Chưa có trạng thái cuối</p></td></tr><tr><td>SMSID</td><td>string</td><td>Trạng thái của thông báo ZNS.</td></tr><tr><td>SendFailed</td><td>int</td><td>Số lượng tin thất bại.</td></tr><tr><td>SendStatus</td><td>int</td><td>Trạng thái tin nhắn<br>1: Chờ Duyệt<br>2: Chờ gửi.<br>5: Đã gửi xong.</td></tr><tr><td>SendSuccess</td><td>int</td><td>Số lượng tin thành công.</td></tr><tr><td>TotalPrice</td><td>string</td><td>Tổng tiền của đơn.</td></tr><tr><td>TotalReceiver</td><td>int</td><td>Số lượng người nhận.</td></tr><tr><td>TotalSent</td><td>int</td><td>Số lượng gửi.</td></tr><tr><td>ZaloMsgId</td><td>string</td><td>Mã giao dịch của Zalo.</td></tr></tbody></table>



* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#dfb2453d-0f9e-43ec-b7ac-260af32cbac3)**.**
