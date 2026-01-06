---
description: >-
  Hàm cho phép bạn gửi tin nhắn thoại đến 1 số điện thoại bởi file ghi âm đã
  tạo.
---

# Hàm tạo cuộc gọi tự động từ file ghi âm

## HTTP request

\
<mark style="color:green;">**`GET`**</mark> [https://voiceapi.esms.vn/MainService.svc/json/MakeCallRecord\_V2?ApiKey=\{{ApiKey\}}\&SecretKey=\{{SecretKey\}}\&TemplateId=\{{RecordId\}}\&Phone=\{{Phone\}}\&SendDate=\{{SendDate\}}\&NumberForward=\{{NumberForward\}}\&MaxRepeat=\{{MaxRepeat\}}\&MaxRetry=\{{MaxRetry\}}\&Ivr=\{{Ivr\}}\&TimeWaitToIvr=\{{TimeWaitToIvr\}}\&WaitRetry=\{{WaitRetry\}}\&CallbackUrl=\{{CallbackUrl\}}\&RequestID=\{{RequestId\}}](http://voiceapi.esms.vn/MainService.svc/json/MakeCallRecord_V2?ApiKey=\{{ApiKey\}}\&SecretKey=\{{SecretKey\}}\&TemplateId=\{{RecordId\}}\&Phone=\{{Phone\}}\&SendDate=\{{SendDate\}}\&NumberForward=\{{NumberForward\}}\&MaxRepeat=\{{MaxRepeat\}}\&MaxRetry=\{{MaxRetry\}}\&Ivr=\{{Ivr\}}\&TimeWaitToIvr=\{{TimeWaitToIvr\}}\&WaitRetry=\{{WaitRetry\}}\&CallbackUrl=\{{CallbackUrl\}}\&RequestID=\{{RequestId\}})[](http://voiceapi.esms.vn/MainService.svc/json/MakeCallTemplate_V2?ApiKey={ApiKey}\&SecretKey={SecretKey}\&TemplateId={TemplateId}\&Phone={Phone}\&VariableListStr={VariableListStr}\&SendDate={SendDate}\&Voice={Voice}\&Speed={Speed}\&CallbackUrl={CallbackUrl}\&RequestId={RequestId})<br>

* **Response Type:** <mark style="color:orange;">application/json</mark>

{% code overflow="wrap" %}
```
curl --location --globoff 'https://voiceapi.esms.vn/MainService.svc/json/MakeCallRecord_V2?ApiKey={{ApiKey}}&SecretKey={{SecretKey}}&TemplateId={{RecordId}}&Phone={{Phone}}&SendDate={{SendDate}}&NumberForward={{NumberForward}}&MaxRepeat={{MaxRepeat}}&MaxRetry={{MaxRetry}}&Ivr={{Ivr}}&TimeWaitToIvr={{TimeWaitToIvr}}&WaitRetry={{WaitRetry}}&CallbackUrl={{CallbackUrl}}&RequestID={{RequestId}}'
```
{% endcode %}

* **Cấu trúc body của request:**

<table><thead><tr><th width="202">Tham số</th><th width="137">Kiểu dữ liệu</th><th width="137" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản</td></tr><tr><td>TemplateId</td><td>string</td><td>true</td><td>Id file ghi âm tạo trên trang account.esms.vn</td></tr><tr><td>Phone</td><td>string</td><td>true</td><td>Số điện thoại nhận tin</td></tr><tr><td>NumberForward</td><td>string</td><td>false</td><td>Số điện thoại được chuyển đến khi nhập đúng Ivr</td></tr><tr><td>SendDate</td><td>string</td><td>false</td><td>Đặt lịch gửi tin (định dạng: yyyy/MM/dd hh:mm:ss) Ví dụ: 2017/12/12 14:00:00</td></tr><tr><td>MaxRepeat</td><td>string</td><td>false</td><td>Số lần lặp lại file ghi âm khi nghe</td></tr><tr><td>MaxRetry</td><td>string</td><td>false</td><td>Số lần gọi lại khi người nhận không bắt máy</td></tr><tr><td>Ivr</td><td>string</td><td>false</td><td>Phím quy định khi người nhận bấm để chuyển số (phím từ: 0-9)</td></tr><tr><td>TimeWaitToIvr</td><td>string</td><td>false</td><td>Thời gian chờ tối đa để người gọi nhấn phím</td></tr><tr><td>WaitRetry</td><td>string</td><td>false</td><td>Khoảng cách giữa các lần gọi lại khi người nhận không bắt máy (đơn vị: giây)</td></tr><tr><td>CallbackUrl</td><td>string (<em>URL Encode</em>)</td><td>false</td><td><p></p><p>Url nhận callback kết quả cuộc gọi (mẫu: <code>https://{{Your_API_Domain}}/Esms/ReceiveVocieCallback?ReferenceId=&#x26;CallDuration=&#x26;CallStatus=&#x26;Ivr=&#x26;Price=&#x26;SentResult=&#x26;CID=&#x26;SendStatus=</code>)</p><ul><li><strong>CallDuration</strong>: độ dài cuộc gọi</li><li><strong>CallStatus</strong>: kết quả cuộc gọi (ANSWERED, NO ANSWER)</li><li><strong>Ivr</strong>: phím bấm của khách hàng</li><li><strong>Price</strong>: giá cuộc gọi</li><li><strong>SentResult</strong>: Kết quả gửi tin qua nhà mạng (0: thất bại, 1: thành công)</li><li><strong>CID</strong>: đầu số gửi tin</li><li><strong>SendStatus</strong>: Trạng thái cuộc gọi: </li></ul><p>            2: Chờ gửi.</p><p>            5: Đã gửi xong.</p><p>            7: Đã gửi chờ báo cáo.</p><p></p><p><strong>Yêu cầu phản hồi</strong>:</p><p>Khi đối tác nhận được dữ liệu, vui lòng trả về trạng thái <strong><code>HTTP_STATUS_CODE=200</code></strong> để xác nhận với ESMS là thành công.</p><p>Nếu không nhận được HTTP_STATUS_CODE 200, ESMS sẽ tiến hành gửi lại tối đa 5 lần.<br><br><em>Ví dụ</em>:<br><code>curl --location --globoff --request GET 'https://{{Your_API_Domain}}/Esms/ReceiveVocieCallback?ReferenceId=066107ee-6ec4-4283-b595-aa74977c65c5&#x26;CallDuration=0&#x26;CallStatus=&#x26;Ivr=&#x26;Price=0.0000&#x26;SentResult=0&#x26;CID=02871002454&#x26;SendStatus=5'</code><br></p></td></tr><tr><td>RequestId</td><td>string</td><td>false</td><td>ID đối tác truyền sang để chặn trùng và đối soát khi cần.<br>Độ dài tối đa 50 ký tự.<br><strong>Mỗi RequestId truyền sang có hiệu lực chặn trong 24h.</strong></td></tr></tbody></table>



***

* **Response:**

{% tabs %}
{% tab title="100" %}
```json
{
 "CodeResult": "100",
 "SMSID": "8eb2af6d-fb4c4814-b9cc-4c0e3ed32edf "
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

<table><thead><tr><th width="213">Thuộc tính</th><th width="168">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>String</td><td>Mã trả về.</td></tr><tr><td>SMSID</td><td>String</td><td>ID tin nhắn do esms trả về.</td></tr><tr><td>ErrorMessage</td><td>String</td><td>Thông tin lỗi trả về (nếu có lỗi).</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#bd90912f-439a-4c8e-a741-914b7fc36cde)**.**
