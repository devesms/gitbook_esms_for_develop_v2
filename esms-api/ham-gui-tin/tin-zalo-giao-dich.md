# Tin Zalo giao dịch

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> [https://rest.esms.vn/mainservice.svc/json/SendZaloFollowerMessage\_V5\_post\_json/](http://rest.esms.vn/mainservice.svc/json/SendZaloFollowerMessage_V5_post_json/)



* **Content Type:** <mark style="color:orange;">text/plain</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

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

* **Cấu trúc body của request:**

<table><thead><tr><th width="158">Tham số</th><th width="120">Kiểu dữ liệu</th><th width="121" data-type="checkbox">Tính bắt buộc</th><th>Định nghĩa</th></tr></thead><tbody><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản.</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>Secretkey của tài khoản.</td></tr><tr><td>OAID</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này. <br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr><tr><td>user_id</td><td>string</td><td>true</td><td>userid cần gửi đến, đây là userid của zalo.</td></tr><tr><td>template_type</td><td>string</td><td>true</td><td><p>Loại template:<br>- transaction_billing<br>- transaction_order<br>- transaction_reward<br>- transaction_contract<br>- transaction_booking<br>- transaction_membership<br>- transaction_event<br>- transaction_transaction<br>- transaction_account<br>- transaction_internal<br>- transaction_partnership<br>- transaction_education<br>- transaction_rating</p><p></p></td></tr><tr><td>language</td><td>string</td><td>false</td><td><p>Ngôn ngữ sử dụng của tin<br>Giá trị nhận vào:</p><ul><li>language = <strong>VI</strong></li></ul><p>hoặc</p><ul><li>language = <strong>EN</strong></li></ul><p>Khi chọn ngôn ngữ các nội dung mặc định của mẫu tin sẽ chuyển sang ngôn ngữ tương ứng.</p></td></tr><tr><td>image_url</td><td>string</td><td>true</td><td>Đường link hình ảnh đính kèm.</td></tr><tr><td>align</td><td>string</td><td>false</td><td><p></p><p>Chấp nhận 3 giá trị</p><ul><li>left (hoặc để trống): canh lề bên trái.</li><li>center: canh lề giữa.</li><li>right: canh lề bên phải.</li></ul></td></tr><tr><td>table</td><td>string</td><td>true</td><td><p><strong>Cấu trúc 1 phần tử trong table là:</strong><br>{<br> "key": "giá trị của key" // maxlength = 25 <br>"value": "giá trị của value" // maxlength = 100<br> }<br><mark style="color:red;">Trong đó bắt buộc phải có 1 trong 2 phần tử dưới đây:</mark><br>VI: <br>{ <br>"key": "Mã..." // bắt đầu là "Mã", dùng định danh người nhận <br>"value": "Giá trị tự do" <br>}</p><p>EN:<br> { <br>"key": "...Code..." // bắt buộc có chứa "Code" trong key <br>"value": "Giá trị tự do"<br> }<br><mark style="color:red;">Hoặc:</mark><br>VI:</p><p> {<br> "key": "Tên khách hàng" // key có giá trị cố định "Tên khách hàng" "value": "Giá trị tự do"<br> }</p><p>EN:</p><p> {<br> "key": "Customer Name" // key có giá trị cố định "Customer Name" "value": "Giá trị tự do" <br>}<br><mark style="color:red;">Key “Trạng thái” / “Status” là key duy nhất hiện tại được phép sử dụng tham số “Style”:</mark><br>VN: <br>{ <br>"key": "Trạng thái" // key có giá trị cố định "Trạng thái"<br> "value": "Giá trị tự do"<br> "style": "yellow" // Giá trị hợp lệ: green, blue, yellow, red, grey <br>}</p><p>EN:<br> { <br>"key": "Status" // key có giá trị cố định "Status"<br> "value": "Giá trị tự do" <br>"style": "yellow" // Giá trị hợp lệ: green, blue, yellow, red, grey<br> }<br><em><strong>****Lưu ý: có thể khai báo thêm tối đa 5 phần tử tùy ý.</strong></em><br></p></td></tr><tr><td>button</td><td>string</td><td>false</td><td>Có thể thêm tối đa 4 dòng.</td></tr><tr><td>Sandbox</td><td>string</td><td>false</td><td>1: Tin gửi ở môi trường test, dùng để kiểm tra kết nối và các thông số tích hợp, không về tin nhắn, không trừ tiền.<br>0: Tin gửi ở môi trường bình thường, có về tin nhắn.</td></tr><tr><td>CallbacUrl</td><td>string</td><td>false</td><td>eSMS sẽ trả về kết quả của tin nhắn này. Xem body mẫu <a href="https://samplefordevelopers.esms.vn/#cd0e23a3-5aa5-4198-a8bb-be0d8e450df9">ở đây</a>. <br>Xem chi tiết <a href="https://developers.esms.vn/esms-api/callback-url">ở đây</a>.</td></tr><tr><td>SendDate</td><td>string</td><td>false</td><td>Thời gian hẹn gửi của tin.<br>Không truyền khi tin muốn tin nhắn gửi đi liền.<br>Định dạng: yyyy-mm-dd hh:MM:ss</td></tr></tbody></table>



***

* **Response**

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
