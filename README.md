# Super OK

<img src="https://avatars.githubusercontent.com/u/250842655?s=400&u=0b819e954badf8daf36d926e58c27faafaaac9aa&v=4" alt="logo" width="100"/>

![The app screenshot](./images/browse_home.png)

**Super OK** là ứng dụng media client mã nguồn mở dành cho **Android TV / TV Box** và **Điện thoại / Máy tính bảng** (Android 5.0+). Ứng dụng gộp nhiều kho nội dung vào một giao diện duy nhất:

- 🔴 **YouTube** (nền tảng SmartTube)
- 📺 **Truyền hình IPTV** (M3U + EPG)
- 🎬 **Phim / VOD** (hệ thống plugin JS đa nguồn)
- 📹 **Dailymotion**
- 📂 **Video trong máy**

## Tính năng nổi bật

### 🎨 Giao diện kép (TV & Mobile)
- Lần đầu mở app có thể chọn **Giao diện TV** (tối ưu D-Pad / remote) hoặc **Giao diện Điện thoại** (6 tab icon ở đáy màn hình, tối ưu cảm ứng).
- Có thể chuyển đổi bất kỳ lúc nào trong **Cài đặt → Chế độ giao diện**.
- Hỗ trợ Android 5.0 (API 21) trở lên, kể cả thiết bị không có Google Services.

### 🔴 YouTube / SmartTube
- Giao diện sạch, không quảng cáo
- SponsorBlock (tự động bỏ qua đoạn quảng cáo, intro, outro...)
- Hỗ trợ 8K, 60fps, HDR (tùy phần cứng)
- Chỉnh tốc độ phát, chọn codec (AV01 / VP9 / AVC)
- Xem live chat, đăng nhập tài khoản, xem lịch sử & đăng ký kênh
- Chuyển tiếp (cast) từ điện thoại qua mã kết nối

### 📺 IPTV
- Hỗ trợ nhiều nguồn M3U (URL trực tuyến hoặc file cục bộ), chuyển nguồn nhanh bằng một chạm
- Lịch phát sóng **EPG** (mặc định: lichphatsong.io.vn)
- Nhóm kênh: Tất cả, Yêu thích, VTV & Quốc gia, Thể thao, Giải trí, Tin tức, Thiếu nhi, Quốc tế, Catchup
- Đánh dấu kênh yêu thích, ẩn kênh, xem lại Catchup
- Trình phát chuyên sâu: chỉnh tốc độ (0.25x–2.0x), tua nhanh lặp (2x→64x) bằng cách giữ nút Trái/Phải trên remote

### 🎬 Phim / VOD
- Hệ thống **plugin JS** (Rhino engine) — thêm nguồn phim không cần cập nhật app
- Đa nguồn phổ biến: OPhim, KKPhim, Nguonc, Motchill, AnimeHay, BiluTV...
- Tìm kiếm **đa nguồn cùng lúc**, lọc theo thể loại / quốc gia / năm / sắp xếp
- Chi tiết phim: điểm đánh giá, đạo diễn, diễn viên, tóm tắt, phim liên quan
- Nhiều server & tập phim, chuyển server/tập nhanh
- Hero banner, phân trang tự động (infinite scroll)

### 📂 Khác
- **Dailymotion**: xem & tìm kiếm video
- **Video trong máy**: quét MediaStore (bộ nhớ trong / thẻ nhớ), phát bằng ExoPlayer
- Trình phát ExoPlayer với cử chỉ vuốt (độ sáng / âm lượng / tua), PiP, phát âm thanh nền

## Thiết bị tương thích

- ✅ **Hỗ trợ:** Android TV, Google TV, Chromecast with Google TV, Amazon FireTV, NVIDIA Shield, TV box Android, điện thoại & máy tính bảng Android 5.0+
- ❌ **Không hỗ trợ:** Samsung Tizen, LG webOS, Apple TV, iOS — các nền tảng không phải Android

## Cài đặt

> ⚠️ Không tải Super OK từ cửa hàng ứng dụng hoặc trang web APK lạ — chỉ tải từ nguồn phát hành chính thức.

1. Tải file APK về điện thoại / máy tính.
2. Chuyển APK sang thiết bị TV bằng _Send Files to TV_, USB, hoặc cài qua ADB.
3. Bật **Cài đặt → Bảo mật → Nguồn không xác định** cho trình quản lý file.
4. Mở APK và cài đặt (nếu lỗi, kiểm tra dung lượng ổ đĩa trống).

**Cập nhật:** mở thủ công bản mới nhất và cài đè — dữ liệu (kênh yêu thích, tài khoản, cài đặt) được giữ nguyên.

## Build

**Lưu ý: cần OpenJDK 14 trở xuống.** JDK mới hơn có thể gây crash ứng dụng!

```
git clone <repo-url>.git
cd SuperOK
git submodule update --init
gradlew clean installStstableDebug
```

- Flavor `ststable` → tên app **Super OK** (package: `ok.super.stable`)
- Flavor `stbeta` → tên app **SmartTube beta** (package: `org.smarttube.beta`)
- Flavor `stfdroid` → bản F-Droid (package: `app.smarttube.fdroid`)
- ABI: `armeabi-v7a` + `arm64-v8a`, MultiDex bật, không minify (`minifyEnabled false`)

## FAQ

### Q: Videos bị buffering nhiều
A: Thử đổi DNS mã hóa (ví dụ NextDNS), giảm độ phân giải, hoặc chuyển codec sang AVC.

### Q: Phim không phân giải được dữ liệu ("Lỗi phân giải dữ liệu")
A: Nguồn phim có thể thay đổi cấu trúc trang. Thử đổi sang plugin/nguồn phim khác, hoặc cập nhật file plugin mới nhất.

### Q: Không phát được video do codec không hỗ trợ
A: Chọn codec **VP9** hoặc **AVC** thay vì AV01 (AV01 chỉ hoạt động trên thiết bị hỗ trợ phần cứng mới).

### Q: Có thể cài trên điện thoại không?
A: Có. Super OK hỗ trợ cả giao diện điện thoại (chọn lần đầu khi mở app, hoặc đổi trong Cài đặt).

### Q: Tôi có thể thêm nguồn phim / playlist của riêng mình không?
A: Có. Playlist IPTV: thêm URL M3U hoặc file cục bộ trong Cài đặt. Nguồn phim: thêm plugin JS vào thư mục plugin của app.

## Quyền riêng tư

Xem [PRIVACY.md](./PRIVACY.md) — bản F-Droid không chứa mã theo dõi, không telemetry, không cập nhật tự động.

## Giấy phép

Mã nguồn được phân phối theo giấy phép mã nguồn mở — xem [LICENSE](./LICENSE).
Super OK không chịu trách nhiệm về nội dung từ các dịch vụ bên thứ ba; hãy tuân thủ quy định pháp luật tại địa phương.
