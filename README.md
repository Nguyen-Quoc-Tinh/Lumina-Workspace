# Lumina Workspace

Ứng dụng desktop Windows mã nguồn mở giúp quản lý lịch làm việc, công việc và kho tài liệu cá nhân. Lumina Workspace chạy cục bộ, sử dụng SQLite và không yêu cầu máy chủ hoặc tài khoản trực tuyến.

> **Trạng thái:** phiên bản thử nghiệm `0.1.0`  
> **Nền tảng mục tiêu:** Windows 10/11 64-bit  
> **Lưu trữ:** cục bộ trên máy người dùng

## Tính năng

### Lịch làm việc

- Xem lịch theo tháng hoặc danh sách.
- Tạo, sửa và xóa lịch làm việc.
- Nhấn vào một ngày trong lịch tháng để tạo lịch ngay cho ngày đó.
- Chọn ngày bằng bộ chọn lịch của Windows.
- Thiết lập giờ, địa điểm, danh mục, mức độ ưu tiên và ghi chú.
- Hỗ trợ lịch lặp theo ngày, tuần, tháng hoặc năm.
- Thiết lập nhắc việc trước giờ bắt đầu.
- Tìm kiếm và lọc lịch theo danh mục.

### Quản lý công việc

- Tạo, sửa, hoàn thành và xóa công việc.
- Trạng thái: Chưa bắt đầu, Đang thực hiện, Tạm hoãn và Hoàn thành.
- Mức độ ưu tiên: Thấp, Trung bình, Cao và Khẩn cấp.
- Ngày bắt đầu, hạn chót và cảnh báo quá hạn.
- Checklist cho từng công việc.
- Chế độ xem danh sách và Kanban.

### Kho tài liệu

- Sao chép file vào kho tài liệu.
- Nhập toàn bộ thư mục và giữ nguyên cấu trúc thư mục con.
- Hiển thị file và thư mục con ngay trong thư mục cha.
- Tạo, xóa và di chuyển file/thư mục.
- Di chuyển file hoặc thư mục vào thư mục cấp cao nhất đã có trong kho.
- Tìm kiếm file và thư mục không phân biệt chữ hoa/thường.
- Hỗ trợ tìm kiếm tiếng Việt có dấu.
- Xem trước DOCX, XLSX, XLS, CSV, PDF, ảnh và file văn bản.
- Mở tài liệu bằng ứng dụng mặc định của Windows.
- Đổi tên hiển thị, yêu thích và phân loại tài liệu.
- Xóa file vào Thùng rác, khôi phục hoặc xóa vĩnh viễn.

Lumina hiện nhập file mới theo chế độ **sao chép vào kho**. File gốc bên ngoài vẫn được giữ nguyên.

### Tìm kiếm thông minh

- Tìm đồng thời tài liệu, thư mục, công việc và lịch.
- Không phân biệt chữ hoa/chữ thường.
- Hỗ trợ tìm kiếm tên tiếng Việt có dấu.
- Có thể mở nhanh bằng `Ctrl + K`.

### Sao lưu và khôi phục

- Sao lưu cơ sở dữ liệu và tài liệu thành file `.zip`.
- Khôi phục từ bản sao lưu.
- Sử dụng snapshot SQLite để giảm nguy cơ lỗi khi cơ sở dữ liệu đang được sử dụng.

### Theo dõi dung lượng

- Hiển thị dung lượng tài liệu đã dùng.
- Hiển thị dung lượng còn trống của ổ đĩa chứa workspace.
- Hiển thị tỷ lệ dung lượng kho tài liệu so với tổng dung lượng ổ đĩa.

## Công nghệ

- **Desktop:** Tauri 2
- **Backend:** Rust
- **Frontend:** React 19, TypeScript, Vite
- **Giao diện:** Tailwind CSS, Lucide React
- **Cơ sở dữ liệu:** SQLite bundled với Rusqlite
- **Quản lý trạng thái:** Zustand
- **Xem DOCX:** Mammoth
- **Xem và xuất bảng tính:** SheetJS
- **Đóng gói:** Tauri Bundler

## Yêu cầu hệ thống

### Khi sử dụng bộ cài

- Windows 10 hoặc Windows 11 64-bit.
- Không cần cài Node.js, Rust, VS Code hoặc SQLite.
- Cần đủ dung lượng trên ổ đĩa dùng để lưu workspace và tài liệu.

### Khi chạy mã nguồn

- Windows 10/11.
- Node.js 20 trở lên.
- Rust stable và Cargo.
- npm.

## Cài đặt từ bộ cài Windows

Sau khi build, bộ cài NSIS nằm tại:

```text
src-tauri/target/release/bundle/nsis/Lumina Workspace_0.1.0_x64-setup.exe
```

Người dùng chỉ cần:

1. Tải file `Lumina Workspace_0.1.0_x64-setup.exe`.
2. Nhấp đúp vào file.
3. Chọn `Yes` nếu Windows hỏi quyền cài đặt.
4. Làm theo hướng dẫn trên màn hình.

Nếu muốn chuyển cả dữ liệu hiện có sang máy khác, cần sao chép thêm toàn bộ thư mục `LuminaWorkspace`. Chỉ gửi bộ cài sẽ tạo một workspace mới trên máy nhận.

## Chạy dự án ở chế độ phát triển

Tải mã nguồn và cài dependencies:

```bash
git clone <URL_REPOSITORY>
cd "NEW PRJ"
npm install
```

Chạy ứng dụng Tauri ở chế độ phát triển:

```bash
npm run tauri -- dev
```

Chỉ chạy frontend bằng Vite:

```bash
npm run dev
```

## Kiểm tra và build

Kiểm tra TypeScript và build frontend:

```bash
npm run build
```

Kiểm tra Rust:

```bash
cd src-tauri
cargo check
cd ..
```

Đóng gói ứng dụng Windows:

```bash
npm run tauri -- build
```

Các file đầu ra thường nằm tại:

```text
src-tauri/target/release/tauri-app.exe
src-tauri/target/release/bundle/nsis/Lumina Workspace_0.1.0_x64-setup.exe
src-tauri/target/release/bundle/msi/Lumina Workspace_0.1.0_x64_en-US.msi
```

### Nên gửi file nào cho người dùng?

Nên gửi:

```text
Lumina Workspace_0.1.0_x64-setup.exe
```

Đây là bộ cài đầy đủ. Không nên gửi riêng `tauri-app.exe` cho người dùng phổ thông vì đó chỉ là file chạy trực tiếp, không phải bộ cài.

## Vị trí dữ liệu

Lumina ưu tiên dùng ổ D nếu ổ D tồn tại:

```text
D:\LuminaWorkspace
```

Nếu không có ổ D, ứng dụng dùng:

```text
C:\Users\<Tên người dùng>\Documents\LuminaWorkspace
```

Cấu trúc chính:

```text
LuminaWorkspace/
├── Database/
│   └── lumina.db
├── Documents/
│   └── Tài liệu được sao chép vào kho
└── Backups/
    └── Các file sao lưu .zip
```

### Lưu ý về xóa tài liệu

- Xóa file riêng lẻ trong Kho tài liệu sẽ chuyển file vào Thùng rác.
- Xóa vĩnh viễn hoặc dọn Thùng rác mới xóa file vật lý tương ứng.
- Xóa thư mục với tùy chọn xóa nội dung sẽ xóa vật lý thư mục và các file được sao chép vào kho.
- File gốc bên ngoài kho không bị xóa khi nhập theo chế độ sao chép.

## Đóng góp

1. Fork repository.
2. Tạo branch mới:

   ```bash
   git checkout -b feature/ten-tinh-nang
   ```

3. Cài dependencies và chạy kiểm tra:

   ```bash
   npm run build
   cd src-tauri
   cargo check
   ```

4. Commit thay đổi và tạo Pull Request.

Vui lòng mô tả rõ thay đổi, cách kiểm thử và ảnh chụp màn hình nếu có thay đổi giao diện.

## Bản quyền

Xem thông tin bản quyền và giấy phép trong repository. Nếu dự án chưa có file giấy phép riêng, hãy bổ sung `LICENSE` trước khi phát hành công khai.
