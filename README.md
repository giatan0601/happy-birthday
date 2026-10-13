# happy-birthday
# 🎂 Happy Birthday

Trang web chúc mừng sinh nhật được làm bằng **HTML + CSS + JavaScript (jQuery)** thuần, không cần build hay cài đặt gì. Mở lên là có ngay hộp quà, nhạc nền, hiệu ứng chữ chạy, bóng bay và một bức thư gõ chữ tự động.

> Bản hiện tại là quà sinh nhật gửi tặng **cô Phan Thanh** (sinh nhật **21/04**), nhưng bạn có thể đổi tên, ảnh, lời chúc để tặng bất kỳ ai.

---

## ✨ Tính năng

- 🎁 **Màn hình hộp quà** ban đầu: bấm vào để mở trang (đồng thời kích hoạt nhạc nền do trình duyệt chặn autoplay).
- 🎵 **Nhạc nền** `q.mp3` tự lặp, âm lượng tăng dần (fade-in) sau cú click đầu tiên.
- 🔤 **Tiêu đề "Happy Birthday"** hiện từng chữ theo thời gian, kèm chiếc mũ sinh nhật rơi xuống.
- 📅 **Ngày sinh** được gõ từng ký tự như máy đánh chữ.
- 🖼️ **Ảnh chân dung tròn** trồi lên từ dưới màn hình, có mũ sinh nhật (SVG), tên người nhận và bóng bay đung đưa.
- 🔵 **Huy hiệu tròn xoay** chữ "happy-birthday" quanh trái tim đập.
- ⭐🌸 **Sao, hoa, mặt cười** trang trí xuất hiện lần lượt.
- ✉️ **Nút "xem thư chúc mừng"**: mở khung thư, tiêu đề và nội dung được **gõ tự động**, tự cuộn xuống.
- 📱 **Responsive**: có media query riêng cho màn hình ≤ 658px.

---

## 📁 Cấu trúc dự án

```
happy-birthday/
├── index.html      # Cấu trúc trang + dữ liệu lời chúc + toàn bộ JavaScript
├── style.css       # Giao diện, animation, responsive
├── q.mp3           # Nhạc nền
├── images/         # Ảnh dùng trong trang (cờ, mũ, ảnh người nhận, bóng bay, ...)
└── README.md
```

Các ảnh được tham chiếu trong `index.html`:

| File | Dùng cho |
| --- | --- |
| `images/1.png` | Dây cờ treo hai bên phía trên |
| `images/hat.png` | Mũ sinh nhật rơi xuống tiêu đề |
| `images/phanthanhpng.png` | Ảnh người nhận (khung tròn) |
| `images/balloon1.png`, `images/balloon2.png` | Bóng bay |
| `images/decorate_flower.png` | Hoa trang trí |
| `images/decorate.png` | Hình trang trí góc dưới |
| `images/smiley_icon.png` | Mặt cười |

---

## 🚀 Cách chạy

**Cách 1: mở trực tiếp**

```bash
git clone https://github.com/giatan0601/happy-birthday.git
cd happy-birthday
```

Sau đó mở file `index.html` bằng trình duyệt (double-click).

**Cách 2: chạy bằng server cục bộ** (khuyên dùng nếu nhạc/ảnh không tải được)

```bash
# Python
python -m http.server 8000

# hoặc Node.js
npx serve .
```

Rồi truy cập `http://localhost:8000`.

**Cách 3: đưa lên mạng bằng GitHub Pages**

1. Vào **Settings → Pages** của repo.
2. Chọn **Branch: `main`** và thư mục **`/ (root)`**, bấm **Save**.
3. Chờ khoảng 1 phút, trang sẽ có địa chỉ `https://giatan0601.github.io/happy-birthday/`.

> 💡 Cần kết nối Internet vì trang tải **Font Awesome**, **Google Fonts** và **jQuery** từ CDN.

---

## 🛠️ Tuỳ chỉnh cho người khác

### 1. Đổi tên và tiêu đề trang
Trong `index.html`, sửa các chỗ sau:

- Thẻ `<title>`: `Happy Birthday Phan Thanh`
- Dòng tên dưới ảnh: `Tới PHAN THANH`
- Thẻ `.card1` (hộp thư 3D): `To: PHAN THANH 💖`

### 2. Đổi ngày sinh
Trong thẻ `<script>` cuối file:

```js
let datetxt = "21 APRIL";
```

### 3. Đổi nội dung thư
Cũng trong thẻ `<script>`:

```js
let datatxtletter = [...("Nội dung lời chúc của bạn ...")]; // nội dung thư gõ tự động
let titleLetter = "Gửi Cô Phan Thanh";                        // tiêu đề thư
```

### 4. Đổi ảnh người nhận
Thay file `images/phanthanhpng.png` bằng ảnh của bạn (giữ nguyên tên file), hoặc sửa đường dẫn trong `index.html`. Nên dùng ảnh vuông hoặc gần vuông để khung tròn đẹp.

### 5. Đổi nhạc nền
Thay file `q.mp3` bằng bài hát khác (giữ tên `q.mp3`) hoặc sửa thẻ `<source src="q.mp3">`.

### 6. Đổi màu chủ đạo
Các biến màu nằm ở đầu `style.css`:

```css
:root {
    --color-pink: #feecea;       /* nền trang */
    --color-text-pink: #FF7882;  /* màu nhấn chính */
    --color-bg-letter: #fff8e4;  /* nền khung thư */
    --color-border: #DACCBF;
}
```

### 7. Chỉnh thời gian xuất hiện hiệu ứng
Các hiệu ứng chạy theo mốc thời gian (giây) được đặt qua biến `--t` trong HTML và độ trễ `animation` trong CSS. Ví dụ chữ "Happy" bắt đầu ở giây thứ 4, ngày sinh được gõ sau 12 giây, nút thư hiện lúc giây thứ 16. Muốn nhanh hơn hoặc chậm hơn, hãy sửa các giá trị này.

---

## 🧰 Công nghệ sử dụng

- HTML5, CSS3 (animation, keyframes, clip-path, perspective 3D)
- JavaScript + [jQuery 3.7.1](https://jquery.com/)
- [Font Awesome 6.5.1](https://fontawesome.com/) (biểu tượng)
- Google Fonts: Poppins, Dancing Script, Titan One, Sriracha, Coiny, Nerko One

---

## ⚠️ Lưu ý

- Trình duyệt chặn tự phát âm thanh, nên nhạc chỉ bắt đầu sau khi người xem **click/chạm lần đầu** (cú click vào hộp quà).
- Trong `index.html` có đoạn gọi `createLantern`, nhưng hàm này chưa được định nghĩa. Lỗi này nằm trong `.catch`/callback nên không ảnh hưởng nhạc, nhưng bạn có thể xoá dòng đó hoặc tự thêm hiệu ứng đèn lồng.
- Khối `.boxMail` (thiệp 3D) đã có sẵn HTML/CSS nhưng chưa có đoạn JS nào thêm class `active` để mở nó; nút hiện tại chỉ mở khung thư gõ chữ. Muốn dùng thiệp 3D, hãy thêm `document.querySelector('.boxMail').classList.add('active')` vào sự kiện bạn muốn.
- Ảnh `cute2.png` được gọi ở thư mục gốc trong khối thiệp 3D; hãy đảm bảo file này tồn tại nếu bạn bật khối đó.

---

## 💌 Lời nhắn

Làm ra để gửi một lời chúc thật lòng. Nếu bạn dùng lại dự án này, hãy thay bằng lời của chính mình nhé! 🎉
