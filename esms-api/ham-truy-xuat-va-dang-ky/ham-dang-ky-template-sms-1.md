---
description: Đây là hàm dùng để truy xuất thông tin trạng thái ZNS.
---

# Hàm lấy thông tin trạng thái ZNS

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [http://rest.esms.vn/MainService.svc/json/GetZaloMessageStatus](http://rest.esms.vn/MainService.svc/json/GetZaloMessageStatus)<br>

* **Content Type:** <mark style="color:orange;">application/json</mark>



```json
curl --location 'http://rest.esms.vn/MainService.svc/json/GetZaloMessageStatus' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey": "{{ApiKey}}",
    "SecretKey": "{{SecretKey}}",
    "OAID": "{{OAID}}",
    "MessageId": "{{MessageId}}"
}'
```

* **Cấu trúc body của request:**

<table><thead><tr><th width="167">Tham số</th><th width="126">Kiểu dữ liệu </th><th width="134" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey của tài khoản.</td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp.<br>Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này.<br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>MessageId</td><td>string</td><td>true</td><td>Mã ID tin nhắn của đối tác (Zalo)</td></tr></tbody></table>



***

* **Response:**

{% tabs %}
{% tab title="100" %}
```json
{
    "CodeResult": "100",
    "Data": {
        "delivery_time": "1767678030984",
        "message": "The message was delivered to the user's phone",
        "status": 1
    },
    "ErrorMessage": "success. "
}
```

**Request hợp lệ.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th width="204" align="center">Thuộc tính</th><th width="166" align="center">Kiểu dữ liệu</th><th align="center">Mô tả</th></tr></thead><tbody><tr><td align="center">CodeResult</td><td align="center">string</td><td align="center">Kết quả của Request.</td></tr><tr><td align="center">ErrorMessage</td><td align="center">string</td><td align="center">Thông báo kết quả trả về.</td></tr><tr><td align="center">Data</td><td align="center">string</td><td align="center">Thông tin trạng thái ZNS .</td></tr></tbody></table>

**Cấu trúc thuộc tính từng object trong Data**

<table><thead><tr><th width="174">Thuộc tính</th><th width="171">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>delivery_time</td><td>string</td><td>Thời gian thiết bị của người dùng nhận được thông báo ZNS.</td></tr><tr><td>message</td><td>string</td><td><p>Mô tả trạng thái thông báo. Các giá trị trả về:<br>-1: The message does not exist<br>0: The message is pushed successfully to Zalo server but has not yet delivered to user’s phone<br>1: The message was delivered to the user's phone</p><p></p></td></tr><tr><td>status</td><td>int</td><td>Trạng thái ZNS.</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#12f5e80f-025c-4c9c-9c9c-b42622ea8af2)**.**
