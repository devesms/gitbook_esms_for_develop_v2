# Callback Url

* Khi có trạng thái thực tế của tin nhắn, eSMS sẽ gửi callback trạng thái về endpoint (webhook) của khách hàng thông qua phương thức **HTTPS&#x20;**<mark style="color:green;">**GET**</mark>.
* Callback sẽ được retry 5 lần nếu như url của khách hàng trả timeout. Hết 5 lần mà url của khách hàng vẫn timeout thì sẽ ngừng callback.<br>

## Callback mẫu

### Callback mẫu cho loại tin CSKH:

{% code overflow="wrap" %}
```json
curl --location -g 'https://{{yourportalreceivecallback}}?SMSID=dc712784-9c5f-4c69-b9a8-ea69d56adc9a87&SendFailed=2&SendStatus=5&SendSuccess=0&TotalPrice=0.0000&TotalReceiver=2&TotalSent=2&RequestId=&TypeId=2&telcoid=1&phonenumber=0901888484&switchsmsid='
```
{% endcode %}

### Callback mẫu cho loại tin Quảng cáo:

{% code overflow="wrap" %}
```
curl --location -g 'https://{{yourportalreceivecallback}}?SMSID=82b0bb8aed914a0aab8deba567c9b8c2&SendFailed=0&SendStatus=5&SendSuccess=0&TotalPrice=696987.0000&TotalReceiver=169&TotalSent=169&RequestId=&TypeId=1'
```
{% endcode %}

### Callback mẫu cho loại tin Zalo:

{% code overflow="wrap" %}
```json
curl --location -g 'https://{{yourportalreceivecallback}}?SMSID=f66545d2-c7e2-4603-984e-d2238c363c8292&SendFailed=1&SendStatus=5&SendSuccess=0&TotalPrice=0.0000&TotalReceiver=1&TotalSent=0&RequestId=&TypeId=25&telcoid=2&phonenumber=0901888484&partnerids=&error_info=%22{%5C%22error%5C%22%3A-114%2C%5C%22message%5C%22%3A%5C%22User%20is%20inactive%2C%20or%20reject%20the%20message%2C%20or%20using%20an%20outdated%20Zalo%20version%2C%20or%20other%20internal%20errors%5C%22}%22&oaid=1397492183140006179&tempid=2056446'
```
{% endcode %}

### Callback mẫu cho loại tin Viber:

{% code overflow="wrap" %}
```json
curl --location -g 'https://{{yourportalreceivecallback}}?SMSID=849fe08c19294b02857cf91687021a50250&SendFailed=0&SendStatus=5&SendSuccess=1&TotalPrice=470.0000&TotalReceiver=1&TotalSent=1&RequestId=&TypeId=23&telcoid=2&phonenumber=0901888484'
```
{% endcode %}

### Callback mẫu cho loại tin Zalo tư vấn:

{% code overflow="wrap" %}
```json
curl --location -g 'https://{{yourportalreceivecallback}}?SMSID=7d11c87a22934df390f73ec59d8defd6205&SendFailed=0&SendStatus=5&SendSuccess=1&TotalPrice=60.0000&TotalReceiver=1&TotalSent=1&RequestId=&TypeId=26&phonenumber=312158068343230&error_info=%257B%2522data%2522%3A%257B%2522message_id%2522%3A%2522e1a60e8890be9de4c4ab%2522%2C%2522user_id%2522%3A%252231215806834323092%2522%257D%2C%2522error%2522%3A0%2C%2522message%2522%3A%2522Success%2522%257D____24%2F04%2F2024%252016%3A58%3A01&oaid=4097311281936189049&partnerids=e1a60e8890be9de4c4ab'
```
{% endcode %}

### Callback mẫu cho loại tin Zalo giao dịch:

{% code overflow="wrap" %}
```json
curl --location -g 'https://{{yourportalreceivecallback}}?SMSID=53dbbc6e816f4159a9035a14a787e08f172&SendFailed=0&SendStatus=5&SendSuccess=1&TotalPrice=60.0000&TotalReceiver=1&TotalSent=1&RequestId=&TypeId=26&phonenumber=312158068343230&error_info=%257B%2522data%2522%3A%257B%2522message_id%2522%3A%2522f405841b5f2352790b36%2522%2C%2522user_id%2522%3A%252231215806834323092%2522%257D%2C%2522error%2522%3A0%2C%2522message%2522%3A%2522Success%2522%257D____24%2F04%2F2024%252017%3A07%3A01&oaid=4097311281936189049&partnerids=f405841b5f2352790b36'
```
{% endcode %}

### Callback mẫu cho loại tin Zalo dạng yêu cầu mẫu thông tin người dùng:

{% code overflow="wrap" %}
```json
curl --location -g 'https://{{yourportalreceivecallback}}?SMSID=53dbbc6e816f4159a9035a14a787e08f172&SendFailed=0&SendStatus=5&SendSuccess=1&TotalPrice=60.0000&TotalReceiver=1&TotalSent=1&RequestId=&TypeId=26&phonenumber=312158068343230&error_info=%257B%2522data%2522%3A%257B%2522message_id%2522%3A%2522f405841b5f2352790b36%2522%2C%2522user_id%2522%3A%252231215806834323092%2522%257D%2C%2522error%2522%3A0%2C%2522message%2522%3A%2522Success%2522%257D____24%2F04%2F2024%252017%3A07%3A01&oaid=4097311281936189049&partnerids=f405841b5f2352790b36'
```
{% endcode %}

### Callback mẫu cho loại tin Zalo hành trình

{% code overflow="wrap" %}
```json
curl --location -g 'https://{{yourportalreceivecallback}}?SMSID=7d11c87a22934df390f73ec59d8defd6205&SendFailed=0&SendStatus=5&SendSuccess=1&TotalPrice=220.0000&TotalReceiver=1&TotalSent=1&RequestId=&TypeId=27&phonenumber=312158068343230&error_info=%257B%2522data%2522%3A%257B%2522message_id%2522%3A%2522e1a60e8890be9de4c4ab%2522%2C%2522user_id%2522%3A%252231215806834323092%2522%257D%2C%2522error%2522%3A0%2C%2522message%2522%3A%2522Success%2522%257D____24%2F04%2F2024%252016%3A58%3A01&oaid=4097311281936189049&partnerids=e1a60e8890be9derir3gfbff'
```
{% endcode %}

### **Callback mẫu cho loại tin Zalo gửi bằng UID**

{% code overflow="wrap" %}
```
curl --location --globoff 'https://{{yourportalreceivecallback}}?SMSID=5450d5579bfa466a9f2a5911c82f4037&SendFailed=0&SendStatus=5&SendSuccess=1&TotalPrice=2104.0000&TotalReceiver=1&TotalSent=1&RequestId=&TypeId=25&telcoid=9&phonenumber=5308693166941955879&error_info={%22error%22%3A0%2C%22message%22%3A%22Success%22%2C%22data%22%3A{%22delivery_time%22%3Anull%2C%22message%22%3A%22The%20message%20was%20delivered%20to%20the%20user%27s%20phone%22%2C%22status%22%3A1}}&oaid=3639635426588416370&tempid=523194&partnerids=416f53d0cf0ec7569e19'
```
{% endcode %}

## Thông tin kết quả trả về của callback:

<table><thead><tr><th width="138.5999755859375">Thuộc tính</th><th width="112.199951171875">Kiểu dữ liệu</th><th>Định nghĩa</th></tr></thead><tbody><tr><td>SMSID</td><td>string</td><td>Mã tin nhắn.</td></tr><tr><td>SendFailed</td><td>string</td><td>Số lượng tin nhắn thất bại.</td></tr><tr><td>SendStatus</td><td>string</td><td>Trạng thái tin nhắn<br>1: Chờ duyệt.<br>2: Chờ gửi.<br>4: Từ chối.<br>5: Đã gửi xong (<strong>Kiểm tra thêm SendSuccess/SendFailed để biết tin gửi thành công hay thất bại</strong>).<br>7: Đã gửi chờ báo cáo.</td></tr><tr><td>SendSuccess</td><td>string</td><td>Số lượng tin thành công.</td></tr><tr><td>Totalprice</td><td>string</td><td>Tổng tiền đơn.</td></tr><tr><td>TotalReceiver</td><td>string</td><td>Tổng số người nhận.</td></tr><tr><td>TotalSent</td><td>string</td><td>Tổng số lượng tin được gửi.</td></tr><tr><td>RequestId</td><td>string</td><td>Mã request của khách hàng.</td></tr><tr><td>TypeId</td><td>string</td><td>Loại tin nhắn<br>1: tin quảng cáo.<br>2: tin chăm sóc khách hàng.<br>23: tin viber.<br>24: tin zalo ưu tiên.<br>25: tin zalo bình thường.</td></tr><tr><td>telcoid</td><td>string</td><td>Nhà mạng<br>1: Viettel, 2: Mobi, 3: Vina, 4: Vietnammobile, 5: Gtel, 6: Itel, 7: Reddi.</td></tr><tr><td>phonenumber</td><td>string</td><td>Số điện thoại người nhận.<br><br>Riêng đối với <a href="https://developers.esms.vn/esms-api/ham-gui-tin/tin-nhan-zalo-1">API gửi tin Zalo bằng UID</a> thì trường này là zalo userid của người nhận.</td></tr><tr><td>partnerids</td><td>string</td><td>Mã giao dịch của Zalo <strong>(chỉ có đối với tin zalo).</strong></td></tr><tr><td>error_info</td><td>string</td><td>Mã lỗi của tin nhắn <strong>(chỉ có đối với tin zalo).</strong></td></tr><tr><td>oaid</td><td>string</td><td>ID của Oa gửi tin <strong>(chỉ có đối với tin zalo).</strong></td></tr><tr><td>tempid</td><td>string</td><td>Tempid gửi tin <strong>(chỉ có đối với tin zalo).</strong></td></tr></tbody></table>

