---
description: >-
  Khác với tin gencode tự động SMS, tin gencode ở hàm này sẽ là multichanel. Nếu
  tin ZNS thất bại sẽ về tin nhắn SMS brandname với cùng một mã OTP.
---

# Tin gencode tự động multichanel: Zalo -> SMS

### HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/SendMessageAutoGenCode\_V5](http://rest.esms.vn/MainService.svc/json/SendMessageAutoGenCode\_V5)

* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

{% code overflow="wrap" %}
```json
curl --location 'https://rest.esms.vn/MainService.svc/json/SendMessageAutoGenCode_V5' \
--header 'Content-Type: application/json' \
--data '{
 "ApiKey": "{{ApiKey}}",
 "Phone": "{{Phone}}",
 "TimeAlive": "{{TimeAlive}}",
 "SecretKey": "{{SecretKey}}",
 "MultiChannelTempId": "{{MultiChannelTempId}}",
 "TypeId":"{{TypeId}}"
}'
```
{% endcode %}

* **Cấu trúc body của request:**

<table><thead><tr><th width="207">Tham số</th><th width="124">Kiểu dữ liệu </th><th width="143" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>Phone</td><td>string</td><td>true</td><td>Số điện thoại nhận tin.</td></tr><tr><td>TimeAlive</td><td>string</td><td>true</td><td>Thời gian hiệu lực của mã code. <br>Đơn vị tính: Phút. <br>Giới hạn từ 2 phút đến 15 phút.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr><tr><td>MultiChannelTempId</td><td>string</td><td>true</td><td>Id do ViHAT cung cấp. Khi muốn sử dụng hàm này tài khoản của bạn phản có OA ZNS và brandname. Bạn cung cấp tempid của ZNS và template của tin SMS cho nhân viên kinh doanh để tạo MultiChannelTempId.</td></tr><tr><td>TypeId</td><td>string</td><td>true</td><td>1: Chỉ tạo ra mã Code.<br>2: Tạo ra và gửi tin nhắn về máy.</td></tr></tbody></table>

***

* Response:&#x20;

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
    "CodeResult": "100",
    "CountRegenerate": 0,
    "SMSID": "ebe101db-87cd-4285-b97b-6a7a90455ded30"
}
```

**Sai thông tin ApiKey/SecretKey.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

| Thuốc tính   | Kiểu dữ liệu  | Mô tả                             |
| ------------ | ------------- | --------------------------------- |
| CodeResult   | string        | Mã trả về.                        |
| SMSID        | string        | ID tin nhắn do esms trả về.       |
| ErrorMessage | string        | Thông tin lỗi trả về (nếu có lỗi) |

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#3ccbb0ef-9dec-4574-96db-397674952f88)**.**
* <mark style="color:orange;">**Sử dụng API Checkcode để kiểm tra code có hợp lệ hay không. Xem API check code ở link sau đây:**</mark> [**API Checkcode**](../cac-api-khac/ham-check-code.md)**.**&#x20;
