# ViệtGem Network — Website tĩnh

## 🚀 Deploy

Vì mỗi trang là một folder chứa `index.html` (`/rules/index.html`, `/staffs/index.html`...), các nền tảng hosting tĩnh dưới đây tự nhận diện và phục vụ đúng URL sạch (`/rules/`, `/staffs/`...) mà **không cần cấu hình thêm**:

- **GitHub Pages**: push toàn bộ thư mục lên nhánh (ví dụ `main`), bật Pages trong Settings → Pages, chọn nhánh + thư mục gốc. Xong.
- **Netlify**: kéo-thả cả thư mục vào Netlify Drop, hoặc kết nối repo Git — không cần build command, publish directory để `/` (gốc).
- **Vercel**: import repo, Framework Preset chọn "Other", không cần build command.
- **Cloudflare Pages**: tương tự Netlify — không có bước build, output directory là gốc dự án.

## 💻 Chạy thử ở máy local

**Không mở trực tiếp `index.html` bằng cách double-click** (giao thức `file://`) — khi đó `/rules/`, `/staffs/`... sẽ không hoạt động vì trình duyệt không tự động tìm `index.html` trong folder.

Cách đúng — dùng một server local đơn giản:

```bash
# Cách 1: Python (đã có sẵn trên hầu hết máy)
python -m http.server 8000
# rồi mở http://localhost:8000/

# Cách 2: VS Code — cài extension "Live Server", bấm "Go Live"
```

## ⚙️ Các chỉnh sửa thường gặp

**Đổi IP server:**
Mở `/js/main.js`, sửa dòng đầu tiên:
```js
const SERVER_IP = "viegem.net";
```

**Thêm cụm mới (ví dụ "SkyBlock"):**
1. Tạo folder mới: `/skyblock/index.html` (copy từ `/magirpg/index.html` và sửa nội dung).
2. Vào `/index.html`, copy khối `<a class="cluster-card">...</a>` trong phần "Các cụm hiện có", đổi link, ảnh, tên, mô tả.
3. Thêm link cụm mới vào `<nav class="main-nav">` ở mọi trang nếu muốn hiện trên menu chính.
4. (Tuỳ chọn) Thêm mục luật riêng cho cụm mới trong `/rules/index.html` (copy khối `.rules-box`).

**Thêm staff mới:**
Mở `/js/staffs.js`, thêm 1 object vào mảng `STAFF_LIST`:
```js
{ ign: "TenIngame", discordId: "id_discord_18_so", role: "Moderator" }
```

**Thêm mục wiki mới:**
Mở `/wiki/index.html`:
1. Copy 1 khối `<div class="wiki-card" id="...">...</div>`, đổi `id`, tiêu đề, nội dung.
2. Thêm 1 dòng `<li><a href="#id-moi">Tên mục</a></li>` vào phần `<nav class="wiki-toc">` bên trái.

## 📁 Cấu trúc thư mục

```
/index.html
/rules/index.html
/staffs/index.html
/wiki/index.html
/magirpg/index.html
/css/style.css
/js/main.js       — header scroll, hamburger menu, copy IP, mở game, fade-in
/js/status.js     — trạng thái server real-time (trang chủ)
/js/staffs.js     — dữ liệu & hiển thị staff
```
