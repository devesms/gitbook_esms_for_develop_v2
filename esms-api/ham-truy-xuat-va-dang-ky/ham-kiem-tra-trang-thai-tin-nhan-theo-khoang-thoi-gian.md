---
description: API cho phép đối tác lấy sản lượng tin nhắn trong một khoảng thời gian.
---

# Hàm kiểm tra trạng thái tin nhắn theo khoảng thời gian

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/GetSmsSentData\_V2](http://rest.esms.vn/MainService.svc/json/GetSmsSentData_V2')

* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location 'https://rest.esms.vn/MainService.svc/json/GetSmsSentData_V2' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey": "{{ApiKey}}",
    "SecretKey": "{{SecretKey}}",
    "SmsType": "2",
    "From": "2025-01-01 06:00:00",
    "To": "2025-01-02 18:00:00",
    "Page": 1,
    "PageSize": 500
}'
```

**Cấu trúc body của request:**

<table><thead><tr><th width="172">Tham số</th><th width="133">Kiểu dữ liệu</th><th width="180" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey eSMS cung cấp.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey eSMS cung cấp.</td></tr><tr><td>From </td><td>string</td><td>true</td><td>Lấy dữ liệu từ ngày nào (theo ngày tạo tin)<br> Định dạng: yyyy-MM-dd HH:mm:ss.</td></tr><tr><td>To</td><td>string</td><td>true</td><td>Lấy dữ liệu đến ngày nào (theo ngày tạo tin).<br>Định dạng: yyyy-MM-dd HH:mm:ss.</td></tr><tr><td>Page</td><td>string</td><td>true</td><td>Lấy bắt đầu từ trang bao nhiêu.</td></tr><tr><td>PageSize</td><td>string</td><td>true</td><td>Số lượng tin nhắn cần xem (tối đa 500 tin nhắn).</td></tr><tr><td>SmsType</td><td>string</td><td>true</td><td>Loại tin nhắn<br>1: Tin quảng cáo.<br>2: Tin CSKH.<br>8: Tin Cố định giá rẻ.<br>23: Tin Viber.<br>24: Zalo ưu tiên.<br>25: Zalo bình thường.</td></tr></tbody></table>

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

**Cấu trúc body của response:**

<table><thead><tr><th width="140.79998779296875">Thuộc tính</th><th width="130.5999755859375">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td> CodeResult</td><td>string</td><td> Mã trả về.</td></tr><tr><td>CountTotal</td><td>string</td><td>Tổng số tin nhắn.</td></tr><tr><td>SentData</td><td>object</td><td>Chi tiết tin nhắn.</td></tr></tbody></table>

**Câu trúc thuộc tính SentData**

<table><thead><tr><th width="142.60003662109375">Thuộc tính</th><th width="134">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>Campaign</td><td>string</td><td><p>Tên chiến dịch.</p><p><br>Lấy dữ liệu của tham số campaignid khi request gửi tin.</p></td></tr><tr><td>Content</td><td>string</td><td>Nội dung tin nhắn.</td></tr><tr><td>Phone</td><td>string</td><td>Số điện thoại nhận tin nhắn.</td></tr><tr><td>ReferenceId</td><td>string</td><td>SmsId trả về từ các hàm gửi tin nhắn.</td></tr><tr><td>SellPrice</td><td>string</td><td>Giá của tin.</td></tr><tr><td>SendResult</td><td>string</td><td><p>Kết quả cuối của tin nhắn<br></p><p>1: Tin đã được gửi thành công. <br>0: Tin thất bại. <br>2: Tin chưa xác định trạng thái.</p></td></tr><tr><td>SendStatus</td><td>string</td><td>Trạng thái tin nhắn:<br><br>0: Đang soạn thảo.<br>1: Chờ duyệt.<br>2: Chờ gửi.<br>4: Từ chối.<br>5: Đã gửi xong (Kiểm tra thêm SendResult để biết tin gửi thành công hay thất bại).<br>7: Đã gửi chờ báo cáo</td></tr><tr><td>SentTime</td><td>string</td><td>Thời gian gửi tin.</td></tr><tr><td>SmsId</td><td>string</td><td>Id của tin nhắn trên giao diện eSMS<br><img src="../../.gitbook/assets/image (1).png" alt=""></td></tr><tr><td>SmsType</td><td>string</td><td>Loại tin nhắn<br>1: Tin quảng cáo.<br>2: Tin CSKH.<br>8: Tin Cố định giá rẻ.<br>23: Tin Viber.<br>24: Zalo ưu tiên.<br>25: Zalo bình thường.</td></tr></tbody></table>



* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#282f1bec-d093-4c68-8f99-f4d25024e9f8)**.**
