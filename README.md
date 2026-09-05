# Sổ tay nhỏ — hướng dẫn biến app thành file cài đặt & dùng trên điện thoại

Project này đã được kiểm tra build thành công (bản Linux). Làm theo các bước dưới đây, anh sẽ có:

- Một file **setup thật (.exe)** để cài lên Windows, có icon riêng, chạy như app bình thường, không cần mở trình duyệt.
- Một bản có thể **"Cài đặt" ngay từ điện thoại/laptop khác** qua trình duyệt (giống app thật, có icon riêng ở màn hình chính, dùng được cả khi mất mạng).

Cả hai đều tự động, anh không cần cài công cụ lập trình gì trên máy.

## Bước 1 — Tạo tài khoản GitHub (nếu chưa có)

Vào https://github.com và đăng ký (miễn phí).

## Bước 2 — Tạo một repository mới

1. Bấm nút **"New repository"**.
2. Đặt tên bất kỳ, ví dụ `so-tay-nho`.
3. Chọn **Public** (bắt buộc để dùng GitHub Pages miễn phí).
4. Bấm **Create repository**.

## Bước 3 — Tải toàn bộ thư mục này lên repository đó

Cách dễ nhất, không cần dùng dòng lệnh:
1. Vào trang repository vừa tạo trên GitHub.
2. Bấm **"Add file" → "Upload files"**.
3. Kéo thả **toàn bộ nội dung bên trong thư mục `desktop-app`** (không kéo cả thư mục `desktop-app`, mà kéo các file/thư mục con bên trong nó: `www`, `build`, `.github`, `main.js`, `package.json`, `.gitignore`, `README.md`) vào ô tải lên.
4. Bấm **Commit changes**.

## Bước 4 — Lấy file cài đặt Windows (.exe)

Sau khi tải lên xong, GitHub sẽ **tự động build** (mất khoảng 3–5 phút):
1. Vào tab **Actions** trên repository.
2. Bấm vào lượt chạy **"Build Windows Installer"** mới nhất (có thể phải đợi nó chạy xong, biểu tượng chuyển sang dấu tích xanh ✅).
3. Kéo xuống mục **Artifacts**, bấm tải về **SoTayNho-Windows** (file .zip).
4. Giải nén ra sẽ thấy:
   - `So tay nho Setup 1.0.0.exe` → **đây là file cài đặt**, double-click để cài như phần mềm bình thường (có icon trái tim, tạo shortcut ngoài Desktop và Start Menu).
   - `So tay nho 1.0.0.exe` (bản portable) → chạy thẳng không cần cài, tiện để mang theo USB.

Mỗi lần anh sửa lại nội dung `www/index.html` và tải file mới lên GitHub, nó sẽ tự build lại bản .exe mới — không cần lặp lại các bước trên.

## Bước 5 — Dùng trên điện thoại / laptop khác (không cần cài .exe)

Cũng ngay sau bước 3, GitHub sẽ tự động đưa app lên mạng qua **GitHub Pages**:
1. Vào **Settings → Pages** trên repository.
2. Trong repository Settings → Actions → General, mục "Workflow permissions", chọn **"Read and write permissions"** rồi Save (chỉ cần làm 1 lần đầu).
3. Sau khi workflow "Deploy to GitHub Pages" chạy xong (xem ở tab Actions), Settings → Pages sẽ hiện đường link dạng:
   `https://ten-tai-khoan.github.io/so-tay-nho/`
4. Mở link đó bằng trình duyệt trên điện thoại (Chrome/Safari) hoặc laptop khác:
   - **Android (Chrome):** bấm menu (⋮) → **"Cài đặt ứng dụng"** / "Thêm vào Màn hình chính".
   - **iPhone (Safari):** bấm nút Chia sẻ (⬆️) → **"Thêm vào MH chính"**.
   - **Laptop (Chrome/Edge):** bấm biểu tượng "Cài đặt" ⊕ ở thanh địa chỉ.

Sau khi cài, app sẽ có icon trái tim riêng, mở lên full màn hình như app thật, không còn thanh địa chỉ trình duyệt, và **vẫn dùng được khi không có mạng** (dữ liệu vẫn lưu trên máy đó).

> Lưu ý: dữ liệu được lưu riêng trên từng máy/trình duyệt/app đã cài (không tự đồng bộ qua lại giữa điện thoại và laptop). Dùng chức năng **Sao lưu** trong app (xuất file .json) để chuyển dữ liệu giữa các máy khi cần.

## Muốn tự build trên máy mình (không bắt buộc)

Nếu có máy Windows/Mac riêng và muốn build thủ công thay vì chờ GitHub:
```
npm install
npm run dist
```
File cài đặt sẽ nằm trong thư mục `dist/`.
