---
description: Cho phép bạn gửi tin nhắn đến số điện thoại đang sử dụng Viber.
---

# Tin Viber



<figure><img src="../../.gitbook/assets/hình lên viber.png" alt=""><figcaption><p>Hình mẫu tin nhắn Viber</p></figcaption></figure>

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/Send\_Multiple\_Sms\_OTT/](http://rest.esms.vn/MainService.svc/json/Send_Multiple_Sms_OTT/)

* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

{% code overflow="wrap" %}
```json
curl --location 'https://rest.esms.vn/MainService.svc/json/Send_Multiple_Sms_OTT/' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey": "{{ApiKey}}",
    "SecretKey": "{{SecretKey}}",
    "Brandname": "{{Brandname}}",
    "Content": "🍀 🍀 Chúng tôi vừa mở bán căn hộ ĐẸP NHẤT thuộc siêu dự án- Đất nền sổ đỏ sở hữu lâu dài.\r\n🌼 🌼 THANH TOÁN 15%  SỞ HỮU ngay Căn Hộ hiện đại & đẳng cấp nhất. 🏚 🏚  ƯU ĐÃI GIỮ CHỔ SỚM 3% cùng CHIẾT KHẤU lên đến 15%.\r\n🔆 🔆   CĂN ĐẸP GIÁ TỐT cho khách hàng nhanh tay booking. NHẬN BÁO GIÁ NGAY!! 🍀 🍀🍀",
    "OttImgUrl": "https://minio.esms.vn/shared/fbff4ff5694a44c688d4f93eda4572af.png",
    "OttLabel": "Dịch vụ SMS Viber",
    "OttUrl": "https://esms.vn/dich-vu/dich-vu-sms-viber",
    "Phones": [
        "0901888484"
    ],
    "SmsType": "23",
    "RequestId": "96accf59-0c41-4bc7-a5c4-4a466c2e41c2"
}'
// Truyền \r\n để gửi nội dung xuống dòng
// Gửi tin đến nhiều số điện thoại khác nhau sẽ truyền theo cú pháp: "0901888484","0918238965"
```
{% endcode %}

<mark style="color:orange;">**`Lưu ý:`**</mark> Tin nhắn Viber có 4 kiểu nội dung để lựa chọn như sau:\
\- <mark style="color:green;">**Kiểu Văn bản - Ảnh- Nút**</mark> => Khi request truyền các tham số: Content, OttImgUrl, OttUrl, OTTLabel.\
\- <mark style="color:green;">**Kiểu Văn bản - Nút**</mark> => Khi request truyền các tham số: Content, OttUrl, OTTLabel.\
\- <mark style="color:green;">**Kiểu Ảnh**</mark> => Khi request truyền các tham số: OttImgUrl.\
\- <mark style="color:green;">**Kiểu Văn bản**</mark> => Khi request truyền các tham số: Content.

* **Cấu trúc body của request:**

<table><thead><tr><th width="136.77777099609375">Tham số</th><th width="109.7777099609375">Kiểu dữ liệu</th><th width="118.1112060546875" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản</td></tr><tr><td>Brandname</td><td>string</td><td>true</td><td>Tên Brandname (tên công ty hay tổ chức khi gửi tin sẽ hiển thị trên tin nhắn đó). Chú ý: sẽ phải đăng ký trước khi sử dụng.</td></tr><tr><td>SmsType</td><td>number</td><td>true</td><td>Loại tin nhắn<br>23: Tin nhắn OTT Viber.</td></tr><tr><td>Content</td><td>string</td><td>true</td><td>Nội dung gửi đến người nhận</td></tr><tr><td>OttImgUrl</td><td>string</td><td>false</td><td>Đường dẫn hình ảnh.</td></tr><tr><td>OTTLabel</td><td>string</td><td>false</td><td>Tên nút.</td></tr><tr><td>OttUrl</td><td>string</td><td>false</td><td>Đường dẫn tên nút.</td></tr><tr><td>Phones</td><td>array</td><td>true</td><td><p>Số điện thoại người nhận. </p><p></p><p>Truyền nhiều số điện thoại theo cú pháp</p><p>[ "0901888484","0918238965","..." ]</p></td></tr><tr><td>IsSandBox</td><td>number</td><td>false</td><td>1: Tin gửi ở môi trường test, dùng để kiểm tra kết nối và các thông số tích hợp, không về tin nhắn, không trừ tiền.<br>0: Tin gửi ở môi trường bình thường, có về tin nhắn.</td></tr><tr><td>CallbackUrl</td><td>string</td><td>false</td><td>URL nhận kết quả gửi tin. <br>Xem body mẫu <a href="https://samplefordevelopers.esms.vn/#6acfe1fc-8601-4bce-9549-65bf17f279b1">ở đây</a>. <br>Xem chi tiết <a href="https://developers-v2.esms.vn/esms-api/callback-url">ở đây</a>.</td></tr><tr><td>RequestId</td><td>string</td><td>false</td><td>ID đối tác truyền sang để chặn trùng và đối soát khi cần.<br>Độ dài tối đa 50 ký tự.<br><strong>Mỗi RequestId truyền sang có hiệu lực chặn trong 24h.</strong></td></tr><tr><td>SendDate</td><td>string</td><td>false</td><td>Thời gian hẹn gửi của tin.<br>Không truyền khi tin muốn tin nhắn gửi đi liền.<br>Định dạng: yyyy-mm-dd hh:MM:ss</td></tr></tbody></table>



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
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th width="163.666748046875">Thuộc tính</th><th width="121.3333740234375">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Request được gửi đến ESMS thành công.<br><br><strong>Lưu ý:</strong> Mã phản hồi <strong>100</strong> chỉ xác nhận rằng yêu cầu đã được gửi thành công đến hệ thống ESMS, <strong>không phản ánh việc tin nhắn đã được gửi đến số điện thoại người nhận hay chưa</strong>.<br>Để theo dõi trạng thái cuối cùng của tin nhắn, quý khách vui lòng truyền thêm tham số <strong>CallbackUrl</strong>; hệ thống ESMS sẽ tự động gửi phản hồi (callback) đến địa chỉ này khi có trạng thái cuối của tin.</td></tr><tr><td>SMSID</td><td>string</td><td>ID tin nhắn do esms trả về.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi).</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#9a4ce369-8f02-43cb-9693-f2e9ab827af3)**.**
