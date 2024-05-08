---
description: >-
  Hàm này chỉ dùng đối với những tin nhắn khi request gửi tin khách hàng có
  truyền trường CallbackUrl để nhận thông tin trạng thái tin nhắn qua callback.
---

# Hàm lấy thông tin callback tin nhắn Zalo

Những SMSID khi request không truyền CallbackUrl, dùng hàm này sẽ không có thông tin.

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://status-sms.esms.vn/ZaloCallback/GetCallback](https://status-sms.esms.vn/ZaloCallback/GetCallback)\


* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location 'https://status-sms.esms.vn/ZaloCallback/GetCallback' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey":"{{ApiKey}}",
    "SecretKey":"{{SecretKey}}",
    "ListRefid": [
        "{{Refid}}",
        "{{Refid}}",
        "{{Refid}}"
    ],
    "OAId": "{{OAId}}"
}'
```

* **Cấu trúc body của request:**

<table><thead><tr><th width="137">Tham số</th><th width="152">Kiểu dữ liệu</th><th width="160" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey của tài khoản.</td></tr><tr><td>ListRefid</td><td>string</td><td>true</td><td>Danh sách ReferenceId đã gửi tin.<br>Giới hạn 200 RefId, truyền nhiều hơn sẽ chỉ lấy callback của 200 RefId theo thứ tự từ trên xuống.</td></tr><tr><td>OAId</td><td>string</td><td>true</td><td>Id của OA đã gửi tin</td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```json
{
    "Code": 100,
    "Message": "Success",
    "Data_callback": [
        {
            "SMSID": "4a496110-9fd3-4838-ac8b-bcaa36616f7011",
            "SendFailed": 1,
            "SendSuccess": 0,
            "SendStatus": 5,
            "TotalPrice": 0.0,
            "TotalReceiver": 1,
            "TotalSent": 1,
            "RequestId": null,
            "TypeId": 25,
            "Telcoid": 1,
            "PhoneNumber": "0909090909",
            "CallbackUrl": "https://api.esms.vn/zalo-zns/zns/receive-callback",
            "Partnerids": "7984e9b198c40e9957d6",
            "ErrorInfo": "{\"error\":-124,\"message\":\"Access token is invalid\"}Object reference not set to an instance of an object.",
            "OAId": "1090257973118325189",
            "ZnsTempId": "228386"
        } 
                    ]
  } 
```

**Request hợp lệ.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th width="168.33333333333331">Thuộc tính</th><th width="158">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>SMSID</td><td>string</td><td>ReferenceId của tin nhắn muốn xem callback.</td></tr><tr><td>SendFailed</td><td>string</td><td>Tổng số tin thất bại.</td></tr><tr><td>SendSuccess</td><td>string</td><td>Tổng số tin thành công.</td></tr><tr><td>SendStatus</td><td>string</td><td>Trạng thái tin nhắn.</td></tr><tr><td></td><td></td><td><ul><li>Trạng thái 2: Chờ gửi .</li><li>Trạng thái 5: Đã gửi .</li></ul></td></tr><tr><td>TotalPrice</td><td>string</td><td>Tổng số tiền của tin.</td></tr><tr><td>TotalReceiver</td><td>string</td><td>Tổng số tin.</td></tr><tr><td>TotalSent</td><td>string</td><td>Tổng số tin đã gửi.</td></tr><tr><td>RequestId</td><td>string</td><td>Request mà KH truyền vào API để gửi tin.</td></tr><tr><td>TypeId</td><td>string</td><td><p>Loại tin nhắn.</p><ul><li>Type 24: Zalo Ưu Tiên.</li></ul><ul><li>Type 25: Zalo Bình Thường.</li></ul></td></tr><tr><td>Telcoid</td><td>string</td><td><p>Mạng viễn thông của thuê bao nhận tin.</p><ul><li>Mạng số 1: Viettel</li></ul><ul><li>Mạng số 2: Mobifone</li></ul><ul><li>Mạng số 3: Vinaphone</li></ul><ul><li>Mạng số 4: Vietnammobile</li></ul><ul><li>Mạng số 5: Gmobile</li></ul><ul><li>Mạng số 6: Itel</li></ul><ul><li>Mạng số 7: Reddi</li></ul></td></tr><tr><td>PhoneNumber</td><td>string</td><td>Số điện thoại nhận tin.</td></tr><tr><td>CallbackUrl</td><td>string</td><td>Link nhận callback .</td></tr><tr><td>Partnerids</td><td>string</td><td>Mã của tin nhắn vừa được gửi (do Zalo trả về).</td></tr><tr><td>ErrorInfo</td><td>string</td><td>Mã lỗi và thông tin lỗi của tin nhắn.</td></tr><tr><td>OAId</td><td>string</td><td>Id của OA mà KH gửi tin.</td></tr><tr><td>ZnsTempId</td><td>string</td><td>Id của template KH gửi tin.</td></tr></tbody></table>

{% hint style="info" %}
Chú ý:

* Số ReferenceId tối đa cho 1 lần request là 200, nhiều hơn 200 sẽ chỉ trả 200 ReferenceId đầu tiên.
* Giới hạn request 20TPS.
{% endhint %}

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [<mark style="color:blue;">**Link code mẫu**</mark>](https://samplefordevelopers.esms.vn/#eb870a67-0f33-444d-85e5-bbabf920299d)**.**
