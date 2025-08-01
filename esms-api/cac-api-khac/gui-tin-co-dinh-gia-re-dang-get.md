# Gửi tin cố định giá rẻ dạng GET

## HTTP request

\
<mark style="color:green;">**`GET`**</mark> <mark style="color:blue;">https://rest.esms.vn/MainService.svc/json/SendMultipleMessage\_V4\_get?Phone=\{{Phone\}}\&Content=\{{Content\}}\&ApiKey=\{{ApiKey\}}\&SecretKey=\{{SecretKey\}}\&IsUnicode=\{{IsUnicode\}}\&SmsType=8\&CallbackUrl=\{{CallbackUrl\}}\&RequestId=\{{RequestId\}}\&SendDate=\{{yyyy-mm-dd HH:mm:hh\}}</mark>

* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location -g 'https://rest.esms.vn/MainService.svc/json/SendMultipleMessage_V4_get?Phone={{Phone}}&Content={{Content}}&ApiKey={{ApiKey}}&SecretKey={{SecretKey}}&IsUnicode={{IsUnicode}}&SmsType=8&CallbackUrl={{CallbackUrl}}&RequestId={{RequestId}}&SendDate={{yyyy-mm-dd%20HH%3Amm%3Ahh}}'
```

* **Cấu trúc body của request:**

<table><thead><tr><th width="148">Tham số</th><th width="139">Kiểu dữ liệu</th><th width="142" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>Phone</td><td>string</td><td>true</td><td>Số điện thoại nhận tin.</td></tr><tr><td>Content</td><td>string</td><td>true</td><td>Nội dung tin nhắn.</td></tr><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr><tr><td>Unicode</td><td>string</td><td>false</td><td>Gửi nội dung có dấu<br>1: Có dấu.<br>0: Không dấu.</td></tr><tr><td>SmsType</td><td>string</td><td>true</td><td>Loại tin nhắn<br>8: Tin Cố định giá rẻ.</td></tr><tr><td>CallbackUrl</td><td>string</td><td>false</td><td>URL nhận kết quả gửi tin. <br>Xem body mẫu <a href="https://samplefordevelopers.esms.vn/#20f85e1f-3d9e-4ff4-bc4f-8d9c9edbc88a">ở đây</a>. <br>Xem chi tiết <a href="https://developers-v2.esms.vn/esms-api/callback-url">ở đây</a>.</td></tr><tr><td>RequestId</td><td>string</td><td>false</td><td>ID đối tác truyền sang để chặn trùng và đối soát khi cần.<br>Độ dài tối đa 50 ký tự.<br><strong>Mỗi RequestId truyền sang có hiệu lực chặn trong 24h.</strong></td></tr><tr><td>SendDate</td><td>string</td><td>false</td><td>Thời gian hẹn gửi của tin. <br>Không truyền khi tin muốn tin nhắn gửi đi liền.<br>Định dạng: yyyy-mm-dd hh:MM:ss</td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```
{
    "CodeResult": "100",
    "CountRegenerate": 0,
    "SMSID": "d8e0f1f0702544b2acb456ca9ccfd111250"
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

{% tab title="99" %}
```json
{
  "error": "Invalid request"
}
```

**Kiểm tra lại thông tin kết nối hoặc liên hệ bộ phận chăm sóc khách hàng để được hỗ trợ khi gặp lỗi này.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th width="162.5333251953125">Thuộc tính</th><th width="134.2667236328125">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Request được gửi đến ESMS thành công.<br><br><strong>Lưu ý:</strong> Mã phản hồi <strong>100</strong> chỉ xác nhận rằng yêu cầu đã được gửi thành công đến hệ thống ESMS, <strong>không phản ánh việc tin nhắn đã được gửi đến số điện thoại người nhận hay chưa</strong>.<br>Để theo dõi trạng thái cuối cùng của tin nhắn, quý khách vui lòng truyền thêm tham số <strong>CallbackUrl</strong>; hệ thống ESMS sẽ tự động gửi phản hồi (callback) đến địa chỉ này khi có trạng thái cuối của tin.</td></tr><tr><td>SMSID</td><td>string</td><td>ID tin nhắn do esms trả về.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi).</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* <mark style="color:yellow;">Lấy code mẫu của các ngôn ngữ ở link:</mark> [**Code mẫu**](https://samplefordevelopers.esms.vn/#562c21f1-e073-4352-8a24-eac62657953b) **.**
