# 🎆 Happy New Year - Pháo Hoa

Trang web hiệu ứng pháo hoa chúc mừng năm mới, sẵn sàng deploy lên **GitHub Pages**.

---

## 🚀 Deploy lên GitHub Pages

### Bước 1: Tạo Repository trên GitHub
1. Vào [github.com/new](https://github.com/new)
2. Đặt tên repo (ví dụ: `happy-new-year`)
3. Chọn **Public** → Nhấn **Create repository**

### Bước 2: Push code lên GitHub
Mở terminal trong thư mục `happy-new-year` và chạy:
```bash
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/TEN-USERNAME/happy-new-year.git
git push -u origin main
```
> ⚠️ Thay `TEN-USERNAME` bằng username GitHub của bạn.

### Bước 3: Bật GitHub Pages
1. Vào **Settings** → **Pages**
2. Source: chọn **Deploy from a branch**
3. Branch: chọn **main** → folder **(root)** → **Save**
4. Đợi 1-2 phút, trang web sẽ có tại: `https://TEN-USERNAME.github.io/happy-new-year/`

---

## ✏️ Hướng dẫn tùy chỉnh

### 1. Đổi tiêu đề trang
📄 **File:** `index.html` — **Dòng 5**
```html
<title>Happy New Year 2026</title>
```
→ Đổi thành tên bạn muốn, ví dụ: `<title>Chúc Mừng Năm Mới - Tùng</title>`

---

### 2. Thay đổi lời chúc bay trên màn hình
📄 **File:** `js/script.js` — **Dòng ~552**

Tìm đoạn `WISH_MESSAGES`:
```javascript
let WISH_MESSAGES = [
    "Năm mới an khang thịnh vượng",
    "Năm mới bình an",
    "Chúc mọi điều ước của em đều trở thành hiện thực ✨",
    "Chúc gia đình em luôn bình an và hạnh phúc ❤️",
    "Chúc em luôn khỏe mạnh và tràn đầy năng lượng 💪",
    "Chúc công việc thuận lợi, thăng tiến không ngừng 🚀",
    "Chúc em luôn mỉm cười và yêu đời mỗi ngày 😊",
    "Chúc em gặp nhiều may mắn và niềm vui 🎉",
];
```
→ **Sửa, thêm, hoặc xóa** các câu chúc tùy ý. Mỗi câu nằm trong dấu `""` và kết thúc bằng dấu `,`

---

### 3. Thay đổi ảnh hiển thị trong pháo hoa
📄 **File:** `js/script.js` — **Dòng ~73**

Tìm đoạn `imageSources`:
```javascript
let imageSources = [
    "./images/image1.jpeg",
    "./images/image2.jpeg",
    "./images/image3.jpeg",
    "./images/image4.jpeg",
    "./images/image5.jpeg",
];
```

**Cách thay ảnh:**
1. Chuẩn bị ảnh của bạn (JPEG hoặc PNG)
2. Đặt ảnh vào thư mục `images/` (ghi đè hoặc thêm mới)
3. Cập nhật danh sách trong code cho khớp tên file

**Ví dụ** thêm ảnh mới:
```javascript
let imageSources = [
    "./images/anh-gia-dinh.jpg",
    "./images/anh-ban-be.jpg",
    "./images/anh-couple.png",
];
```

> 💡 **Lưu ý:** Ảnh nên có kích thước vừa phải (~500KB trở xuống) để load nhanh.

---

### 4. Thay đổi nhạc nền
📄 **File:** `js/script.js` — **Dòng ~3529**

Tìm đoạn:
```javascript
this.audio = new Audio('./audio/321_join.mp3');
```
→ Thay `321_join.mp3` bằng file nhạc của bạn (đặt trong thư mục `audio/`)

---

### 5. Đổi favicon (icon tab trình duyệt)
Thay file `images/favicon.png` bằng ảnh icon của bạn (khuyến nghị 64x64 hoặc 128x128 px).

---

### 6. Đổi nút Start
📄 **File:** `index.html` — **Dòng 545**
```html
<button class="start-button" id="startButton">START</button>
```
→ Đổi chữ `START` thành gì bạn muốn, ví dụ: `BẮT ĐẦU` hay `MỞ QUÀ 🎁`

---

## 📁 Cấu trúc thư mục

```
happy-new-year/
├── index.html          ← Trang chính (sửa tiêu đề, nút Start)
├── ok.png              ← Ảnh tile
├── css/
│   └── style.css       ← Giao diện (màu sắc, font chữ)
├── js/
│   ├── script.js       ← ⭐ FILE CHÍNH (lời chúc, ảnh, nhạc)
│   ├── Stage.js        ← Engine pháo hoa
│   ├── MyMath.js       ← Thư viện toán
│   └── fscreen.js      ← Fullscreen API
├── fonts/              ← Font chữ
├── images/             ← ⭐ ẢNH (thay ảnh tại đây)
│   ├── favicon.png
│   └── image1-5.jpeg
└── audio/              ← ⭐ ÂM THANH
    ├── 321_join.mp3    ← Nhạc nền (thay file này)
    ├── lift1-3.mp3     ← Tiếng phóng pháo
    ├── burst1-2.mp3    ← Tiếng nổ lớn
    ├── burst-sm-1-2.mp3← Tiếng nổ nhỏ
    ├── crackle1.mp3    ← Tiếng lách tách
    └── crackle-sm-1.mp3
```

---

## 🧪 Test trước khi deploy

Vì trình duyệt chặn `fetch()` khi mở file trực tiếp, bạn cần chạy local server:

```bash
# Cách 1: Python (đã cài sẵn)
cd happy-new-year
python -m http.server 8080
# Mở http://localhost:8080

# Cách 2: Node.js
npx -y http-server . -p 8080
# Mở http://localhost:8080
```

> 🎯 **Trên GitHub Pages thì không cần lo điều này** — web sẽ hoạt động đầy đủ âm thanh + hình ảnh!

---

## Credit
Dựa trên project [Firework Simulator](https://github.com/NianBroken/Firework_Simulator) by 碎念_Nian (Apache-2.0 License)
