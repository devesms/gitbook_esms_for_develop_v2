# Gửi tin chăm sóc khách hàng dạng GET

## HTTP request

\
<mark style="color:green;">**`GET`**</mark> <mark style="color:blue;">https://rest.esms.vn/MainService.svc/json/SendMultipleMessage\_V4\_get?Phone=\{{Phone\}}\&Content=\{{Content\}}\&ApiKey=\{{ApiKey\}}\&SecretKey=\{{SecretKey\}}\&IsUnicode=\{{IsUnicode\}}\&Brandname=\{{Brandname\}}\&SmsType=2\&CallbackUrl=\{{CallbackUrl\}}\&RequestId=\{{RequestId\}}\&SendDate=\{{yyyy-mm-dd HH:mm:hh\}}\&SandBox=\{{SandBox\}}</mark>

* **Response Type:** <mark style="color:orange;">application/json</mark>

```
curl --location -g 'https://rest.esms.vn/MainService.svc/json/SendMultipleMessage_V4_get?Phone={{Phone}}&Content={{Content}}&ApiKey={{ApiKey}}&SecretKey={{SecretKey}}&IsUnicode={{IsUnicode}}&Brandname={{Brandname}}&SmsType=2&CallbackUrl={{CallbackUrl}}&RequestId={{RequestId}}&SendDate={{yyyy-mm-dd%20HH%3Amm%3Ahh}}'
```

* **Cấu trúc body request:**

<table><thead><tr><th width="156">Tham số</th><th width="155">Kiểu dữ liệu </th><th width="145" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>Phone</td><td>string</td><td>true</td><td>Số điện thoại nhận tin.</td></tr><tr><td>Content</td><td>string</td><td>true</td><td>Nội dung tin nhắn.</td></tr><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr><tr><td>Unicode</td><td>string</td><td>false</td><td>Gửi nội dung có dấu<br>1: Có dấu.<br>0: Không dấu.</td></tr><tr><td>Brandname</td><td>string</td><td>true</td><td>Tên Brandname (tên công ty hay tổ chức khi gửi tin sẽ hiển thị trên tin nhắn đó). <br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>SmsType</td><td>number</td><td>true</td><td>Loại tin nhắn<br>2: Tin CSKH.</td></tr><tr><td>CallbackUrl</td><td>string</td><td>false</td><td>URL nhận kết quả gửi tin. <br>Xem body mẫu <a href="https://samplefordevelopers.esms.vn/#20f85e1f-3d9e-4ff4-bc4f-8d9c9edbc88a">ở đây</a>. <br>Xem chi tiết <a href="../callback-url.md">ở đây</a>.</td></tr><tr><td>RequestId</td><td>string</td><td>false</td><td>ID Tin nhắn của đối tác, dùng để kiểm tra ID này đã được hệ thống esms tiếp nhận trước đó hay chưa.<br>Ví dụ: requestid=123456</td></tr><tr><td>SendDate</td><td>string</td><td>false</td><td>Thời gian hẹn gửi của tin. <br>Không truyền khi tin muốn tin nhắn gửi đi liền.<br>Định dạng: yyyy-mm-dd hh:MM:ss</td></tr><tr><td>SandBox</td><td>string</td><td>false</td><td>1: Tin gửi ở môi trường test, dùng để kiểm tra kết nối và các thông số tích hợp, không về tin nhắn, không trừ tiền.<br>0: Tin gửi ở môi trường bình thường, có về tin nhắn.</td></tr></tbody></table>



***

* **Response:**

{% tabs %}
{% tab title="100" %}
```json
{
    "CodeResult": "100",
    "CountRegenerate": 0,
    "SMSID": "ebe101db-87cd-4285-b97b-6a7a90455ded30"
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

{% tab title="104" %}
```json
{
    "CodeResult": "104",
    "CountRegenerate": 0,
    "ErrorMessage": "Brand name code is not exist"
}
```

**Brandname truyền chưa đúng hoặc chưa được active.**
{% endtab %}

{% tab title="124" %}
```json
{
    "CodeResult": "124",
    "CountRegenerate": 0,
    "ErrorMessage": "Request exist 1"
}
```

**Trùng RequestId. Mỗi RequestId chỉ được gửi cho 1 request.**
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

<table><thead><tr><th width="196">Thuộc tính</th><th width="133">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Mã trả về.</td></tr><tr><td>SMSID</td><td>string</td><td>ID tin nhắn do esms trả về.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi).</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#df0d691e-6423-490b-b75e-d9df2d961615)**.**
