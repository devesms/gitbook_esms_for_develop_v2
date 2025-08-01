---
description: >-
  Hàm cho phép bạn gửi tin nhắn thoại đến 1 số điện thoại bởi mẫu cuộc gọi đã
  được tạo sẵn trên hệ thống.
---

# Hàm tạo cuộc gọi tự động theo Template

## HTTP request

\
<mark style="color:green;">**`GET`**</mark> [https://voiceapi.esms.vn/MainService.svc/json/MakeCallTemplate\_V2?ApiKey=\{{ApiKey\}}\&SecretKey=\{{SecretKey\}}\&TemplateId=\{{TemplateId\}}\&Phone=\{{Phone\}}\&VariableListStr=\{{VariableListStr\}}\&SendDate=\{{SendDate\}}\&Voice=\{{Voice\}}\&Speed=\{{Speed\}}\&CallbackUrl=\{{CallbackUrl\}}\&RequestId=\{{RequestId\}}](http://voiceapi.esms.vn/MainService.svc/json/MakeCallTemplate_V2?ApiKey=\{{ApiKey\}}\&SecretKey=\{{SecretKey\}}\&TemplateId=\{{TemplateId\}}\&Phone=\{{Phone\}}\&VariableListStr=\{{VariableListStr\}}\&SendDate=\{{SendDate\}}\&Voice=\{{Voice\}}\&Speed=\{{Speed\}}\&CallbackUrl=\{{CallbackUrl\}}\&RequestId=\{{RequestId\}})

* **Response Type:** <mark style="color:orange;">application/json</mark>

{% code overflow="wrap" %}
```
curl --location --globoff 'https://voiceapi.esms.vn/MainService.svc/json/MakeCallTemplate_V2?ApiKey={{ApiKey}}&SecretKey={{SecretKey}}&TemplateId={{TemplateId}}&Phone={{Phone}}&VariableListStr={{VariableListStr}}&SendDate={{SendDate}}&Voice={{Voice}}&Speed={{Speed}}&CallbackUrl={{CallbackUrl}}&RequestId={{RequestId}}'
```
{% endcode %}

* **Cấu trúc body của request::**

<table><thead><tr><th width="169">Tham số</th><th width="143">Kiểu dữ liệu</th><th width="134" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản</td></tr><tr><td>TemplateId</td><td>string</td><td>true</td><td>Id kịch bản cuộc gọi đăng ký trên trang account.esms.vn</td></tr><tr><td>Phone</td><td>string</td><td>true</td><td>Số điện thoại nhận tin</td></tr><tr><td>VariableListStr</td><td>string</td><td>false</td><td>Chuỗi biến chứa danh sách giá trị các biến của mẫu cuộc gọi, cách nhau bởi dấu “||”, thứ tự các biến từ trái sang phải. Ví dụ: Trung||20000 (Giá trị biến 1: Trung, Giá trị biến 2: 20000)</td></tr><tr><td>SendDate</td><td>string</td><td>false</td><td>Đặt lịch gửi tin (định dạng: yyyy/MM/dd hh:mm:ss) Ví dụ: 2017/12/12 14:00:00</td></tr><tr><td>Voice</td><td>string</td><td>false</td><td><p></p><p>Giọng đọc biến, có các giá trị sau đây:</p><ul><li>male: giọng nam miền Bắc</li><li>female: giọng nữ miền Bắc</li><li>hatieumai: giọng nữ miền Nam</li><li>ngoclam: giọng nữ Huế</li></ul></td></tr><tr><td>Speed</td><td>string</td><td>false</td><td><p></p><p>Tốc độ đọc biến, có các giá trị sau đây:</p><ul><li>-3: rất chậm</li><li>-2: khá chậm</li><li>-1: chậm</li><li>0: bình thường</li><li>1: nhanh</li><li>2: khá nhanh</li><li>3: rất nhanh</li></ul></td></tr><tr><td>RequestId</td><td>string</td><td>false</td><td>ID đối tác truyền sang để chặn trùng và đối soát khi cần.<br>Độ dài tối đa 50 ký tự.<br><strong>Mỗi RequestId truyền sang có hiệu lực chặn trong 24h.</strong></td></tr><tr><td>CallbackUrl</td><td>string (<em>URL Encode</em>)</td><td>false</td><td><p></p><p>Url nhận callback kết quả cuộc gọi (mẫu: <code>https://{{Your_API_Domain}}/Esms/ReceiveVocieCallback?ReferenceId=&#x26;CallDuration=&#x26;CallStatus=&#x26;Ivr=&#x26;Price=&#x26;SentResult=&#x26;CID=&#x26;SendStatus=</code>)</p><ul><li><strong>CallDuration</strong>: độ dài cuộc gọi</li><li><strong>CallStatus</strong>: kết quả cuộc gọi (ANSWERED, NO ANSWER)</li><li><strong>Ivr</strong>: phím bấm của khách hàng</li><li><strong>Price</strong>: giá cuộc gọi</li><li><strong>SentResult</strong>: Kết quả gửi tin qua nhà mạng (0: thất bại, 1: thành công)</li><li><strong>CID</strong>: đầu số gửi tin</li><li><strong>SendStatus</strong>: Trạng thái cuộc gọi: </li></ul><p>            2: Chờ gửi.</p><p>            5: Đã gửi xong.</p><p>            7: Đã gửi chờ báo cáo.</p><p></p><p><strong>Yêu cầu phản hồi</strong>:</p><p>Khi đối tác nhận được dữ liệu, vui lòng trả về trạng thái <strong><code>HTTP_STATUS_CODE=200</code></strong> để xác nhận với ESMS là thành công.</p><p>Nếu không nhận được HTTP_STATUS_CODE 200, ESMS sẽ tiến hành gửi lại tối đa 5 lần.<br><br><em>Ví dụ</em>:<br><code>curl --location --globoff --request GET 'https://{{Your_API_Domain}}/Esms/ReceiveVocieCallback?ReferenceId=066107ee-6ec4-4283-b595-aa74977c65c5&#x26;CallDuration=0&#x26;CallStatus=&#x26;Ivr=&#x26;Price=0.0000&#x26;SentResult=0&#x26;CID=02871002454&#x26;SendStatus=5'</code><br></p></td></tr></tbody></table>



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
<pre class="language-json"><code class="lang-json"><strong>{
</strong>    "CodeResult": "101",
    "ErrorMessage": "Authorize Failed"
}
</code></pre>

**Sai thông tin ApiKey/SecretKey.**
{% endtab %}

{% tab title="104" %}
```json
{
    "CodeResult": "104",
    "ErrorMessage": "Template not found"
}
```

TemplateId không tổng
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

| Thuộc tính | Kiểu dữ liệu | Mô tả                                                                                             |
| ---------- | ------------ | ------------------------------------------------------------------------------------------------- |
| CodeResult | string       | Mã trả về.                                                                                        |
| SMSID      | string       | ID của cuộcgoji mới được tạo ra trên hệ thống eSMS. Dùng ID này để query lấy trạng thái cuộc gọi. |

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#9b15367f-ff51-4cf4-9769-455cbdcec284)**.**
