---
description: >-
  API eSMS gửi tin nhắn Zalo hàng loạt với nội dung tùy chỉnh cho từng khách
  hàng. Hỗ trợ mẫu tin, tham số động, hẹn giờ gửi và callback. Tích hợp dễ dàng
  qua HTTP POST JSON.
---

# Tin Zalo mỗi khách hàng một nội dung

{% hint style="warning" %}
API này không hỗ trợ gửi tin từ ví zns miễn phí, các tin nhắn được miễn phí sẽ hậu kiểm và đối trừ sau.
{% endhint %}

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/Send\_zns\_bulk\_v4\_post\_json/](http://rest.esms.vn/MainService.svc/json/Send_zns_bulk_v4_post_json/)



* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```bash
curl --location 'https://rest.esms.vn/MainService.svc/json/Send_zns_bulk_v4_post_json/' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey": "{{ApiKey}}",
    "SecretKey": "{{SecretKey}}",
    "campaignid": "Chiến dịch 1",
    "OAID": "4097311281936189049",
    "TempID": "267247",
    "Sandbox": "0",
    "CallbackUrl": "https://esms.vn/webhook/",
    "Data": [
        {
            "Phone": "0901888484",
            "RequestId": "96accf59-0c41-4bc7-a5c1",
            "Params": [ "Chị A", "Gội đầu", "KH001", "19/03/2025" ]
        },
        {
            "Phone": "0918238965",
            "RequestId": "96accf59-0c41-4bc7-a5c2",
            "Params": [ "Chị B", "Uốn", "KH002", "19/03/2025" ]
        },
        {
            "Phone": "0765418062",
            "RequestId": "96accf59-0c41-4bc7-a5c3",
            "Params": [ "Chị C", "Nhuộm", "KH003", "19/03/2025" ]
        }
    ]
}'
```

* **Cấu trúc body của request:**

<table><thead><tr><th width="155">Tham số</th><th width="124">Kiểu dữ liệu</th><th width="141" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey </td><td>string</td><td>true</td><td>Chuỗi ký tự đại diện cho khóa API của tài khoản eSMS.</td></tr><tr><td>SecretKey </td><td>string</td><td>true</td><td>Chuỗi ký tự bí mật của tài khoản eSMS.</td></tr><tr><td>campaignid</td><td>string</td><td>false</td><td>Tên chiến dịch gửi tin, tối đa 254 ký tự.<br>Đây là mã chiến dịch mà bạn sẽ phân biệt được các chiến dịch gửi tin.</td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>ID của Zalo Official Account (OA) của doanh nghiệp. Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy OAID này. <br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>TempID</td><td>string</td><td>true</td><td>ID của mẫu tin nhắn Zalo OA mà doanh nghiệp đã đăng ký với eSMS.</td></tr><tr><td>Sandbox</td><td>string</td><td>false</td><td>Chế độ Sandbox để kiểm tra API mà không gửi tin nhắn thực tế.<br><strong>Mặc định:</strong> <code>Sandbox = 0</code></td></tr><tr><td>SendDate</td><td>string</td><td>false</td><td>Thời gian hẹn gửi tin nhắn.<br>Nếu không truyền tham số này, tin nhắn sẽ được gửi ngay lập tức.<br><strong>Định dạng:</strong> <code>yyyy-mm-dd hh:MM:ss</code></td></tr><tr><td>CallbackUrl</td><td>string</td><td>false</td><td>URL mà hệ thống sẽ gọi lại để trả kết quả gửi tin nhắn.<br>Xem body mẫu <a href="https://samplefordevelopers.esms.vn/#eeaca8c5-ef65-4fed-ac2e-697d0360327b">ở đây</a>. <br>Xem chi tiết <a href="../callback-url.md">ở đây</a>.</td></tr><tr><td>Data</td><td>Array</td><td>true</td><td>Mảng đối tượng chứa thông tin về từng tin nhắn bạn muốn gửi.<br><strong>Chú ý: Mảng có kích thước tối đa 500 phần tử.</strong></td></tr><tr><td>Data: Phone</td><td>string</td><td>true</td><td>Số điện thoại người nhận.</td></tr><tr><td>Data: RequestId</td><td>string</td><td>false</td><td>ID đối tác truyền sang để chặn trùng và đối soD đối tác truyền sang để chặn trùng và đối soát khi cần.<br>Độ dài tối đa 50 ký tự.<br><strong>Mỗi RequestId truyền sang có hiệu lực chặn trong ngày.</strong></td></tr><tr><td>Data: Params </td><td>string</td><td>true</td><td><p></p><p>Danh sách các giá trị cần truyền cho các biến trong mẫu tin nhắn.<br> <strong>*Lưu ý:</strong></p><ol><li>Các tham số truyền vào phải đúng thứ tự như template bạn đăng ký.</li><li>Nếu tham số trùng nhau chỉ cần truyền vào một tham số.</li></ol></td></tr><tr><td>SendingMode</td><td>string</td><td>false</td><td>Chế độ gửi:<br> <kbd><strong>1</strong></kbd> (Default): Gửi thường, tin ZNS được gửi theo cơ chế thông thường. <br><kbd><strong>3</strong></kbd>: Gửi vượt hạn mức, cho phép OA gửi tin ZNS tag 3 vượt hạn mức. <br><br><strong>Lưu ý</strong>: Chế độ Gửi vượt hạn mức (SendingMode = 3) chỉ áp dụng cho các OA được whitelist. Vui lòng liên hệ đội ngũ CSKH nếu có nhu cầu gửi ở chế độ Gửi vượt hạn mức.</td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```json

{
    "CodeResult": "100",
    "Message": "Sucess",
    "TotalFail": 1,
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
            "SMSID": "b83ff06e-8989-4b0d-818e-795b96699e86261"
        },
        {
            "CodeResult": "108",
            "Phone": "{Phone}",
            "ErrorMessage": "The phone number 097469188 is not valid."
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

<table><thead><tr><th width="177">Thuốc tính</th><th width="146">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Request được gửi đến ESMS thành công.<br><br><strong>Lưu ý:</strong> Mã phản hồi <strong>100</strong> chỉ xác nhận rằng yêu cầu đã được gửi thành công đến hệ thống ESMS, <strong>không phản ánh việc tin nhắn đã được gửi đến số điện thoại người nhận hay chưa</strong>.<br>Để theo dõi trạng thái cuối cùng của tin nhắn, quý khách vui lòng truyền thêm tham số <strong>CallbackUrl</strong>; hệ thống ESMS sẽ tự động gửi phản hồi (callback) đến địa chỉ này khi có trạng thái cuối của tin.</td></tr><tr><td>Message</td><td>string</td><td>Mô tả chi tiết về phản hồi.</td></tr><tr><td>TotalFail</td><td>string</td><td>Tổng số điện thoại request gửi tin thất bại.</td></tr><tr><td>TotalSuccess</td><td>string</td><td>Tổng số điện thoại request gửi tin thành công.</td></tr><tr><td>detail : CodeResult</td><td>string</td><td>Mã trả về.</td></tr><tr><td>detail : Phone</td><td>string</td><td>Số điện thoại tương ứng với ID tin nhắn do esms trả về.</td></tr><tr><td>detail : SMSID</td><td>string</td><td>ID tin nhắn do esms trả về.</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#1f75d02b-c622-4de4-aedc-dd9d4c2b16ea)**.**&#x20;
