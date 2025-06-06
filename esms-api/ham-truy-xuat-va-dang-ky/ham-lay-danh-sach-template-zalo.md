# Hàm lấy danh sách template Zalo

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/MainService.svc/json/GetTemplate/](https://rest.esms.vn/MainService.svc/json/GetTemplate/)

* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

{% code overflow="wrap" %}
```json
curl --location 'https://rest.esms.vn/MainService.svc/json/GetTemplate/' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey": "{{ApiKey}}",
    "SecretKey": "{{SecretKey}}",
    "OAId": "4097311281936189049",
    "SmsType": "24"
}'
```
{% endcode %}

* **Cấu trúc body của request:**

<table><thead><tr><th width="159">Tham số</th><th width="126">Kiểu dữ liệu </th><th width="155" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr><tr><td>OAId</td><td>string</td><td>true</td><td>ID của OA cần lấy template.</td></tr><tr><td>SmsType</td><td>string</td><td>true</td><td>Loại tin<br>24: Zalo ưu tiên.<br>25: Zalo bình thường.</td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```
{
    "CodeResult": "100",
    "ErrorMessage": "success",
    "ZNSTemplates": [
        {
            "TempContent": "<div class=\"group-desc\" style=\"box-sizing: border-box; -webkit-tap-highlight-color: rgba(0, 0, 0, 0); color: #131820; font-family: Muli, sans-serif; font-size: 16px;\"> <p style=\"box-sizing: border-box; -webkit-tap-highlight-color: rgba(0, 0, 0, 0); margin: 0px; padding: 0px; color: #394e60; font-size: 0.875rem; line-height: 20px;\">Mã OTP của bạn là</p> </div> <p><span class=\"otp-code\" style=\"box-sizing: border-box; -webkit-tap-highlight-color: rgba(0, 0, 0, 0); font-weight: bold; color: #131820; font-size: 1.5rem; letter-spacing: 3.75px; line-height: 24px; display: block; padding: 12px 0px; font-family: Muli, sans-serif;\">{{otp}}</span></p> <div class=\"group-desc\" style=\"box-sizing: border-box; -webkit-tap-highlight-color: rgba(0, 0, 0, 0); color: #131820; font-family: Muli, sans-serif; font-size: 16px;\"> <p style=\"box-sizing: border-box; -webkit-tap-highlight-color: rgba(0, 0, 0, 0); margin: 0px; padding: 0px; color: #394e60; font-size: 0.875rem; line-height: 20px;\">Không tiết lộ cho bất kỳ ai, Mã xác nhận sẽ có hiệu lực trong 5 phút.</p> </div>",
            "TempId": 205644,
            "TempName": "Xác nhận đăng ký dịch vụ",
            "ZNSTempDetail": [
                {
                    "Limit": 10,
                    "Param": "otp",
                    "ParamLevel": 1,
                    "RequireType": "type_text"
                }
            ]
        }
    ]
}
```

**Request hợp lệ.**
{% endtab %}

{% tab title="101" %}
```
{
    "CodeResult": "101",
    "ErrorMessage": "Authorize Failed"
}
```

**Sai thông tin ApiKey/SecretKey.**
{% endtab %}
{% endtabs %}

**Cấu trúc body response:**

<table><thead><tr><th width="174.5999755859375">Thuộc tính</th><th width="136.4000244140625">Kiểu dữ liệu </th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Mã trả về.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi).</td></tr><tr><td>ZNSTemplates</td><td>object</td><td>Thông tin chi tiết template.</td></tr></tbody></table>

**Cấu trúc thuộc tính từng object trong ZNSTemplates**

<table><thead><tr><th width="174">Thuộc tính</th><th width="141.800048828125">Kiểu dữ liệu </th><th>Mô tả</th></tr></thead><tbody><tr><td>TempContent</td><td>string</td><td>Nội dung của template.</td></tr><tr><td>Tempid</td><td>string</td><td>Template ID.</td></tr><tr><td>TempName</td><td>string</td><td>Tên template.</td></tr><tr><td>ZNSTempDetail</td><td>object</td><td>Thông tin chi tiết kiểu biến.</td></tr></tbody></table>

**Cấu trúc thuộc tính từng object trong ZNSTempDetail**

<table><thead><tr><th width="172.199951171875">Thuộc tính</th><th width="144.60009765625">Kiểu dữ liệu </th><th>Mô tả</th></tr></thead><tbody><tr><td>Limit</td><td>string</td><td>Giới hạn độ dài nội dung truyền vào.<br>Khi gửi quá giới hạn này sẽ bị sai template.</td></tr><tr><td>Param</td><td>string</td><td>Tên biến.</td></tr><tr><td>ParamLevel</td><td>string</td><td>Thứ tự của biến</td></tr><tr><td>RequireType</td><td>string</td><td>Kiểu dữ liệu của biến.<br><br>- type_text<br>- type_number <strong>(chỉ truyền số từ 0 đến 9, tối đa là 12 số)</strong><br>- type_date <strong>(truyền theo định dạng dd/MM/yyyy)</strong><br>- type_cta_url</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#d201e3b3-5f46-4db7-b829-2b730a29b6b4)**.**
