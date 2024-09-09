# Tin nhắn Zalo sử dụng hash phone

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [http://rest.esms.vn/MainService.svc/json/SendZaloMessage\_V6/hash\_phone/](http://rest.esms.vn/MainService.svc/json/SendZaloMessage\_V6/hash\_phone/)

* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

{% code overflow="wrap" %}
```json
curl --location 'https://rest.esms.vn/MainService.svc/json/SendZaloMessage_V6/' \
--header 'Content-Type: application/json' \
--header 'Cookie: ASP.NET_SessionId=wzlj2i5udpvik2ktprsusma5' \
--data-raw '{
    "ApiKey": "APIKEYCUABAN",
    "SecretKey": "SECRETKEYCUABAN",
    "OAID": "4097311281936189049",
    "HashPhone": "ApwfITmMxKtH+LpkHRrocCjwj2EUdZJKwu1ASF7SolwJgvn+tllS+6iQ+IDmJZDgoh4fRUci978o7SnUAxxQOGu2FnGkppRz9zGOkMurKCjPRRA6p8AGYN12ZsB7QGlqLOCGrxPzaAjJ8qFrsYg8LZwjK0=",
    "TempData": {
        "customer_name": "Đinh Thái Hà",
        "order_code": "HD00001",
        "address": "140-142 Đường Số 1, KDC Vạn Phúc, Hiệp Bình Phước, Thủ Đức",
        "phone": "0901888484",
        "email": "dinhthaiha@vihatgroup.com",
        "product_name": "Gói duy trì OA Zalo Premium 1 năm",
        "quantity": "1",
        "payment_amount": "4308000",
        "delivery_date": "01/08/2024"
    },
    "TempID": "200607",
    "campaignid": "Xác nhận mua hàng",
    "RequestId": "96accf59-0c41-4bc7-a5c4-4a466c2e41c2",
    "CallbackUrl": "https://esms.vn/webhook/"
}'
```
{% endcode %}

* **Cấu trúc body của request:**

<table><thead><tr><th width="152">Tham số</th><th width="136">Kiểu dữ liệu</th><th width="137" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>HashPhone</td><td>string</td><td>true</td><td>Số điện thoại của người nhận. <br>Lưu ý: Số điện thoại cần được mã hóa RSA trước khi truyền vào.<br>Liên hệ kỹ thuật để lấy Public key</td></tr><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey eSMS cung cấp.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey eSMS cung cấp.</td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này. <br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>TempData</td><td>JSON object</td><td>true</td><td>Các thuộc tính của template mà khách hàng eSMS đã đăng ký với Zalo.<br><strong>Chú ý: Cấu trúc TempData</strong> <strong>được quy định riêng ứng với từng template.</strong></td></tr><tr><td>SendDate</td><td>string</td><td>false</td><td>Thời gian hẹn gửi của tin. <br>Không truyền khi tin muốn tin nhắn gửi đi liền.<br>Định dạng: yyyy-mm-dd hh:MM:ss.</td></tr><tr><td>TempID </td><td>string</td><td>true</td><td>Template của Zalo OA mà khách hàng đăng kí với eSMS.</td></tr><tr><td>campaignid</td><td>string</td><td>false</td><td>Tên chiến dịch gửi tin, tối đa 254 ký tự.</td></tr><tr><td>Sandbox</td><td>string</td><td>false</td><td>1: Tin gửi ở môi trường test, dùng để kiểm tra kết nối và các thông số tích hợp, không về tin nhắn, không trừ tiền.<br>0: Tin gửi ở môi trường bình thường, có về tin nhắn.</td></tr><tr><td>CallbackUrl</td><td>string</td><td>false</td><td>URL nhận kết quả gửi tin.<br>Xem body mẫu <a href="https://samplefordevelopers.esms.vn/#b98ca55e-3001-4446-b5bb-a4ab86127b0b">ở đây</a><strong>.</strong> <br>Xem chi tiết <a href="../callback-url.md">ở đây</a><strong>.</strong></td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```json
{
    "CodeResult": "100",
    "CountRegenerate": 0,
    "SMSID": "d8e0f1f0702544b2acb456ca9ccfd111250"
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

{% tab title="789" %}
```json
{
    "CodeResult": "789",
    "CountRegenerate": 0,
    "ErrorMessage": "TemplateId is not config"
}
```

**Template chưa được cấu hình cho OA ID bạn đang sử dụng.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th width="195">Thuộc tính</th><th width="156">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Mã trả về.</td></tr><tr><td>SMSID</td><td>string</td><td>ID của tin nhắn mới được tạo ra trên hệ thống eSMS. Dùng ID này để query lấy trạng thái tin nhắn.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi).</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu của các ngôn ngữ ở link**</mark>_<mark style="color:yellow;">:</mark> [**Link code mẫu .**](https://samplefordevelopers.esms.vn/#2d996c73-a5c2-45ca-973e-d18aabb960c7)
