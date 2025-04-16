# Tin Zalo giao dịch

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/mainservice.svc/json/SendZaloFollowerMessage\_V5\_post\_json/](http://rest.esms.vn/mainservice.svc/json/SendZaloFollowerMessage_V5_post_json/)



* **Content Type:** <mark style="color:orange;">text/plain</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

{% code overflow="wrap" %}
```json
curl --location 'https://rest.esms.vn/mainservice.svc/json/SendZaloFollowerMessage_V5_post_json/' \
--header 'Content-Type: text/plain' \
--data '{
    "ApiKey": "{{ApiKey}}",
    "SecretKey": "{{SecretKey}}",
    "OAID": "{{OAID}}",
    "Payload": {
        "recipient": {
            "user_id": "{{user_id}}"
        },
        "message": {
            "attachment": {
                "type": "template",
                "payload": {
                    "template_type": "transaction_order",
                    "language": "VI",
                    "elements": [
                        {
                            "image_url": "https://minio.esms.vn/blogimg/agent-1/BlogImg/full_cccc34d4-3a46-4644-8613-1b226203c5d5.png",
                            "type": "banner"
                        },
                        {
                            "type": "header",
                            "content": "Trạng thái đơn hàng",
                            "align": "left"
                        },
                        {
                            "type": "text",
                            "align": "left",
                            "content": "• Cảm ơn bạn đã mua hàng tại cửa hàng.<br>• Thông tin đơn hàng của bạn như sau:"
                        },
                        {
                            "type": "table",
                            "content": [
                                {
                                    "value": "eSMS-001",
                                    "key": "Mã khách hàng"
                                },
                                {
                                    "style": "yellow",
                                    "value": "Đang giao",
                                    "key": "Trạng thái"
                                },
                                {
                                    "value": "250,000đ",
                                    "key": "Giá tiền"
                                }
                            ]
                        },
                        {
                            "type": "text",
                            "align": "center",
                            "content": "📲 Lưu ý điện thoại. Xin cảm ơn!"
                        }
                    ],
                    "buttons": [
                        {
                            "title": "Kiểm tra lộ trình",
                            "image_icon": "https://img.icons8.com/?size=100&id=kJlyCVWJrclv&format=png&color=000000",
                            "type": "oa.open.url",
                            "payload": {
                                "url": "https://esms.vn/huong-dan/huong-dan-tich-hop/huong-dan-tich-hop-api-cua-esms-vao-website"
                            }
                        },
                        {
                            "title": "Xem lại giỏ hàng",
                            "image_icon": "https://img.icons8.com/?size=100&id=S2Z1vzGMFT1v&format=png&color=000000",
                            "type": "oa.open.url",
                            "payload": {
                                "url": "https://esms.vn/huong-dan/huong-dan-su-dung"
                            }
                        },
                        {
                            "title": "Liên hệ tổng đài",
                            "image_icon": "https://img.icons8.com/?size=100&id=KKBDB20a4V6t&format=png&color=000000",
                            "type": "oa.open.phone",
                            "payload": {
                                "phone_code": "0901888484"
                            }
                        }
                    ]
                }
            }
        }
    }
}'
```
{% endcode %}

* **Cấu trúc body của request:**

<table><thead><tr><th width="158">Tham số</th><th width="120">Kiểu dữ liệu</th><th width="121" data-type="checkbox">Tính bắt buộc</th><th>Định nghĩa</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này. <br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>Sandbox</td><td>string</td><td>false</td><td>1: Tin gửi ở môi trường test, dùng để kiểm tra kết nối và các thông số tích hợp, không về tin nhắn, không trừ tiền.<br>0: Tin gửi ở môi trường bình thường, có về tin nhắn.</td></tr><tr><td>CallbackUrl</td><td>string</td><td>false</td><td>eSMS sẽ trả về kết quả của tin nhắn này. Xem body mẫu <a href="https://samplefordevelopers.esms.vn/#cd0e23a3-5aa5-4198-a8bb-be0d8e450df9">ở đây</a>. <br>Xem chi tiết <a href="https://developers.esms.vn/esms-api/callback-url">ở đây</a>.</td></tr><tr><td>SendDate</td><td>string</td><td>false</td><td>Thời gian hẹn gửi của tin.<br>Không truyền khi tin muốn tin nhắn gửi đi liền.<br>Định dạng: yyyy-mm-dd hh:MM:ss</td></tr><tr><td>Payload</td><td>Object</td><td>true</td><td>Chứa nội dung cần gửi</td></tr></tbody></table>

**Cấu trúc thuộc tính recipient**

<table><thead><tr><th width="151.933349609375">Tham số</th><th width="130.5333251953125">Kiểu dữ liệu</th><th width="124.2666015625" data-type="checkbox">Tính bắt buộc</th><th>Định nghĩa</th></tr></thead><tbody><tr><td>user_id</td><td>string</td><td>true</td><td>ID của người nhận.</td></tr></tbody></table>

**Cấu trúc thuộc tính message**

<table><thead><tr><th width="153">Tham số</th><th width="125.2667236328125">Kiểu dữ liệu</th><th width="126.2667236328125" data-type="checkbox">Tính bắt buộc</th><th>Định nghĩa</th></tr></thead><tbody><tr><td>attachment</td><td>object</td><td>true</td><td>Attachment cần gửi</td></tr></tbody></table>

**Cấu trúc thuộc tính message.attachment**

<table><thead><tr><th width="151.933349609375">Tham số</th><th width="125.199951171875">Kiểu dữ liệu</th><th width="131.5333251953125" data-type="checkbox">Tính bắt buộc</th><th>Định nghĩa</th></tr></thead><tbody><tr><td>type</td><td>string</td><td>true</td><td><p>Loại attachment<br></p><p>Giá trị nhận vào bắt buộc:</p><ul><li><code>type</code> = template</li></ul></td></tr><tr><td>payload</td><td>object</td><td>true</td><td>Chứa payload của attachment muốn gửi.</td></tr></tbody></table>

**Cấu trúc thuộc tính message.attachment.payload**

<table><thead><tr><th width="154.066650390625">Tham số</th><th width="123.2000732421875">Kiểu dữ liệu</th><th width="131.5333251953125" data-type="checkbox">Tính bắt buộc</th><th>Định nghĩa</th></tr></thead><tbody><tr><td>template_type</td><td>string</td><td>true</td><td><p>Loại template<br></p><ul><li>transaction_billing</li><li>transaction_order</li><li>transaction_reward</li><li>transaction_contract</li><li>transaction_booking</li><li>transaction_membership</li><li>transaction_event</li><li>transaction_transaction</li><li>transaction_account</li><li>transaction_internal</li><li>transaction_partnership</li><li>transaction_education</li><li>transaction_rating</li></ul></td></tr><tr><td>language</td><td>string</td><td>false</td><td><p>Ngôn ngữ sử dụng của tin<br><br>Giá trị nhận vào:</p><ul><li><code>language</code> = <strong>VI</strong></li></ul><p>hoặc</p><ul><li><code>language</code> = <strong>EN</strong></li></ul><p>Khi chọn ngôn ngữ các nội dung mặc định của mẫu tin sẽ chuyển sang ngôn ngữ tương ứng</p></td></tr><tr><td>elements</td><td>array</td><td>true</td><td>Các đối tượng của template.<br><br>Xem thêm mục <strong>message.attachment.payload.elements</strong> bên dưới</td></tr><tr><td>buttons</td><td>array</td><td>false</td><td>Các nút nhấn CTA (tùy chọn có hoặc không, tối đa 4 button) <br>Xem thêm mục <strong>message.attachment.payload.buttons</strong> bên dưới</td></tr></tbody></table>

**Cấu trúc tham số message.attachment.payload.elements**

<table><thead><tr><th width="104.99993896484375">Type</th><th width="112.933349609375">Thuộc tính</th><th width="106.13330078125">Kiểu dữ liệu</th><th width="116.800048828125" data-type="checkbox">Tính bắt buộc</th><th>Định nghĩa</th></tr></thead><tbody><tr><td><strong>banner</strong></td><td>image_url</td><td>string</td><td>true</td><td><strong>image_url</strong> : Đường dẫn đến ảnh<br>Các định dạng ảnh hỗ trợ: jpg và png<br>Dung lượng tối đa: 1MB<br>Tỉ lệ kích thước ảnh (height :width): từ 1:5 đến 1:1 (ảnh vuông)</td></tr><tr><td><strong>header</strong></td><td>content</td><td>string</td><td>true</td><td>Nội dung của header, tối đa 100 ký tự.</td></tr><tr><td></td><td>align</td><td>string</td><td>false</td><td><p>Chấp nhận 3 giá trị<br></p><ul><li>left (hoặc để trống): canh lề bên trái</li><li>center: canh lề giữa</li><li>right: canh lề bên phải</li></ul></td></tr><tr><td><strong>text (lưu ý tối đa được 2 đoạn text)</strong></td><td>content</td><td>string</td><td>true</td><td>Nội dung của text, tối đa 250 ký tự mỗi đoạn</td></tr><tr><td></td><td>align</td><td>string</td><td>false</td><td><p>Chấp nhận 3 giá trị<br></p><ul><li>left (hoặc để trống): canh lề bên trái</li><li>center: canh lề giữa</li><li>right: canh lề bên phải</li></ul></td></tr><tr><td><strong>table</strong></td><td>content</td><td>array</td><td>true</td><td><p>Cấu trúc 1 phần tử trong table là:<br>{<br>"key": "giá trị của key" // maxlength = 25<br>"value": "giá trị của value" // maxlength = 100<br>}<br><mark style="background-color:orange;">Trong đó bắt buộc phải có 1 trong 2 phần tử dưới đây:</mark><br>VI:<br>{<br>"key": "Mã..." // bắt đầu là "Mã", dùng định danh người nhận<br>"value": "Giá trị tự do"<br>}</p><p>EN:<br>{<br>"key": "...Code..." // bắt buộc có chứa "Code" trong key<br>"value": "Giá trị tự do"<br>}<br><mark style="background-color:orange;">Hoặc:</mark><br>VI:</p><p>{<br>"key": "Tên khách hàng" // key có giá trị cố định "Tên khách hàng" "value": "Giá trị tự do"<br>}</p><p>EN:</p><p>{<br>"key": "Customer Name" // key có giá trị cố định "Customer Name" "value": "Giá trị tự do"<br>}<br><mark style="background-color:orange;">Key “Trạng thái” / “Status” là key duy nhất hiện tại được phép sử dụng tham số “Style”:</mark><br>VN:<br>{<br>"key": "Trạng thái" // key có giá trị cố định "Trạng thái"<br>"value": "Giá trị tự do"<br>"style": "yellow" // Giá trị hợp lệ: green, blue, yellow, red, grey<br>}</p><p>EN:<br>{<br>"key": "Status" // key có giá trị cố định "Status"<br>"value": "Giá trị tự do"<br>"style": "yellow" // Giá trị hợp lệ: green, blue, yellow, red, grey<br>}<br>****<strong>Lưu ý</strong>: có thể khai báo thêm tối đa 5 phần tử tùy ý.</p></td></tr></tbody></table>

**Cấu trúc tham số message.attachment.payload.buttons**

<table><thead><tr><th width="114.60015869140625">Thuộc tính</th><th width="106.7333984375">Kiểu dữ liệu</th><th width="113.4666748046875" data-type="checkbox">Tính bắt buộc</th><th>Định nghĩa</th></tr></thead><tbody><tr><td>title</td><td>string</td><td>true</td><td><p>Tiêu đề của button</p><p>Lưu ý: Tiêu đề không được vượt quá 35 ký tự</p></td></tr><tr><td>image_icon</td><td>string</td><td>true</td><td><p>Có thể tryền:</p><ul><li>image url của hình ảnh</li><li>attachment_id sau khi sử dụng API upload hình ảnh</li><li>để trống hoặc “default”: để sử dụng imaeg icon mặc định của Zalo</li></ul><p>Lưu ý: Kích thước hình ảnh tối ưu: 100px * 100px</p></td></tr><tr><td>type, payload</td><td>object</td><td>true</td><td>Xem thêm mục <strong>Cấu trúc payload cho các loại action được hỗ trợ</strong> bên dưới</td></tr></tbody></table>

**Cấu trúc payload cho các loại action được hỗ trợ**

<table><thead><tr><th width="135.933349609375">Giá trị type</th><th width="195.666748046875">Kiểu dữ liệu của payload</th><th>Giá trị payload và kết quả khi người quan tâm bấm vào</th></tr></thead><tbody><tr><td>oa.open.url</td><td>string</td><td><p>Data là một Url sẽ được mở trong ứng dụng Zalo khi người quan tâm bấm vào button. Ví dụ:<br><code>{</code><br>    <code>"title": "OPEN URL",</code><br>    <code>"payload" : {</code><br>    <code>"url": "https://developers.zalo.me/"</code><br>    <code>},</code><br>    <code>"type": "oa.open.url"</code><br><code>}</code></p><ul><li><strong>Chú ý:</strong>  Giới hạn cho thuộc tính "title" là 100 kí tự.</li></ul></td></tr><tr><td>oa.query.show</td><td>string</td><td><p>Data là một chuỗi ký tự ví dụ “#callback_data”. Khi người quan tâm bấm vào button, hệ thống sẽ gửi một tin nhắn có nội dung chứa trong data từ người quan tâm đến Official Account. Tin nhắn này sẽ hiện trên cửa sổ chat trên máy của người quan tâm. Ví dụ:<br><code>{</code><br>    <code>"title": "QUERY SHOW",</code><br>    <code>"type": "oa.query.show",</code><br>    <code>"payload": "#callback_data"</code><br><code>}</code><br></p><ul><li><p><strong>Chú ý:</strong>  </p><ul><li>Giới hạn cho thuộc tính "title" là 100 kí tự.</li><li>Giới hạn cho thuộc tính "payload" là 1000 kí tự.</li></ul></li></ul></td></tr><tr><td>oa.query.hide</td><td>string</td><td><p>Data là một chuỗi ký tự ví dụ “#callback_data”. Khi người quan tâm bấm vào button, hệ thống sẽ gửi một tin nhắn có nội dung chứa trong data từ người quan tâm đến Official Account. Tin nhắn này sẽ bị ẩn trên cửa sổ chat trên máy của người quan tâm. Ví dụ:<br><code>{</code><br>    <code>"title": "QUERY HIDE",</code><br>    <code>"type": "oa.query.hide",</code><br>    <code>"payload": "#callback_data"</code><br><code>}</code><br></p><ul><li><p><strong>Chú ý:</strong>  </p><ul><li>Giới hạn cho thuộc tính "title" là 100 kí tự.</li><li>Giới hạn cho thuộc tính "payload" là 1000 kí tự.</li></ul></li></ul></td></tr><tr><td>oa.open.sms</td><td>object</td><td><p>Data đối tượng json chứa 2 thuộc tính “content” và “phoneCode”. Ví dụ:<br><code>{</code><br>    <code>"title": "OPEN SMS",</code><br>    <code>"type": "oa.open.sms",</code><br>    <code>"payload": {</code><br>    <code>"content":"alo",</code><br>    <code>"phone_code":"84919018791"</code><br><code>}</code><br><code>}</code><br></p><p>Khi người quan tâm click vào button, cửa sổ sms trên điện thoại của người quan tâm sẽ được mở với 2 thông tin sẵn có là phone code và nội dung tin nhắn trong data.</p><ul><li><p><strong>Chú ý:</strong></p><ul><li>Giới hạn cho thuộc tính "title" là 100 kí tự.</li><li>Thuộc tính "content" có giới hạn là 160 kí tự.</li></ul></li></ul></td></tr><tr><td>oa.open.phone</td><td>object</td><td><p>Data số điện thoại sẽ nhập vào khi bật ứng dụng gọi điện, ví dụ:<br><code>{</code><br>    <code>"title": "OPEN PHONE",</code><br>    <code>"type": "oa.open.phone",</code><br>    <code>"payload":{</code><br>    <code>"phone_code":"84919018791"</code><br><code>}</code><br><code>}</code><br></p><p>Khi người quan tâm click vào button, cửa sổ call trên điện thoại của người quan tâm sẽ được mở với thông tin sẵn có là phone number trong data.</p><ul><li><strong>Chú ý:</strong>  Giới hạn cho thuộc tính "title" là 100 kí tự.</li></ul></td></tr></tbody></table>



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
{% endtabs %}

* **Cấu trúc body của response:**

| Thuốc tính   | Kiểu dữ liệu | Mô tả                              |
| ------------ | ------------ | ---------------------------------- |
| CodeResult   | string       | Mã trả về.                         |
| SMSID        | string       | ID tin nhắn do esms trả về.        |
| ErrorMessage | string       | Thông tin lỗi trả về (nếu có lỗi). |

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [_**Link code mẫu**_](https://samplefordevelopers.esms.vn/#eb8ca6b8-796c-463e-95b7-3601c8f49b33)_**.**_
