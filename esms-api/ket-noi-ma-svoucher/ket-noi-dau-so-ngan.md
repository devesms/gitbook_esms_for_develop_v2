# Kết nối đầu số ngắn

## _**1: Thông tin kết nối:**_

### **Bước 1:** Khi khách hàng gửi tin nhắn lên đầu số ngắn, phía eSMS sẽ gọi 1 request như bên dưới sang đối tác

{% code title="HTTP GET" overflow="wrap" fullWidth="false" %}
```http
http://domain.abc/receive_mo?sender={{sender}}&content={{content}}&serviceNumber={{serviceNumber}}&keyword={{keyword}}&sign={{sign}}&cpid={{cpid}}&smsid={{smsid}}&receiverTime={{receiverTime}}
```
{% endcode %}

Trong đó:

* `http://domain.abc/receive_mo` : là link mà đối tác cung cấp cho eSMS để nhận các tin nhắn MO từ khách hàng

<table><thead><tr><th width="198">Tham số</th><th width="120">Kiểu</th><th>Mô tả</th></tr></thead><tbody><tr><td><pre><code>cpid
</code></pre></td><td>string</td><td>Là mã định danh CP do eSMS cung cấp.<br>Bao gồm CPID và PrivateKey</td></tr><tr><td><pre><code>sign
</code></pre></td><td>string</td><td>chữ ký số, tạo bởi chuỗi bí mật của ứng dụng tương ứng cpid</td></tr><tr><td><pre><code>smsid
</code></pre></td><td>string</td><td>là một chuỗi do eSMS.vn cung cấp. Đây là số duy nhất tương ứng với một tin nhắn. Số này dùng để kiểm tra các trường hợp trùng và đối chiếu đối soát về sau.</td></tr><tr><td><pre><code>sender
</code></pre></td><td>string</td><td>số điện thoại khách hàng, định dạng quốc tế (có 84)</td></tr><tr><td><pre><code>serviceNumber
</code></pre></td><td>string</td><td>đầu số dịch vụ (8041, 8079, 6088, ...)</td></tr><tr><td><pre><code>keyword
</code></pre></td><td>string</td><td>từ đầu tiên trong cú pháp MO</td></tr><tr><td><pre><code>content
</code></pre></td><td>string</td><td>nội dung mà khách hàng nhắn</td></tr><tr><td><pre><code>receiverTime
</code></pre></td><td>string</td><td>Thời gian nhận được MO, có format yyyyMMddhhmmss</td></tr></tbody></table>

### **Bước 2:** Đối tác xử lý request này và trả về thông tin có dạng sau:

```
<ClientResponse>
   <Message>Nội dung tin nhắn trả về</Message>
   <Smsid>ID của tin nhắn gửi lên</Smdid>
   <Receiver>Số điện thoại người nhận</Receiver>
</ClientResponse>
```

## _**2. Tạo khóa bí mật:**_

Sign: được băm từ 5 tham số: `Cpid`, `smsid`, `content`, `receiveTime` và `PrivateKey` \
hashValue(value1, value2,…) = MD5(value1 + value2 + … + private\_key) \
\
Ví dụ: đối tác A sử dụng dịch vụ X có khóa bí mật là 17417a0d20114d36a902e49cad0e97f3 thì giá trị băm được tính như sau: \
hash("abcdef", "1234", "xyz") = MD5("abcdef1234xyz17417a0d20114d36a902e49cad0e97f3");\
\
Format thời gian: giá trị thời gian được truyền dưới định dạng sau: `yyyyMMddhhmmss`. Ví dụ ngày 28 tháng 2 năm 2013, lúc 13 giờ 01 phút 01 giây: 20130228130101

### **Mã lệnh mẫu**

Trong việc giao tiếp giữa client và server, có một giá trị băm gửi gửi kèm để đảm bảo toàn bộ các thông tin là chính xác. Đoạn lệnh mẫu tính giá trị băm xin tham khảo dưới đây.

* **.NET**

```csharp
string GetHash(string s)
{
  UTF8Encoding ue = new UTF8Encoding();
  byte[] v = ue.GetBytes(s);
  byte[] hashValue = new MD5CryptoServiceProvider().ComputeHash(v);
  return Convert.ToBase64String(hashValue);
}
```

* **Java**

```java
String getHash(String sSrc) throws Exception {
  Charset utf8Charset = Charset.forName("UTF-8");
  byte[] textBytes = sSrc.getBytes(utf8Charset);
  MessageDigest m = MessageDigest.getInstance("MD5");
  byte[] digest = m.digest(textBytes);
  String sEncodedText = B64.b64encode(digest);
  return sEncodedText;
} 
```

* **PHP**

```php
<?php
    $str = 'qwertyuiop';
    $hash = base64_encode(md5($str, true));
?>
```
