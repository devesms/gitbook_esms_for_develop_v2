---
description: Đây là hàm dùng để truy xuất trạng thái của thông báo ZNS.
---

# Hàm lấy thông tin trạng thái ZNS

{% hint style="warning" %}
**Lưu ý:** Giới hạn tốc độ gọi api này là 30 requests/giây.
{% endhint %}

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [http://rest.esms.vn/MainService.svc/json/GetZaloMessageStatus](http://rest.esms.vn/MainService.svc/json/GetZaloMessageStatus)<br>

* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>



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

<table><thead><tr><th width="167">Tham số</th><th width="126">Kiểu dữ liệu </th><th width="134" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey của tài khoản.</td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp.<br>Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này.<br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>MessageId</td><td>string</td><td>true</td><td>ID của thông báo cần lấy thông tin trạng thái ZNS (chính là Partnerids được trả về trong <a href="ham-lay-thong-tin-callback-tin-nhan-zalo.md">hàm lấy thông tin  callback tin nhắn zalo</a>)</td></tr></tbody></table>



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

<table><thead><tr><th width="204">Thuộc tính</th><th width="166">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Kết quả của Request.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông báo kết quả trả về.</td></tr><tr><td>Data</td><td>string</td><td>Thông tin trạng thái của thông báo ZNS .</td></tr></tbody></table>

* **Cấu trúc thuộc tính từng object trong Data:**

<table><thead><tr><th width="174">Thuộc tính</th><th width="171">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>delivery_time</td><td>string</td><td>Thời gian thiết bị của người dùng nhận được thông báo ZNS.</td></tr><tr><td>message</td><td>string</td><td>Mô tả trạng thái thông báo. Các giá trị trả về:<br>-1: Tin nhắn không tồn tại<br>0: Tin nhắn đã được gửi lên máy chủ Zalo nhưng chưa được chuyển đến điện thoại của người dùng<br>1: Tin nhắn đã được chuyển đến điện thoại của người dùng</td></tr><tr><td>status</td><td>int</td><td>Trạng thái của thông báo ZNS.</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#cab8ca81-d83a-46e5-ab19-b58f29a6f656)**.**
