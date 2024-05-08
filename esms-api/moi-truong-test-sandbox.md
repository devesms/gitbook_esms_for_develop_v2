# Môi trường test ( Sandbox)

* Để gửi tin ở môi trường thử nghiệm, eSMS đã cung cấp cho khách hàng môi trường test tin. Khách hàng truyền thêm trường Sandbox vào body gửi. Tin nhắn sẽ không được lưu ở hệ thống eSMS, không tính phí và không về máy khách hàng.
* Truyền Sandbox = 1 cho các api có hỗ trợ môi trường Sandbox.



## **Body mẫu cho gửi thử nghiệm tin nhắn Chăm sóc khách hàng:**

{% code overflow="wrap" %}
```json
curl --location 'https://rest.esms.vn/MainService.svc/json/SendMultipleMessage_V4_post_json/' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey": "{{ApiKey}}",
    "Content": "Cam on quy khach da su dung dich vu cua chung toi. Chuc quy khach mot ngay tot lanh!",
    "Phone": "{{Phone}}",
    "SecretKey": "{{SecretKey}}",
    "Brandname": "Baotrixemay",
    "SmsType": "2",
    "Sandbox": "1"
}'
```
{% endcode %}

## **Body mẫu cho gửi thử nghiệm tin nhắn Zalo:**

{% code overflow="wrap" %}
```json
curl --location 'https://rest.esms.vn/MainService.svc/json/SendZaloMessage_V5_post/' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey": "{{ApiKey}}",
    "SecretKey": "{{SecretKey}}",
    "OAID": "4097311281936189049",
    "Phone": "{{Phone}}",
    "TempData": [
        {
            "key": "otp",
            "value": "686868"
        }
    ],
    "TempID": "205644",
    "Sandbox": "1"
}'
```
{% endcode %}

## Body mẫu cho gửi thử nghiệm tin nhắn Viber:

```json
curl --location 'https://rest.esms.vn/MainService.svc/json/Send_Multiple_Sms_OTT/' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey": "{{ApiKey}}",
    "SecretKey": "{{SecretKey}}",
    "Brandname": "BAT DONG SAN GIA TOT",
    "SmsType": "23",
    "Content": "Chúng tôi vừa mở bán căn hộ ĐẸP NHẤT thuộc siêu dự án- Đất nền sổ đỏ sở hữu lâu dài.",
    "OttImgUrl": "https://freesms.vn/wp-content/uploads/2021/07/esms-la-gi.png",
    "OttLabel": "eSMS.vn",
    "OttUrl": "https://esms.vn",
    "Phones": [
        "{{Phones}}"
    ],
    "IsSandBox": "1"
}'
```

## Body mẫu cho gửi thử nghiệm tin nhắn Quảng cáo:

```json
curl --location 'https://rest.esms.vn/MainService.svc/json/SendMultipleSMSBrandname_json/' \
--header 'Content-Type: application/json' \
--data '{
    "ApiKey":"{{ApiKey}}",
    "SecretKey":"{{SecretKey}}",
    "Content":"TEST SANDBO",
    "SmsType":"1",
    "Brandname":"Svoucher",
    "Phones":["{{Phones1}}","{{Phones2}}","{{Phones3}}"],
    "Sandbox":"1"
}'
```
