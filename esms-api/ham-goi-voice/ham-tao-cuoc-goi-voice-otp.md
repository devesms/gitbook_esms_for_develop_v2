# Hàm tạo cuộc gọi voice OTP

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/SendMultipleMessage\_V4\_post\_json/](http://rest.esms.vn/MainService.svc/json/SendMultipleMessage\_V4\_post\_json/)\


* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```
curl --location 'https://rest.esms.vn/MainService.svc/json/SendMultipleMessage_V4_post_json/' \
--header 'Content-Type: application/json' \
--data '{
   "ApiKey": "{{ApiKey}}",
   "Content": "{{Content}}",
   "Phone": "{{Phone}}",
   "SecretKey": "{{SecretKey}}",
   "SmsType": "8",
   "IsUnicode": {{IsUnicode}},
   "Sandbox": {{Sandbox}},
   "campaignid": "{{campaignid}}",
   "RequestId": "{{RequestId}}",
   "CallbackUrl": "{{CallbackUrl}}",
   "SendDate":{{SendDate}}
}'
```

* **Cấu trúc body của request:**

<table><thead><tr><th width="145">Tham số</th><th width="121">Kiểu dữ liệu</th><th width="147" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey eSMS cung cấp.</td></tr><tr><td>Content</td><td>string</td><td>true</td><td>Nội dung tin nhắn.</td></tr><tr><td>Phone</td><td>string</td><td>true</td><td>Số điện thoại nhận tin nhắn.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey eSMS cung cấp.</td></tr><tr><td>SmsType</td><td>number</td><td>true</td><td>Loại tin nhắn<br>8: Tin Cố định giá rẻ</td></tr><tr><td>Unicode</td><td>number</td><td>false</td><td><p>Gửi nội dung có dấu<br>1: Có dấu.</p><p>0: Không dấu.</p></td></tr><tr><td>Sandbox</td><td>number</td><td>false</td><td>1: Tin gửi ở môi trường test, dùng để kiểm tra kết nối và các thông số tích hợp, không về tin nhắn <br>0: Tin gửi ở môi trường bình thường, có về tin nhắn.</td></tr><tr><td>campaignid</td><td>string</td><td>false</td><td>Tên chiến dịch.</td></tr><tr><td>RequestId</td><td>string</td><td>false</td><td>ID đối tác truyền sang để chặn trùng và đối soát khi cần.</td></tr><tr><td>CallbackUrl</td><td>string</td><td>false</td><td>URL nhận kết quả gửi tin.</td></tr><tr><td>SendDate</td><td>string</td><td>false</td><td>Thời gian hẹn gửi của tin. <br>Không truyền khi tin muốn tin nhắn gửi đi liền.<br>Định dạng: yyyy-mm-dd hh:MM:ss</td></tr></tbody></table>



***

* **Response:**

{% tabs %}
{% tab title="100" %}
```
{
    "CodeResult": "101",
    "CountRegenerate": 0,
    "ErrorMessage": "Authorize Failed"
}
```

**Request hợp lệ.**
{% endtab %}

{% tab title="101" %}
```
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

<table><thead><tr><th width="176">Thuộc tính</th><th width="178">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Mã trả về.</td></tr><tr><td>SMSID</td><td>string</td><td>ID của tin nhắn mới được tạo ra trên hệ thống eSMS. Dùng ID này để query lấy trạng thái tin nhắn.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi).</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu của các ngôn ngữ ở link**</mark>**:**_ [**Code mẫu**](https://samplefordevelopers.esms.vn/#562c21f1-e073-4352-8a24-eac62657953b) **.**

