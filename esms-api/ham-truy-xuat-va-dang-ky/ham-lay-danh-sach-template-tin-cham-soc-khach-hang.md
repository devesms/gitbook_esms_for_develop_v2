---
description: >-
  Đối với các Brandname SMS, các doanh nghiệp sẽ cần đăng ký Template là các tin
  nhắn mẫu với nhà mạng trước khi được gửi. Hàm này cho phép lấy về danh sách
  các Template của 1 Brandname thuộc tài khoản
---

# Hàm lấy danh sách template tin chăm sóc khách hàng

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark>[ ](http://rest.esms.vn/MainService.svc/json/GetTemplate/)[https://rest.esms.vn/MainService.svc/json/GetTemplate/](https://rest.esms.vn/MainService.svc/json/GetTemplate/)

* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location 'https://rest.esms.vn/MainService.svc/json/GetTemplate/' \
--header 'Content-Type: application/json' \
--data '{
 "ApiKey":"{{ApiKey}}",
 "SecretKey":"{{SecretKey}}",
 "SmsType":"2",
 "Brandname":"{{Brandname}}"
}'
```

* **Cấu trúc body của request:**

<table><thead><tr><th>Tham số</th><th width="136">Kiểu dữ liệu</th><th width="167" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr><tr><td>SmsType</td><td>string</td><td>true</td><td>Loại tin nhắn<br>2: Loại tin Chăm sóc khách hàng.</td></tr><tr><td>BrandName</td><td>string</td><td>true</td><td>Tên brandname.</td></tr></tbody></table>



***

* **Response:**

{% tabs %}
{% tab title="100" %}
```json
{
    "BrandnameTemplates": [
        {
            "NetworkID": 6,
            "TempContent": "{P1,20} la ma xac minh dang ky Baotrixemay cua ban",
            "TempId": 458
        },
        {
            "NetworkID": 4,
            "TempContent": "Baotrixemay da nhan duoc so tien thanh toan {P2,20} VND luc {P2,20} cho don hang {P1,20}. Cam on quy khach!",
            "TempId": 466
        },
        {
            "NetworkID": 2,
            "TempContent": "Cam on quy khach da su dung dich vu cua chung toi. Chuc quy khach mot ngay tot lanh!",
            "TempId": 12640
        },
        {
            "NetworkID": 5,
            "TempContent": "Cam on quy khach da su dung dich vu cua chung toi. Chuc quy khach mot ngay tot lanh!",
            "TempId": 12647
        },
        {
            "NetworkID": 3,
            "TempContent": "Chuc mung sinh nhat {P2,50}. Kinh chuc QK co nhieu suc khoe, thanh cong va hanh phuc! Nhan dip sinh nhat xin gui den {P2,50} coupon {P2,20}. Tran trong.",
            "TempId": 12899
        },
        {
            "NetworkID": 1,
            "TempContent": "Cam on quy khach da su dung dich vu cua chung toi. Chuc quy khach mot ngay tot lanh!",
            "TempId": 12884
        }
    ],
    "CodeResult": "100",
    "ErrorMessage": "success"
}
```

**Request hợp lệ.**
{% endtab %}

{% tab title="101" %}

{% endtab %}

{% tab title="104" %}
```
```


{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th width="175">Thuộc tính</th><th>Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>NetworkID</td><td>string</td><td>1: Viettel<br>2: Mobi<br>3: Vinaphone<br>4: Vietnammobile<br>5: Gtel<br>6: Itel<br>7: Reddi</td></tr><tr><td>TempContent</td><td>string</td><td>Content đã đăng ký với nhà mạng</td></tr><tr><td>TempId</td><td>string</td><td>TempId của nhà mạng</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu của các ngôn ngữ ở link:**</mark>_ [**Code mẫu**](https://samplefordevelopers.esms.vn/#ca4176c1-a1af-4d93-bf29-81cd9dc3a85c) **.**
