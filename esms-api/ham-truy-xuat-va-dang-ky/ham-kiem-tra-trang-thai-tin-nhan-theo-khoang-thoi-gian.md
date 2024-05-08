---
description: API cho phép đối tác lấy sản lượng tin nhắn trong một khoảng thời gian.
---

# Hàm kiểm tra trạng thái tin nhắn theo khoảng thời gian

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/GetSmsSentData\_V2](http://rest.esms.vn/MainService.svc/json/GetSmsSentData\_V2')

* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location 'https://rest.esms.vn/MainService.svc/json/GetSmsSentData_V2' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey":"{{ApiKey}}",
    "SecretKey":"{{SecretKey}}",
    "SmsType":"{{SmsType}}",
    "From": "{{DateFrom}}",
    "To":"{{DateTo}}",
    "Page":{{Page}},
    "PageSize":{{PageSize}}
}'
```

* **Cấu trúc body của request:**

<table><thead><tr><th width="172">Tham số</th><th width="133">Kiểu dữ liệu</th><th width="180" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr><tr><td>From </td><td>string</td><td>true</td><td>Ngày bắt đầu lấy tin.<br> Định dạng: yyyy-MM-dd HH:mm:ss.</td></tr><tr><td>To</td><td>string</td><td>true</td><td>Ngày kết thúc lấy tin.<br>Định dạng: yyyy-MM-dd HH:mm:ss.</td></tr><tr><td>Page</td><td>string</td><td>true</td><td>Lấy bắt đầu từ trang bao nhiêu.</td></tr><tr><td>PageSize</td><td>string</td><td>true</td><td>Số lượng tin nhắn cần xem (tối đa 500 tin nhắn).</td></tr><tr><td>SmsType</td><td>string</td><td>true</td><td>Loại tin nhắn<br>1: Tin quảng cáo.<br>2: Tin CSKH.<br>8: Tin Cố định giá rẻ.<br>23: Tin Viber.<br>24: Zalo ưu tiên.<br>25: Zalo bình thường.<br>26: Zalo Follower.</td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```
{
    "CodeResult": "100",
    "CountTotal": 2
    "SentData": [
        {
            "Campaign": "Chiến dịch 02/10/2023",
            "Content": "Cam on quy khach da su dung dich vu cua chung toi. Chuc quy khach mot ngay tot lanh!",
            "Phone": "0901888484",
            "ReferenceId": "35781d6c25524e40a035c26663189549",
            "SellPrice": 345.0,
            "SendResult": 0,
            "SendStatus:5,
            "SentTime": "/Date(1705484048995+0700)/",
            "SmsId": 29028845,
            "SmsType": 2
        },
        {
            "Campaign": "Chiến dịch 02/10/2023",
            "Content": "Cam on quy khach da su dung dich vu cua chung toi. Chuc quy khach mot ngay tot lanh!",
            "Phone": "0901888484",
            "ReferenceId": "0aac72e0-ba9b-4348-8530-d18d105778db18",
            "SellPrice": 790.0000,
            "SendResult": 1,
            "SendStatus:5,
            "SentTime": "/Date(1705484048995+0700)/",
            "SmsId": 29028845,
            "SmsType": 2
        }
    ]
```

**Request hợp lệ.**
{% endtab %}

{% tab title="101" %}
```json
{
    "CodeResult": "101",
    "ErrorMessage": "Authorize Failed."
}
```

**Sai thông tin ApiKey/SecretKey.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

| Thuộc tính   | Kiểu dữ liệu | Mô tả                                                                                                                                                                     |
| ------------ | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  CodeResult  | string       |  Mã trả về.                                                                                                                                                               |
| CountTotal   | string       | Tổng số tin nhắn.                                                                                                                                                         |
| Campaign     | string       | Tên chiến dịch.                                                                                                                                                           |
| Content      | string       | Nội dung tin nhắn.                                                                                                                                                        |
| Phone        | string       | Số điện thoại nhận tin nhắn.                                                                                                                                              |
| RefercenceId | string       | SmsId trả về từ các hàm gửi tin nhắn.                                                                                                                                     |
| Sellprice    | string       | Giá của tin.                                                                                                                                                              |
| SendResult   | string       | <p>Trạng thái tin nhắn:</p><p>1: Tin đã được gửi thành công.<br>0: Tin thất bại.<br>2: Tin chưa xác định trạng thái.</p>                                                  |
| SendStatus   | string       | <p>0: Đang soạn thảo.<br>1: Chờ duyệt.<br>2: Chờ gửi.<br>4: Từ chối.<br>5: Đã gửi xong.<br>7: Đã gửi chờ báo cáo</p>                                                      |
| SentTime     | string       | Thời gian gửi tin.                                                                                                                                                        |
| SmsId        | string       | Id của tin nhắn trên giao diện.                                                                                                                                           |
| SmsType      | string       | <p>Loại tin nhắn<br>1: Tin quảng cáo.<br>2: Tin CSKH.<br>8: Tin Cố định giá rẻ.<br>23: Tin Viber.<br>24: Zalo ưu tiên.<br>25: Zalo bình thường.<br>26: Zalo Follower.</p> |

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#282f1bec-d093-4c68-8f99-f4d25024e9f8)**.**
