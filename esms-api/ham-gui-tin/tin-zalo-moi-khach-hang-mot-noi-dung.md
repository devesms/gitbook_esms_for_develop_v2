# Tin Zalo mỗi khách hàng một nội dung

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/Send\_zns\_bulk\_v4\_post\_json/](http://rest.esms.vn/MainService.svc/json/Send\_zns\_bulk\_v4\_post\_json/)



* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location 'https://rest.esms.vn/MainService.svc/json/Send_zns_bulk_v4_post_json/' \
--header 'Content-Type: application/json' \
--data '{
"ApiKey": "{{ApiKey}}",
"SecretKey": "{{SecretKey}}",
"TempID": "{{TempID}}",
"Data": [
{"Phone":"{{Phone}}","Params":["{{value1}}","{{value2}}","{{value3}}"]},
{"Phone":"{{Phone}}","Params":["{{value1}}","{{value2}}","{{value3}}"]},
{"Phone":"{{Phone}}","Params":["{{value1}}","{{value2}}","{{value3}}"]}
],
"SendDate":"{{SendDate}}",
"OAID":"{{OAID}}",
"CallbackUrl":"{{CallbackUrl}}"
}'
```

* **Cấu trúc body của request:**

<table><thead><tr><th width="155">Tham số</th><th width="124">Kiểu dữ liệu</th><th width="141" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey </td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey </td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr><tr><td>TempID </td><td>string</td><td>true</td><td>Template của Zalo OA mà khách hàng đăng kí với eSMS.</td></tr><tr><td>Data: Phone</td><td>string</td><td>true</td><td>Số điện thoại người nhận.</td></tr><tr><td>Date: Params </td><td>string</td><td>true</td><td><p></p><p>Giá trị cần truyền cho các biến trong Template.<br> <strong>*Lưu ý:</strong></p><ol><li>Các tham số truyền vào phải đúng thứ tự như template bạn đăng ký.</li><li>Nếu tham số trùng nhau chỉ cần truyền vào một tham số.</li></ol></td></tr><tr><td>SendDate</td><td>string</td><td>false</td><td>Thời gian hẹn gửi của tin. <br>Không truyền khi tin muốn tin nhắn gửi đi liền.<br>Định dạng: yyyy-mm-dd hh:MM:ss</td></tr><tr><td>OAID </td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này. <br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>CallbackUrl</td><td>string</td><td>false</td><td>URL nhận kết quả gửi tin. <br>Xem body mẫu <a href="https://samplefordevelopers.esms.vn/#eeaca8c5-ef65-4fed-ac2e-697d0360327b">ở đây</a>. <br>Xem chi tiết <a href="../callback-url.md">ở đây</a>.</td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```json

{
    "CodeResult": "100",
    "Message": "Sucess",
    "TotalSuccess": 2,
    "detail": [
        {
            "CodeResult": "100",
            "Phone": "{Phone}",
            "SMSID": "a037b928-cb7e-4bfc-bdf9-0286318163aa264"
        },
        {
            "CodeResult": "100",
            "Phone": "{Phone}",
            "SMSID": "b83ff06e-8989-4b0d-818e-795b96699e86264"
        }
    ]
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

<table><thead><tr><th width="209">Thuốc tính</th><th width="146">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Mã trả về.</td></tr><tr><td>Message</td><td>string</td><td>Trạng thái request.</td></tr><tr><td>TotalSuccess</td><td>string</td><td>Tổng số điện thoại request gửi tin thành công.</td></tr><tr><td>detail : CodeResult</td><td>string</td><td>Mã trả về.</td></tr><tr><td>detail : Phone</td><td>string</td><td>Số điện thoại tương ứng với ID tin nhắn do esms trả về.</td></tr><tr><td>detail : SMSID</td><td>string</td><td>ID tin nhắn do esms trả về.</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#1f75d02b-c622-4de4-aedc-dd9d4c2b16ea)**.**&#x20;
