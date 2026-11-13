# DevModsHub — RPG Maker MV/MZ Mods & Dev Hub Plugin

**Phiên bản:** `2.6.0` (Dual Engine: RPG Maker **MV** & **MZ**)  
**File chính:**
- `DevModsHub.protected.js` — Phiên bản mã hóa AES/XOR-Stream chống sửa tay cấu hình trực tiếp (Khuyên dùng trong dự án game).
- `DevModsHub.js` — Phiên bản mã nguồn gốc dành cho nhà phát triển tùy biến sâu.

---

## ✨ Tính Năng Nổi Bật

1. **Giao Diện macOS Card Có Hiệu Ứng Trượt (Slide Animation)**
   - Nút nổi `[⚙️ • Mods]` góc màn hình (hoặc phím tắt mặc định `F10`, hỗ trợ lệnh Plugin Command MZ `OpenModsHub` / `CloseModsHub` / `ToggleModsHub`).
   - Thanh điều hướng mượt, đóng mở bằng `ESC`, hỗ trợ **Song Ngữ (Tiếng Việt / English)**.

2. **Plugins — Cô Lập Lỗi An Toàn (Error Sandbox)**
   - Liệt kê toàn bộ danh sách plugin đang tải và trạng thái hoạt động.
   - Không cho phép tắt nóng plugin đang chạy giữa chừng để tránh crash dữ liệu save.
   - Tự động bắt ngoại lệ từ các plugin xung đột, đưa vào danh sách cô lập và hiển thị nguyên nhân.

3. **Configurations — Cài Đặt Hệ Thống & Hiển Thị**
   - **Khớp Toàn Màn Hình (Vẫn ở Window):** Công tắc bật/tắt chế độ tự động mở rộng cửa sổ + khung hình game khớp 100% vùng làm việc màn hình ngay khi khởi động, vẫn giữ nguyên thanh tiêu đề Windows & Taskbar (không khóa vào Fullscreen độc quyền).
     - ⚠️ **Yêu cầu Reboot Game:** Thay đổi công tắc sẽ lưu cài đặt vào `save/devmods_settings.json` / `localStorage` và hỏi bạn có muốn **Khởi Động Lại Game (Reboot)** ngay hay không.
     - Nếu bạn chọn **không Reboot ngay**, game sẽ **giữ nguyên độ phân giải hiện tại** và hiển thị thông báo chờ Reboot cùng nút **Khởi Động Lại Game Ngay** trong mục `Configurations`.
   - **Xóa Cache Dữ Liệu:** Dọn sạch bộ nhớ đệm hình ảnh (`ImageManager`), âm thanh và bitmap tạm khi được hướng dẫn hoặc khi lag.
   - **Xóa Toàn Bộ Data Game (2-Step Confirm):** Yêu cầu xác nhận 2 bước chống bấm nhầm trước khi xóa toàn bộ save và dữ liệu cục bộ.
   - **Xuất Logs (.txt):** Xuất toàn bộ thông số máy, danh sách plugin, trạng thái Fit Window Mode, nhật ký lỗi & stack trace ra file `.txt`.
   - **Bảo Mật Mã PIN (Secure Vault):** Mã PIN lưu trữ có mã hóa + chữ ký chống sửa tay. Khi đổi PIN bắt buộc nhập **Mã PIN Cũ** hợp lệ; khi mở khóa Dev Mode sẽ ẩn mã nhập dạng `••••`.
   - **Vị Trí Nút `[• Mods]`:** Tùy chỉnh 4 góc màn hình.

4. **Developers Mode — Console Cho Nhà Làm Game**
   - Khóa bằng Mã PIN bảo mật (có thể bật/tắt tính năng Developers Mode hoặc yêu cầu PIN ngay trong RPG Maker Plugin Manager).
   - Nhập `help` để xem toàn bộ lệnh: `maps`, `tele`, `hp`, `mp`, `atk`, `def`, `mat`, `mdf`, `agi`, `luk`, `level`, `gold`, `item`, `god`, `noclip`, `speed`, `save`, `clear`, `cls`, `lock`.
   - Lưu lịch sử lệnh bằng phím Mũi Tên Lên/Xuống.

5. **Chẩn Đoán (Checker)**
   - Tự động quét lỗi runtime trong quá trình chơi, kiểm tra file tài nguyên thiếu (ảnh/âm thanh), kèm **Dòng Chú Thích Nguyên Nhân** và **Khuyến Nghị Xử Lý** tiếng Việt/Anh rõ ràng.

6. **Guide & Versions**
   - Thông số engine đang chạy, hướng dẫn phím tắt, lịch sử cập nhật và mục **Miễn Trừ Trách Nhiệm** tích hợp sẵn ngay trong menu.

---

## 🛠️ Hướng Dẫn Cài Đặt Vào RPG Maker MV / MZ

1. Copy **`DevModsHub.protected.js`** (khuyến nghị) vào thư mục:
   ```text
   <Thư_Mục_Game>/js/plugins/DevModsHub.protected.js
   ```
   *(Nếu dùng bản nguồn mở để chỉnh sửa code, dùng `DevModsHub.js`; **chỉ bật 1 trong 2 file** trong Plugin Manager, không bật trùng cả hai).*
2. Mở RPG Maker MV/MZ → **Plugin Manager (F10)** → thêm `DevModsHub.protected`.
3. Chỉnh các tham số mặc định như:
   - `EnableDeveloperMode` (`true`/`false`): Bật hoặc tắt quyền dùng Console phát triển.
   - `RequirePin` & `DefaultPin`: Thiết lập bảo vệ mã PIN ban đầu.
   - `DefaultLanguage`: `vi` hoặc `en`.
   - `ToggleHotkey`: Mặc định `F10`.
   - `ShowFloatingButton` / `ButtonPosition`: Hiển thị & vị trí nút nổi.
   - `EnableErrorSandbox` / `EnableFpsCounter`: Sandbox bắt lỗi và bộ đếm FPS.

### Quy Trình Chống Sửa Tay Bằng File Mã Hóa
Khi chỉnh sửa `DevModsHub.js`, chạy lệnh sau trong thư mục mã nguồn để đóng gói lại bản bảo vệ:
```bash
node protect_plugin.js
```

---

## ⚙️ Chế Độ Khớp Toàn Màn Hình (Fit Fullscreen Windowed) Hoạt Động Như Thế Nào?

- **Bật ON → Chọn OK để Reboot:** Ở lần khởi động tiếp theo, game phóng to cửa sổ vừa khít vùng làm việc màn hình desktop (giữ nguyên viền Titlebar & Taskbar Windows) và khởi tạo `Graphics` / `Tilemap` / `Weather` / `HDLayout` khớp 100% khung nhìn, không bị viền đen hai bên và chuột bấm chuẩn pixel (`Pixel-Perfect`).
- **Bật ON / Tắt OFF → Chọn Cancel (Chưa Reboot):** Game giữ nguyên 100% độ phân giải đang chạy của phiên hiện tại. Bạn có thể Reboot bất cứ lúc nào từ nút cảnh báo trong `Configurations` hoặc tự tắt mở lại game.
- **Tắt OFF → Reboot:** Cửa sổ tự động khôi phục (`unmaximize`) về đúng kích thước mặc định của RPG Maker (`Screen Width × Screen Height` trong System).

---

## ⚖️ Miễn Trừ Trách Nhiệm (Disclaimer)

Vui lòng đọc kỹ bản đầy đủ tại **[MIEN_TRU_TRACH_NHIEM.md](./MIEN_TRU_TRACH_NHIEM.md)** trước khi sử dụng hoặc phân phối kèm dự án game. Tóm tắt ngắn gọn:

1. **Mục đích sử dụng:** `DevModsHub` là plugin hỗ trợ nhà phát triển kiểm thử, chẩn đoán lỗi và quản trị cấu hình trong RPG Maker MV/MZ.
2. **Dữ liệu & Save Game:** Tính năng **Xóa Toàn Bộ Data Game** sẽ xóa vĩnh viễn toàn bộ file save và cấu hình cục bộ trên máy/trình duyệt. Việc bật **Developers Mode**, **Error Sandbox** (bỏ qua lỗi plugin) hoặc thay đổi dữ liệu nhân vật/map trong Console có thể ảnh hưởng tiến trình game. Người dùng cần **tự sao lưu (backup)** save và dự án trước khi thao tác.
3. **Không chịu trách nhiệm thiệt hại:** Tác giả cung cấp plugin theo nguyên trạng (**AS-IS**) và không chịu trách nhiệm pháp lý hay bồi thường đối với mọi mất mát dữ liệu, hỏng file save, xung đột với plugin bên thứ ba khác hoặc việc người chơi/bên thứ ba lạm dụng công cụ nhà phát triển vào mục đích gian lận.
4. **Quyền phân phối:** Khi đưa game ra cộng đồng (Release build), nhà phát triển có trách nhiệm đặt lại `EnableDeveloperMode = false` hoặc đổi **Mã PIN** an toàn nếu không muốn người chơi truy cập Console Dev.
