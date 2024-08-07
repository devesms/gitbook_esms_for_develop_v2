---
description: >-
  API dùng để gửi tin Quảng cáo đến khách hàng. Mỗi request tối thiểu 30 số để
  được duyệt tin và tối đa 5000 số.
---

# Tin SMS quảng cáo

## **HTTP request**&#x20;

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/SendMultipleSMSBrandname\_json/](http://rest.esms.vn/MainService.svc/json/SendMultipleSMSBrandname\_json/)

* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location 'https://rest.esms.vn/MainService.svc/json/SendMultipleSMSBrandname_json/' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey": "{{SecretKey}}",
    "SecretKey": "{{SecretKey}}",
    "Brandname": "{{Brandname}}",
    "Content": "{{Content}}",
    "Phones": [
        "{{Phones}}",
        "{{Phones}}",
        "{{Phones}}"
    ],
    "SmsType": "1",
    "SendDate": "{{SendDate}}",
    "Sandbox":"{{Sandbox}}"
}'
```

* **Cấu trúc body của request:**

<table><thead><tr><th width="170">Tham số</th><th width="141">Kiểu dữ liệu</th><th width="136" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey </td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey </td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr><tr><td>Content </td><td>string</td><td>true</td><td>Nội dung tin nhắn.</td></tr><tr><td>SmsType </td><td>string</td><td>true</td><td>Loại tin nhắn<br>1: Tin quảng cáo.</td></tr><tr><td>Brandname </td><td>string</td><td>true</td><td>Tên Brandname (tên công ty hay tổ chức khi gửi tin sẽ hiển thị trên tin nhắn đó). <br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>Phones </td><td>string</td><td>true</td><td>Số điện thoại nhận tin nhắn.</td></tr><tr><td>SendDate</td><td>string</td><td>false</td><td>Thời gian hẹn gửi của tin. <br>Không truyền khi tin muốn tin nhắn gửi đi liền.<br>Định dạng: yyyy-mm-dd hh:MM:ss</td></tr><tr><td>Sandbox</td><td>string</td><td>false</td><td>1: Tin gửi ở môi trường test, dùng để kiểm tra kết nối và các thông số tích hợp, không về tin nhắn, không trừ tiền.<br>0: Tin gửi ở môi trường bình thường, có về tin nhắn.</td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```json
{
    "CodeResult": "100",
    "CountRegenerate": 0,
    "SMSID": "d533459ee42b2b9525ba9eabf6a8156"
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

{% tab title="107" %}
```json
{
    "CodeResult": "107",
    "CountRegenerate": 0,
    "ErrorMessage": "Each request has at least 30 numbers to be approved"
}
```

**Tạo tin không thành công. Mỗi request phải có ít nhất 30 số điện thoại hợp lệ.**
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
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th width="179">Thuộc tính</th><th width="207">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Mã trả về.</td></tr><tr><td>SMSID</td><td>string</td><td>ID tin nhắn do esms trả về.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi).</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [_**Link code mẫu.**_](https://samplefordevelopers.esms.vn/#001e2636-af74-42d3-b25a-173b1dd1faed)
* _<mark style="color:orange;">**Sử dụng hàm này để lấy thông tin chi tiết tin nhắn Quảng cáo:**</mark>_ [_**Link hàm**_](https://developers.esms.vn/esms-api/ham-truy-xuat-va-dang-ky/ham-kiem-tra-trang-thai-tin-nhan-theo-khoang-thoi-gian) .
