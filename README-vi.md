# Hướng dẫn & Thông tin về Minecraft Cloud Shell

Đây là dự án giúp bạn có thể lưu trữ (host) một máy chủ Minecraft trên nền tảng đám mây.

**Các tính năng đã được bổ sung vào dự án:**
- Hỗ trợ nhiều loại máy chủ Bedrock.
- Giao diện gọn gàng và thân thiện.
- Hỗ trợ thêm nhiều loại máy chủ Java *(ví dụ: Sponge, Paper, Fabric, NeoForge, v.v.)*.
- **Tự động nhận diện phiên bản Java thông minh** *(tự động tải JDK 8, 17, 21 hoặc 25 tùy theo phiên bản Minecraft của bạn)*.
- **Đảm bảo an toàn bộ nhớ** *(tự động dành riêng 1GB RAM cho hệ điều hành máy chủ để tránh lỗi hết bộ nhớ)*.
- Bổ sung chức năng quản lý máy chủ.
- Các script dễ sử dụng hơn *(ví dụ: [**./uninstall**](https://github.com/kleqing/mchost/blob/main/README.md#uninstallremove-the-server) giúp bạn dễ dàng xóa máy chủ)*.
- Tự động thiết lập EULA ngay lập tức *(bỏ qua hoàn toàn bước này, giúp việc quản lý dễ dàng hơn)*.
- Cài đặt máy chủ nhanh hơn *(thông thường chỉ mất khoảng 30 giây để thiết lập một máy chủ)*.

### Danh sách công việc
- [x] Hỏi người dùng phiên bản Java cụ thể mà họ muốn sử dụng.
- [x] Thêm các nguồn tải từ bên thứ ba vào danh sách.
- [x] Tự động nhập lệnh vào máy chủ. (Ứng dụng AFK)
- [x] Đơn giản hóa việc tải tệp lên Google Drive. (Sử dụng Cloud Shell Editor)
- [x] Cập nhật script.

### Cấu hình máy chủ
- **Hệ điều hành:** Debian GNU/Linux 10 (buster) x86_64
- **RAM:** 8GB đến 16GB
- **Vị trí:** Phụ thuộc vào vị trí địa lý thực tế của bạn.
- **Dung lượng lưu trữ:** Khoảng 5GB
- **CPU:** AMD EPYC (2) 7B12 @ 2.249GHz hoặc Intel Xeon (4) @ 2.199GHz

Bạn có thể xem chính xác cấu hình máy chủ bằng lệnh `./specinfo`.

### Dịch vụ được sử dụng
- [playit.gg](https://playit.gg)
- [console.cloud.google.com](https://console.cloud.google.com)

## Cài đặt

- Kích hoạt [Google Cloud Shell](https://console.cloud.google.com/) trên Google Cloud.
- Clone dự án GitHub này vào cửa sổ dòng lệnh:

```bash
git clone https://github.com/kleqing/mchost
```

- Truy cập thư mục `mchost`:

```bash
cd mchost
```

- Cấp quyền thực thi cho tất cả các lệnh:

```bash
chmod +x *
```

- Chạy script cài đặt:

```bash
./install
```

Làm theo các bước cài đặt hiển thị trong cửa sổ dòng lệnh.

- Chạy script khởi động máy chủ:

```bash
./startserver
```

*(Bạn chỉ cần thực hiện bước này nếu đã chọn `No` trong quá trình cài đặt.)*

## Thiết lập bổ sung cho máy chủ Java (có thể bỏ qua)

*(Chỉ áp dụng cho máy chủ Java, bao gồm cả Nukkit, hoặc trường hợp script EULA không hoạt động với bạn.)*

Khi khởi động máy chủ lần đầu, máy chủ có thể không chạy được vì bạn cần chấp nhận **EULA** để máy chủ hoạt động bình thường.

- Truy cập thư mục máy chủ và chấp nhận [EULA](https://www.minecraft.net/en-us/eula):

```bash
cd server
```

```bash
nano eula.txt
```

- Đảm bảo tệp `eula.txt` có nội dung sau:

```text
eula=true
```

Nhấn `Ctrl + W`, sau đó nhấn `Y` để lưu và nhấn `Enter` để thoát trình chỉnh sửa văn bản.

- Quay lại thư mục chính:

```bash
cd ..
```

- [Khởi động lại máy chủ](https://github.com/kleqing/mchost/blob/main/README.md#restarting-your-server).

Bây giờ mọi thứ sẽ hoạt động bình thường và sẵn sàng sử dụng. Bạn có thể kiểm tra máy chủ đã chạy hay chưa bằng lệnh `screen -r server`.

## Kết nối vào máy chủ

- Để tham gia máy chủ, hãy khởi động máy chủ bằng lệnh `./startserver` *(nếu bạn chưa khởi động)*, sau đó chạy lệnh:

```bash
screen -r playit
```

- Nhấn vào **Claim URL**. Trang được mở ra sẽ hiển thị IP máy chủ và Tunnel Server của bạn.
- Trên trang đó, cuộn xuống và nhấn **Add Tunnel** tại mục Minecraft Java/Bedrock. Tiếp theo, nhấn **Add** bên cạnh mục **Local server address**.
- Sao chép địa chỉ IP chuyên dụng được tạo ra (có dạng tương tự `auto.playit.gg`), sau đó nhập địa chỉ này vào mục Server Address trong Minecraft. Bây giờ bạn đã có thể vào máy chủ.

*(Lưu ý: Nếu muốn thay đổi Claim URL, bạn cần dừng máy chủ. Thao tác này sẽ đặt lại IP máy chủ của bạn.)*

## Truy cập Console của máy chủ

- Để truy cập console của máy chủ, hãy mở session sau:

```bash
screen -r server
```

Để dừng hoàn toàn máy chủ, bạn có thể chạy `./stopserver` trong Linux console hoặc nhập `exit` hay `stop` trong Minecraft console.

## Tách khỏi Screen/Session

Để tách khỏi session mà không đóng session đó, hãy sử dụng tổ hợp phím:

`CTRL + A`, sau đó nhấn `D`.

## Launcher bên thứ ba

- Nếu bạn đang sử dụng phiên bản **Minecraft Java Edition** không chính thức (cracked):

- Mở tệp `server.properties` và tìm thuộc tính `online-mode`:

```bash
nano server.properties
```

- Đổi giá trị từ `true` thành `false`:

```properties
online-mode=false
```

Nhấn `Ctrl + W`, sau đó nhấn `Y` để lưu và nhấn `Enter` để thoát trình chỉnh sửa văn bản.

- [Khởi động lại](https://github.com/kleqing/mchost/blob/main/README.md#restarting-your-server) máy chủ sau khi áp dụng thay đổi.

## Truy cập các tệp của máy chủ

Nếu muốn truy cập các tệp máy chủ, hãy mở **Open Editor** ở góc trên bên phải.

- Nếu không thấy thư mục nào ở phía bên trái, bạn có thể chọn **Open Folder**, sau đó chọn `mcserver` và truy cập thư mục `server` để xem hoặc chỉnh sửa nội dung bên trong.
- Nếu bạn đã thay đổi bất kỳ nội dung nào trong máy chủ, hãy khởi động lại máy chủ.

Sau khi khởi động lại, các thay đổi của bạn sẽ được áp dụng và lưu lại.

## Thay đổi/Tùy chỉnh các biến

Nếu muốn thay đổi các biến trong script hoặc tinh chỉnh để máy chủ hoạt động theo ý muốn, bạn có thể chỉnh sửa các biến tương ứng.

- Để thực hiện, hãy mở một trong hai thư mục `/JavaInstallScripts` hoặc `/BedrockInstallScripts` trong **Cloud Shell Editor**.

Các máy chủ `Java` sau đây hỗ trợ tùy chỉnh biến:

- **Fabric**
- **Forge**
- **NeoForge**
- **Paper**
- **Vanilla**

### Cách hoạt động của launcher máy chủ Java

`startJavaServer` tự động sử dụng launcher được tạo ra tương ứng với từng loại máy chủ:

- Fabric: `fabric-server-launch.jar`
- Forge / NeoForge phiên bản hiện đại: `server/run.sh`
- Vanilla / Paper / Spigot / Sponge / BungeeCord / Forge phiên bản cũ: `server.jar`

Đối với Forge và NeoForge phiên bản hiện đại, hãy chỉnh sửa `server/user_jvm_args.txt` để thay đổi bộ nhớ hoặc các tùy chọn JVM. Các tệp `run.sh` và `libraries/.../unix_args.txt` được tạo tự động sẽ được giữ nguyên, không chỉnh sửa.

Các máy chủ `Bedrock` sau đây hỗ trợ tùy chỉnh biến:

- **Nukkit**
- **PocketmineMP**
- **Vanilla**

Các máy chủ sau đây **không** hỗ trợ tùy chỉnh biến:

- Sponge `Java` *(loại máy chủ này đã quá cũ và chỉ hỗ trợ tải xuống trực tiếp)*.
- GoMint `Bedrock` *(loại máy chủ này không cần cấu hình biến)*.

## Phiên bản cũ

Bạn có thể mở các script của máy chủ và **CHỈ** chỉnh sửa phần mã sau:

```bash
# -- EDIT HERE | DO NOT EDIT ABOVE -- #
EXAMPLE_VARIBALES=VARIABLES # NOTE ABOUT VARIABLES
# -- EDIT HERE | DO NOT EDIT BELOW -- #
```

*(Lưu ý: Không chỉnh sửa phần mã bên trên hoặc bên dưới khu vực này. Nếu làm vậy, quá trình cài đặt có thể bị lỗi và bạn sẽ phải xóa dự án rồi cài đặt lại.)*

## Khởi động lại máy chủ

Nếu bạn chưa biết cách khởi động lại máy chủ, hãy làm theo các bước sau:

- Truy cập thư mục `mcserver` hoặc `../mcserver/`, sau đó chạy lệnh dưới đây.
- Dừng máy chủ. Thao tác này sẽ dừng cả Minecraft Server và hệ thống tunnel của Playit.gg:

```bash
./stopserver
```

- Sau đó khởi động máy chủ lại:

```bash
./startserver
```

- Hoặc bạn có thể sử dụng lệnh:

```bash
./restartserver
```

Vậy là máy chủ đã được khởi động lại hoàn tất.

## Giữ máy chủ hoạt động 24/7

Hiện tại, chỉ có **MỘT** cách để giữ máy chủ trực tuyến lâu hơn 20 phút:

- Bạn phải giữ trình duyệt mở để máy chủ tiếp tục hoạt động. Việc này giúp Cloud Shell không bị kết thúc khi không được sử dụng hoặc khi trình duyệt bị đóng.

*(Đừng lo, thiết bị bạn dùng để host máy chủ sẽ không bị ảnh hưởng bởi mức tải của máy chủ.)*

Nếu bạn biết cách nào có thể giúp máy chủ hoạt động 24/7, hãy thoải mái **Fork** dự án này và gửi **Pull Request**. Mọi sự đóng góp đều rất được hoan nghênh.

## Những hạn chế của dự án

### Giới hạn sử dụng Google Cloud Shell

Trong quá trình phát triển dự án, tôi nhận thấy Google đã áp dụng hạn mức sử dụng cho mỗi tài khoản Cloud Shell. Bạn chỉ có thể host máy chủ tối đa `50` giờ mỗi tuần.

Sau khi sử dụng hết số giờ này, bạn sẽ không thể tiếp tục sử dụng cho đến tuần tiếp theo.

### Không có IP chuyên dụng riêng

Đáng tiếc là bạn không thể sử dụng IP host làm IP chuyên dụng để kết nối vào máy chủ, vì Minecraft sẽ không cho phép bạn tham gia theo cách đó. Bạn chỉ có thể kết nối vào máy chủ bằng IP chuyên dụng được **playit.gg** tạo ra.

Nếu biết cách reverse proxy hệ thống tunnel, bạn *có thể* sử dụng IP host để tạo IP chuyên dụng cho máy chủ, nhưng khả năng thực hiện được điều đó là khá thấp.

### Cấu hình máy chủ không đồng nhất

Mỗi phiên Cloud Shell có thể được cấp cấu hình phần cứng khác nhau tùy theo vị trí địa lý thực tế của bạn. Vì vậy, hiệu năng máy chủ không phải lúc nào cũng tốt nhất.

Tuy nhiên, tin tốt là RAM luôn nằm trong khoảng `8GB` đến `16GB`, do đó bạn không cần quá lo lắng về tình trạng giật lag khi chơi trên máy chủ có mức xử lý cao.

## Máy chủ AFK

Trong khi máy chủ đang chạy, bạn có thể nhập lệnh:

```bash
./startafk
```

Lệnh này sẽ chạy script AFK, giúp terminal luôn duy trì kết nối.

*Lưu ý: Bạn cũng không được đóng tab dashboard nếu không muốn máy chủ bị tắt!*

## Gỡ cài đặt/Xóa máy chủ

- Nếu muốn tạo máy chủ mới hoặc xóa máy chủ hiện tại, hãy chạy lệnh sau bên trong thư mục `~/mcserver`:

```bash
./uninstall
```

Script sẽ hỏi bạn có thực sự muốn gỡ cài đặt hay không.

- Thao tác này sẽ xóa toàn bộ thư mục máy chủ. Sau đó, bạn có thể tạo lại máy chủ bằng lệnh `./install`.

## Xóa/Cập nhật toàn bộ dự án

Dự án sẽ liên tục được cập nhật từng ngày cho đến khi tôi hoàn thiện nó. Nếu bạn đã cài đặt dự án trước đó và phiên bản hiện tại còn thiếu một số tính năng, bạn có thể cập nhật dự án theo các bước sau.

- Đầu tiên, quay về thư mục mặc định:

```bash
cd
```

- Bây giờ hãy xóa toàn bộ dự án. *(Hãy cẩn thận: SAO LƯU/TẢI XUỐNG thư mục world của bạn TRƯỚC KHI xóa. Bạn sẽ không thể khôi phục lại sau khi chạy lệnh này.)*

```bash
sudo rm -r mchost
```

Sau khi dự án được xóa hoàn toàn, bạn có thể [Clone lại dự án](https://github.com/kleqing/mchost/blob/main/README.md#installation). Khi đó, bạn sẽ có phiên bản mới nhất cùng các tính năng và mã nguồn mới được cập nhật!

## Kết luận

Vậy là bạn đã có thể tự host máy chủ Minecraft Java và Bedrock của riêng mình một cách nhanh chóng, dễ dàng mà không tốn bất kỳ chi phí nào để có một máy chủ mạnh và ổn định. Tuyệt vời hơn cả, dịch vụ này là **MIỄN PHÍ MÃI MÃI**!

Nếu có yêu cầu về tính năng muốn bổ sung vào dự án, bạn cứ thoải mái đóng góp. Nếu gặp bất kỳ vấn đề nào, hãy truy cập mục [**Issues**](https://github.com/kleqing/mchost/issues) và gửi issue tại đó.

## Ghi công

- Công trình gốc thuộc về: *[LordOfWizard](https://github.com/lordofwizard)*
