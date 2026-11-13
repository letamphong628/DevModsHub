# MIỄN TRỪ TRÁCH NHIỆM (DISCLAIMER)

Tài liệu này áp dụng cho toàn bộ mã nguồn, tệp đóng gói bảo vệ (`DevModsHub.js`, `DevModsHub.protected.js`), công cụ đi kèm (`protect_plugin.js`) và tài liệu hướng dẫn thuộc dự án **DevModsHub**. Bằng việc cài đặt, kích hoạt hoặc phân phối plugin này trong dự án RPG Maker MV/MZ của bạn, bạn xác nhận đã đọc, hiểu và đồng ý với các điều khoản dưới đây.

---

## 1. Phạm Vi & Mục Đích Sử Dụng
- **DevModsHub** được thiết kế như một công cụ hỗ trợ **phát triển (Development), gỡ lỗi (Debugging), chẩn đoán (Diagnostics)** và **tùy biến hiển thị/tiện ích hệ thống** cho các trò chơi xây dựng bằng RPG Maker MV và RPG Maker MZ.
- Tác giả không khuyến khích sử dụng **Developers Mode** hoặc **Error Sandbox** như một công cụ can thiệp trái phép vào sản phẩm thương mại của bên thứ ba.

## 2. Trách Nhiệm Về Dữ Liệu & File Save
- **Xóa Toàn Bộ Data Game:** Nút xóa dữ liệu trong mục *Configurations* (dù đã có cơ chế xác nhận 2 bước chống bấm nhầm) sẽ xóa vĩnh viễn tệp save cục bộ (`save/` trên NW.js hoặc `localStorage` trên trình duyệt). Dữ liệu đã xóa **không thể khôi phục** nếu bạn không có bản sao lưu trước đó.
- **Khớp Toàn Màn Hình & Độ Ổn Định Giao Diện:** Khi bật chế độ *Khớp Toàn Màn Hình (Vẫn ở Window)* và khởi động lại game (Reboot), `DevModsHub` sẽ tự động điều chỉnh kích thước canvas và áp dụng `HDLayout` động. Với các dự án sử dụng plugin UI/HUD bên thứ ba có tọa độ vẽ cố định cứng (hard-coded pixels), hiển thị có thể khác với thiết kế gốc; bạn có thể tắt chế độ này và Reboot lại bất kỳ lúc nào để quay về kích thước chuẩn của engine.
- **Error Sandbox:** Cơ chế cô lập lỗi giúp ngăn game crash đột ngột khi gặp ngoại lệ JavaScript từ plugin khác, nhưng **không tự động sửa logic bị sai** bên trong plugin gốc đó. Việc tiếp tục chơi và lưu save sau khi một plugin lõi gặp lỗi có thể dẫn tới trạng thái save không nhất quán.
- Hãy luôn **sao lưu (Backup)** thư mục dự án (`js/`, `data/`, `save/`) định kỳ trước khi thử nghiệm thay đổi cấu hình mới.

## 3. Giới Hạn Trách Nhiệm (Cung Cấp Theo Nguyên Trạng "AS-IS")
- Phần mềm được cung cấp theo nguyên trạng (**"AS-IS"**), không kèm theo bất kỳ bảo đảm rõ ràng hay ngụ ý nào về khả năng tương thích tuyệt đối với mọi bộ plugin bên thứ ba, mọi phiên bản NW.js, mọi độ phân giải màn hình hoặc mọi hệ điều hành.
- Trong mọi trường hợp, tác giả **không chịu trách nhiệm** đối với bất kỳ thiệt hại trực tiếp, gián tiếp, ngẫu nhiên hay hệ quả nào phát sinh từ việc sử dụng hoặc không thể sử dụng plugin này — bao gồm nhưng không giới hạn ở: mất dữ liệu, hỏng file save, sập ứng dụng, gián đoạn tiến trình phát triển game, hoặc sự cố tương thích với các plugin khác.

## 4. Trách Nhiệm Bảo Mật Khi Phát Hành Game (Release Build)
- Khi phát hành game chính thức tới người chơi, nhà phát triển/chủ dự án tự chịu trách nhiệm rà soát cấu hình trong **Plugin Manager**:
  - Đặt `EnableDeveloperMode` về `false` nếu không muốn người chơi mở Console chỉnh sửa chỉ số/map/vật phẩm.
  - Thay đổi **Mã PIN mặc định** (`DefaultPin`) hoặc bật `RequirePin = true` trước khi đóng gói phát hành.
- Cơ chế mã hóa và chữ ký trong `DevModsHub.protected.js` và Secure Vault nhằm hạn chế việc chỉnh sửa cấu hình/PIN thông thường bằng trình soạn thảo văn bản; đây không phải là giải pháp DRM tuyệt đối trước các công cụ dịch ngược chuyên sâu.

---

*Nếu bạn không đồng ý với bất kỳ điều khoản nào nêu trên, vui lòng tắt và gỡ bỏ `DevModsHub` khỏi Plugin Manager của dự án trước khi tiếp tục sử dụng hoặc phát hành.*
