# TuansA (Android APK)

Ứng dụng bán hàng/gọi món buffet bằng tiếng Việt, màn hình dọc, nền xanh biển. Luồng chính:

- Chọn khu/bàn (Khu A: 1–7, Khu B: 8–15, Khu C: 16–20)
- Nhập số lượng khách (tự bật bàn phím số)
- Chọn món không giới hạn + ghi chú đơn
- Thanh toán & in bill (in Bếp + in Quầy thu ngân) qua máy in nhiệt WiFi/LAN bằng IP

## Yêu cầu để build APK

- Android Studio (khuyến nghị bản Stable)
- Android SDK đã cài (Android Studio sẽ tự cài)
- JDK 17 (Android Studio thường kèm sẵn; nếu dùng command line thì cài JDK 17)

## Build APK (Debug)

Mở thư mục dự án bằng Android Studio và chạy:

- Build > Build Bundle(s) / APK(s) > Build APK(s)

Hoặc dùng command line (khi máy đã cài Android SDK và cấu hình đúng):

```bash
gradle :app:assembleDebug
```

APK debug sẽ nằm trong:

```
app/build/outputs/apk/debug/app-debug.apk
```

## Build APK bằng GitHub trên điện thoại

Nếu bạn đang dùng điện thoại, có thể build APK bằng GitHub Actions:

1. Tải file `TuansA.zip` về điện thoại.
2. Dùng ứng dụng giải nén như `ZArchiver`, `RAR` hoặc ứng dụng Tệp để giải nén.
3. Tạo 1 repository mới trên GitHub.
4. Upload toàn bộ nội dung đã giải nén của dự án lên repository đó.
5. Mở tab `Actions` trên GitHub.
6. Chạy workflow `Build TuansA APK`.
7. Sau khi chạy xong, vào workflow run đó và tải artifact `TuansA-debug-apk`.

File APK sẽ có tên:

```text
app-debug.apk
```

Lưu ý:

- Workflow đã nằm sẵn tại `.github/workflows/build-apk.yml`
- GitHub sẽ tự cài JDK 17, Android SDK và build APK debug
- Nếu repo của bạn dùng nhánh `main` hoặc `master`, workflow sẽ tự nhận

## Cấu hình máy in

Vào **Quản lý > Máy in**:

- Thêm 1 máy in **Bếp** và 1 máy in **Quầy**
- Nhập IP + Port (mặc định 9100)
- Nếu máy in không hỗ trợ tiếng Việt có dấu, bật **Bỏ dấu khi in**
- Dùng nút **In thử** để kiểm tra kết nối

## In bill 80mm

Bill in ra gồm:

- Tên bàn (khu + số bàn)
- Thời gian tạo đơn
- Số khách
- Số lượng món (tổng phần + số loại)
- Ghi chú đơn hàng (nếu có)
- Danh sách món, tách từng món bằng đường kẻ để dễ đọc
