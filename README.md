# Khung ảnh kỷ niệm 20 năm – THPT Tam Dương II (2006 – 2026)

Trang web tĩnh (HTML/CSS/JS thuần) tạo khung avatar kỷ niệm 20 năm thành lập trường.
**Không cần cài đặt anything** — không Node.js, không build. Chỉ gồm 3 file:

| File | Vai trò |
|---|---|
| `index.html` | Toàn bộ trang web (giao diện + cắt ảnh + ghép khung) |
| `khung.png` | Khung kỷ nhiệm (được ghép lên trên cùng của ảnh) |
| `.nojekyll` | Bắt buộc để GitHub Pages phục vụ đúng mọi file |

Ảnh của người dùng được xử lý 100% ngay trên thiết bị — không gửi lên bất kỳ máy chủ nào.

---

## Đưa trang lên GitHub Pages (miễn phí)

### Cách 1 — Tải lên bằng trình duyệt (không cần biết lệnh)

1. Tạo tài khoản GitHub (nếu chưa có) tại https://github.com/signup
2. Nhấn dấu **`+`** góc phải trên → **New repository**
   - Repository name: ví dụ `khung-20-nam` (tùy ý)
   - Chọn **Public** (bắt buộc để dùng Pages miễn phí)
   - Nhấn **Create repository**
3. Trong trang repo mới, nhấn **uploading an existing file** (hoặc Add file → Upload files)
4. Kéo thả **3 file** (`index.html`, `khung.png`, `.nojekyll`) vào → nhấn **Commit changes**
5. Bật Pages: vào **Settings** → mục **Pages** (trái) →
   - Source: **Deploy from a branch**
   - Branch: chọn **main** / thư mục **/(root)** → **Save**
6. Chờ 1–2 phút, refresh trang Settings → Pages sẽ hiện địa chỉ dạng:

   ```
   https://<tên-github-của-bạn>.github.io/khung-20-nam/
   ```

7. Gửi link này cho thầy cô và học sinh — mở bằng điện thoại là dùng được ngay.

### Cách 2 — Dùng Git (nếu quen lệnh)

```bash
git clone https://github.com/<tài-khoản>/khung-20-nam.git
cd khung-20-nam
# copy 3 file vào thư mục này rồi:
git add .
git commit -m "Thêm trang khung kỷ niệm 20 năm"
git push origin main
# Sau đó bật Pages như bước 5 ở trên
```

> Lưu ý: đây là trang tĩnh, mọi đường dẫn đều **tương đối** (`khung.png`), nên đặt ở repo con
> (`username.github.io/khung-20-nam/`) hay trang riêng (`username.github.io`) đều chạy bình thường.

---

## Thay khung khác (không cần sửa code)

1. Chuẩn bị khung mới: ảnh **PNG** vuông (1080×1080), giữa trong suốt để lộ ảnh đại diện
2. Đổi tên thành `khung.png`, upload đè lên file cũ trong repo (Add file → Upload files → chọn file → Commit)
3. Xong — trang tự dùng khung mới sau khi refresh

Kích thước lỗ tròn hiện được tính theo khung hiện tại: **R ≈ 461/1080** (vành khung ngoài ≈ 512/1080).
Nếu khung mới có lỗ to/nhỏ hơn đáng kể, hãy nhờ điều chỉnh 2 hằng số `AVATAR_R` / `RIM_START` trong `index.html`.

---

## Chạy thử trên máy (tùy chọn)

Mở trực tiếp `index.html` bằng double-click có thể xem giao diện, nhưng một số trình duyệt
chặn việc xuất ảnh vì chính sách bảo mật (file://). Để chạy đủ tính năng:

```bash
# trong thư mục chứa index.html
python3 -m http.server 8080
# mở http://localhost:8080
```

---

## Tính năng

- 📱 Ưu tiên điện thoại: kéo ảnh bằng ngón tay, **ghim 2 ngón để thu phóng**, thanh trượt + nút xoay ±90°
- ✂️ Cắt ảnh vuông 1:1 với vòng tròn hướng dẫn đúng vùng sẽ hiển thị
- 🖼️ Hiệu ứng 2 lớp blur: nền blur mạnh bên ngoài + blur tròn mềm dần quanh trung tâm, ảnh gốc sắc nét ở giữa
- 🧩 Ghép `khung.png` lên trên cùng, xuất ảnh JPEG 1080×1080 (~150–300KB) — nhẹ, gửi Zalo/Facebook nhanh
- 🔒 Ảnh không rời khỏi thiết bị người dùng
