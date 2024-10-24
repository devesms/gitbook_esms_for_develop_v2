# Hàm lấy danh sách UID có tương tác theo khoảng thời gian

## HTTP request&#x20;

<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/QueryListUID/](https://rest.esms.vn/MainService.svc/json/SubServicePreviewJson/)

* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location 'https://rest.esms.vn/MainService.svc/json/QueryListUID/' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey": "{{ApiKey}}",
    "SecretKey": "{{SecretKey}}",
    "OAID": "4097311281936189049",
    "Offset": 0, 
    "Count": 50, 
    "FromDate": "01/09/2024",
    "ToDate": "13/10/2024",
    "IsFollower": "",
    "TagName": "" 
}'
```

* **Cấu trúc body của request:**

<table><thead><tr><th width="143">Tham số</th><th width="129">Kiểu dữ liệu</th><th width="143" data-type="checkbox">Tính băt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey của tài khoản.</td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. <br>Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này.<br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>Offset</td><td>string</td><td>true</td><td><p>Thứ tự của UID trong danh sách trả về.</p><p><strong>Hỗ trợ tối đa 9.950 (tương ứng 10.000 UID, 50 UID/request)</strong>.</p></td></tr><tr><td>Count</td><td>string</td><td>true</td><td>Số lượng UID cần lấy. <br><strong>Tối đa mỗi lần request là 50 UID.</strong></td></tr><tr><td>FromDate</td><td>string</td><td>true</td><td>Thời gian bắt đầu lấy UID có tương tác.</td></tr><tr><td>ToDate</td><td>string</td><td>true</td><td>Thời gian kết thúc lấy UID có tương tác.</td></tr><tr><td>IsFollower</td><td>string</td><td>false</td><td><p></p><p>Trạng thái quan tâm OA của UID</p><ul><li>1: UID đang quan tâm OA.</li><li>0: UID chưa quan tâm OA.</li><li>Rỗng: lấy tất cả.</li></ul></td></tr><tr><td>TagName</td><td>string</td><td>false</td><td><p>Tên của nhãn được gắn cho UID. <br>Khi bạn sử dụng tham số này, API sẽ trả về danh sách UID theo nhãn tương ứng.</p><p>Lưu ý: Trường hợp không truyền vào TagName, API sẽ trả về toàn bộ UID người dùng.</p></td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```json
{
    "CodeResult": "100",
    "Data": {
        "Count": 50,
        "Offset": 0,
        "Total": 4,
        "Users": [
            "7406454492343693107",
            "7210831021380318952",
            "961919545811768483",
            "6559140676281540092"
        ]
    }
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

{% tab title="161" %}
```
{
    "CodeResult": "161",
    "ErrorMessage": "FromDate is invalid date format."
}
{
    "CodeResult": "161",
    "ErrorMessage": "ToDate is invalid date format."
}
```

**Sai định dạng ngày.**
{% endtab %}

{% tab title="162" %}
```
{
    "CodeResult": "162",
    "ErrorMessage": "Offset is invalid."
}
{
    "CodeResult": "162",
    "ErrorMessage": "Count is invalid."
}
```

**Thứ tự lấy UID hoặc số lượng UID cần lấy không hợp lệ.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th width="168">Thuốc tính</th><th width="183">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Kết quả của request.</td></tr><tr><td>Data</td><td>string</td><td><ul><li>Count: Số lượng UID cần lấy.</li><li>Offset: Thứ tự UID cần lấy.</li><li>Tatal: Tổng UID lấy được.</li><li>Users: Danh sách UID.</li></ul></td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu.**](https://samplefordevelopers.esms.vn/#2f26fb8e-2b78-4bbc-89a7-d739a7c32ff7)
