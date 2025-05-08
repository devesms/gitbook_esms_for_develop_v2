---
description: 'Lưu ý: Tối đa mỗi request giới hạn 50 đánh giá.'
---

# Hàm lấy thông tin đánh giá của khách hàng

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/ZNS/GetRating/](https://rest.esms.vn/MainService.svc/json/ZNS/GetRating/)\


* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

{% code overflow="wrap" %}
```json
curl --location 'https://rest.esms.vn/MainService.svc/json/ZNS/GetRating/' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey": "APIKEYCUABAN",
    "SecretKey": "SECRETKEYCUABAN",
    "OAID": "4097311281936189049",
    "TemplateID": "266986",
    "FromTime": "2024-07-28 00:00:00",
    "ToTime": "2024-07-30 23:59:59",
    "Offset": "0",
    "Limit": "50"
}'
```
{% endcode %}

* **Cấu trúc body của request:**

<table><thead><tr><th width="156">Tham số</th><th width="122">Kiểu dữ liệu</th><th width="137" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey của tài khoản.</td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. <br>Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này.<br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>TemplateID</td><td>string</td><td>true</td><td>Template của Zalo OA mà khách hàng đăng kí với eSMS.</td></tr><tr><td>FromTime</td><td>string</td><td>true</td><td>Thời gian bắt đầu lấy đánh giá. Định dạng: yyyy-mm-dd hh:mm:ss .</td></tr><tr><td>ToTime</td><td>string</td><td>true</td><td>Thời gian kết thúc lấy đánh giá. Định dạng: yyyy-mm-dd hh:mm:ss .</td></tr><tr><td>Offset</td><td>string</td><td>true</td><td>Vị trí thứ tự đánh giá đầu tiên trả về. Bắt đầu từ vị trí 0.</td></tr><tr><td>Limit</td><td>string</td><td>true</td><td>Số lượng đánh giá cần xem.</td></tr></tbody></table>



***

* **Response:**

{% tabs %}
{% tab title="100" %}
```json
{
    "CodeResult": "100",
    "ErrorMessage": "success",
    "Data": [
        {
            "feedbacks": [
                "Nhân viên tư vấn nhiệt tình, thái độ vui vẻ, dễ thương",
                "Chính sách hỗ trợ rõ ràng, đầy đủ và dễ hiểu",
                "Chất lượng sản phẩm rất tốt",
                "Giao hàng nhanh",
                "Dịch vụ chăm sóc rất tốt"
            ],
            "msgId": "5dcf84fe1fd8bd85e4ca",
            "note": "",
            "rate": 5,
            "submitDate": "1659750276218",
            "trackingId": ""
        }
    ],
    "Total": 1
}    
```

**Request hợp lệ.**
{% endtab %}

{% tab title="101" %}
```json
{
    "CodeResult": "101",
    "ErrorMessage": "Authorize Failed"
}
```

**Sai thông tin ApiKey/SecretKey.**
{% endtab %}
{% endtabs %}

**Cấu trúc body response:**

<table><thead><tr><th width="172.59991455078125">Thuốc tính</th><th width="125.7999267578125">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Mã trả về</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi)</td></tr><tr><td>Data</td><td>array</td><td>Chi tiết đánh giá.</td></tr><tr><td>Total</td><td>string</td><td>Tổng số lượt đánh giá.</td></tr></tbody></table>

**Cấu trúc thuộc tính từng object trong Data**

<table><thead><tr><th width="170.4000244140625">Thuốc tính</th><th width="130.199951171875">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>feedbacks</td><td>string</td><td>Tổng số tin được gửi trong ngày.</td></tr><tr><td>msgId</td><td>string</td><td>SmsId của zalo.</td></tr><tr><td>note</td><td>string</td><td>Ghi chút của khách hàng cho đánh giá.</td></tr><tr><td>rate</td><td>string</td><td>Số sao khách hàng đánh giá.</td></tr><tr><td>submitDate</td><td>string</td><td>submitDate: Thời điểm khách hàng submit đánh giá. Biến submitDate sẽ có giá trị trong khoảng thời gian từ from_time đến to_time (được truyền vào từ request). <br><strong>Lưu ý: Tính theo timestamp (millisecond).</strong></td></tr><tr><td>trackingId</td><td>string</td><td>Là giá trị của tham số RequestId khách hàng truyền vào khi gửi tin Zalo.</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#c36498c6-2153-494c-9795-36c85330aa33)**.**
