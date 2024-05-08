---
description: >-
  Hàm cho phép bạn gửi tin nhắn thoại đến 1 số điện thoại bởi file ghi âm đã
  tạo.
---

# Hàm lấy trạng thái cuộc gọi

## HTTP request

\
<mark style="color:green;">**`GET`**</mark> [https://voiceapi.esms.vn/MainService.svc/json/GetSendStatus?ApiKey=\{{ApiKey\}}\&SecretKey=\{{SecretKey\}}\&ReferenceId=\{{SMSID\}}](https://voiceapi.esms.vn/MainService.svc/json/GetSendStatus?ApiKey=\{{ApiKey\}}\&SecretKey=\{{SecretKey\}}\&ReferenceId=\{{SMSID\}})

* **Response Type:** <mark style="color:orange;">application/json</mark>

{% code overflow="wrap" %}
```
curl --location -g 'https://voiceapi.esms.vn/MainService.svc/json/MakeCallRecord_V2?ApiKey={{ApiKey}}&SecretKey={{SecretKey}}&TemplateId={{RecordId}}&Phone={{Phone}}&SendDate={{SendDate}}&NumberForward={{NumberForward}}&MaxRepeat={{MaxRepeat}}&MaxRetry={{MaxRetry}}&Ivr={{Ivr}}&TimeWaitToIvr={{TimeWaitToIvr}}&WaitRetry={{WaitRetry}}&CallbackUrl={{CallbackUrl}}&RequestID={{RequestId}}'
```
{% endcode %}

* **Cấu trúc body của request:**

<table><thead><tr><th width="157">Tham số</th><th width="141">Kiểu dữ liệu</th><th width="129" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr><tr><td>ReferenceId</td><td>string</td><td>true</td><td>SMSID khi gọi trả về.</td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```json
{
    "CallDuration": 13,
    "CallStatus": "ANSWERED",
    "CodeResponse": "100",
    "Ivr": "",
    "ReferenceId": "505139D7-54F8-48A9-88FA-9460A78731DD",
    "SendStatus": 5,
    "SentResult": 1
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
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th width="193">Thuộc tính</th><th width="203">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CallDuration</td><td>string</td><td>ID của cuộcgoji mới được tạo ra trên hệ thống eSMS. Dùng ID này để query lấy trạng thái cuộc gọi.</td></tr><tr><td>CallStatus</td><td>string</td><td>Kết quả của cuộc gọi (ANSWERED: cuộc gọi được trả lời, NOANSWERED: cuộc gọi thất bại hoặc không ai bắt máy).</td></tr><tr><td>Ivr</td><td>string</td><td>Phím phản hồi của người nghe.</td></tr><tr><td>ReferenceId</td><td>string</td><td>SMSID tin nhắn check trạng thái.</td></tr><tr><td>SendStatus</td><td>string</td><td>Trạng thái tin nhắn<br>5: Đã gửi xong.</td></tr><tr><td>SentResult</td><td>string</td><td>Kết quả tin nhắn<br>0: Thất bại.<br>1: Thành công.</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#92d7042b-06f1-41c4-85f8-91a1d976944d)**.**
