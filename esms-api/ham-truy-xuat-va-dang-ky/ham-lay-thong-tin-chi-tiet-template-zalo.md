# Hàm lấy thông tin chi tiết template Zalo

## HTTP request

\
<mark style="color:green;">**`GET`**</mark> [https://rest.esms.vn/MainService.svc/json/GetZnsTemplateInfo?TemplateId=\{{TemplateId\}}\&ApiKey=\{{ApiKey\}}\&SecretKey=\{{SecretKey\}}\&OAId=\{{OAId\}}](https://rest.esms.vn/MainService.svc/json/GetZnsTemplateInfo?TemplateId=\{{TemplateId\}}\&ApiKey=\{{ApiKey\}}\&SecretKey=\{{SecretKey\}}\&OAId=\{{OAId\}})

* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location -g 'https://rest.esms.vn/MainService.svc/json/GetZnsTemplateInfo?TemplateId={{TemplateId}}&ApiKey={{ApiKey}}&SecretKey={{SecretKey}}&OAId={{OAId}}'
```

* **Cấu trúc body của request:**

<table><thead><tr><th width="136">Tham số</th><th width="136">Kiểu dữ liệu</th><th width="150" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>TemplateId</td><td>string</td><td>true</td><td>Template của Zalo OA mà khách hàng đăng kí với eSMS.</td></tr><tr><td>ApiKey</td><td>string</td><td>true</td><td>ApiKey của tài khoản</td></tr><tr><td>SecretKey</td><td>string</td><td>true</td><td>SecretKey của tài khoản</td></tr><tr><td>OAId</td><td>string</td><td>true</td><td>Zalo OA ID, là ID của trang Zalo Offical Account của doanh nghiệp. <br>Doanh nghiệp cần đăng nhập vào trang quản trị của Zalo OA để lấy phần Zalo OA ID này.<br><strong>Chú ý: sẽ phải đăng ký trước khi sử dụng.</strong></td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```
{
    "Data": {
        "ListButtons": [
            {
                "Content": "https://oa.zalo.me/4097311281936189049",
                "Title": "Quan tâm OA",
                "Type": 2
            }
        ],
        "ListParams": [
            {
                "AcceptNull": false,
                "MaxLength": 100,
                "MinLength": 0,
                "Name": "customer_name",
                "Require": true,
                "Type": "STRING"
            },
            {
                "AcceptNull": false,
                "MaxLength": 100,
                "MinLength": 0,
                "Name": "product_name",
                "Require": true,
                "Type": "STRING"
            },
            {
                "AcceptNull": false,
                "MaxLength": 30,
                "MinLength": 0,
                "Name": "order_code",
                "Require": true,
                "Type": "STRING"
            },
            {
                "AcceptNull": false,
                "MaxLength": 30,
                "MinLength": 0,
                "Name": "date",
                "Require": true,
                "Type": "STRING"
            }
        ],
        "PreviewUrl": "https://account.zalo.cloud/znspreview/NqFkYJ14yilzdlAXteG_rQ==",
        "Reason": "Template đã được duyệt",
        "Status": "ENABLE",
        "TemplateId": 267247,
        "TemplateName": "Đánh giá dịch vụ - text",
        "TemplateQuality": "null",
        "TemplateTag": "TRANSACTION",
        "Timeout": 7200000
    },
    "Error": 0,
    "Message": "Success"
}
```

**Request lợp lệ.**
{% endtab %}
{% endtabs %}

* **Cấu trúc thuộc tính data.ListButtons**

<table><thead><tr><th width="161">Thuộc tính</th><th width="166">Kiểu dữ liệu</th><th>Định nghĩa</th></tr></thead><tbody><tr><td>Content</td><td>string</td><td>Đường dẫn liên kết/số điện thoại.</td></tr><tr><td>Title</td><td>string</td><td>Nội dung Button.</td></tr><tr><td>Type</td><td>integer</td><td><p>Danh sách button:</p><p>1: Đến trang của doanh nghiệp<br>2: Gọi điện <br>3: Đến trang thông tin OA <br>4: Đến ứng dụng Zalo Mini App của doanh nghiệp <br>5: Đến trang tải ứng dụng <br>6: Đến trang phân phối sản phẩm <br>7: Đến trang web/Zalo Mini App khác <br>8: Đến ứng dụng khác</p></td></tr></tbody></table>

* **Cấu trúc thuộc tính data.listParams**

<table><thead><tr><th width="162">Thuộc tính</th><th width="167">Kiểu dữ liệu</th><th>Định nghĩa</th></tr></thead><tbody><tr><td>Name</td><td>string</td><td>Tên thuộc tính.</td></tr><tr><td>Require</td><td>boolean</td><td>Tính bắt buộc của thuộc tính.</td></tr><tr><td>Type</td><td>string</td><td>Định dạng validate của thuộc tính.</td></tr><tr><td>MaxLength</td><td>int</td><td>Số kí tự tối đa được truyền vào thuộc tính.</td></tr><tr><td>MinLength</td><td>int</td><td>Số kí tự tối thiểu được truyền vào thuộc tính.</td></tr><tr><td>AcceptNull</td><td>boolean</td><td>Thông tin cho biết thuộc tính có thể nhận giá trị rỗng hay không.</td></tr></tbody></table>

* **Cấu trúc thuộc tính data**

<table><thead><tr><th width="171">Thuộc tính</th><th width="165">Kiểu dữ liệu</th><th>Định nghĩa</th></tr></thead><tbody><tr><td>PreviewUrl</td><td>string</td><td>Đường dẫn đến bản xem trước của template.</td></tr><tr><td>Reason</td><td>string</td><td>Lý do template có trạng thái hiện tại:<br><br>- DISABLE/REJECT: Chi tiết lý do khi template ở trạng thái Disable hoặc Reject.<br>- ENABLE: Template đã được duyệt.<br>- DELETE: Template đã bị xóa.<br>- PENDING_REVIEW: Template đang được kiểm duyệt.<br></td></tr><tr><td>Status</td><td>string</td><td>Trạng thái template. Các trạng thái bao gồm: <br><br>- ENABLE: Trạng thái template được kích hoạt, có thể sử dụng để gửi thông báo ZNS.<br>- PENDING_REVIEW: Trạng thái template chờ kiểm duyệt. <br>- DELETE: Trạng thái template bị xóa. <br>- REJECT: Trạng thái template bị từ chối. <br>- DISABLE: Trạng thái template bị hủy kích hoạt.</td></tr><tr><td>TemplateId</td><td>string</td><td>ID của template.</td></tr><tr><td>TemplateName</td><td>string</td><td>Tên của template.</td></tr><tr><td>TemplateQuality</td><td>string</td><td>Trả về giá trị null cho trường thông tin này.</td></tr><tr><td>TemplateTag</td><td>string</td><td>Loại nội dung của template. Các giá trị trả về: <br><br>- TRANSACTION: Giao dịch <br>- CUSTOMER_CARE: Chăm sóc khách hàng <br>- PROMOTION: Hậu mãi</td></tr><tr><td>Timeout</td><td>long</td><td>Thời gian timeout của template.</td></tr><tr><td>ListButtons</td><td>object array</td><td>Danh sách các buttons/CTAs của template <br>Chỉ áp dụng với 2 loại CTA: primary và secondary. <br>Không hiển thị các CTA từ image module và response button.</td></tr><tr><td>ListParams</td><td>object array</td><td>Danh sách các thuộc tính của template.</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi.md) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#43e884e9-36a4-4272-94bd-c388551e7c60)**.**
