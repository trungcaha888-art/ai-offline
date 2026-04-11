# AI BUSINESS SYSTEM — Landing Page Skill

> Quy trình thiết kế & phát triển landing page **AI Business System** cho Trung Caha.  
> Cập nhật: 2026-04-10

---

## 1. Tổng Quan Dự Án

| Thông tin | Chi tiết |
|---|---|
| **Tên sản phẩm** | AI Business System |
| **Tagline** | Xây Doanh Nghiệp AI – Tinh Gọn – Tự Động – Sinh Lợi Nhuận |
| **Thư mục** | `LANDING PAGE/AI BUSINESS SYSTEM/` |
| **Tech stack** | HTML + CSS thuần, font Inter (Google Fonts) |
| **Theme** | Premium Dark + Gold Accents |
| **Deploy** | GitHub Pages / Cloudflare Pages |

---

## 2. Cấu Trúc File

```
AI BUSINESS SYSTEM/
├── index.html          # Trang chính
├── style.css           # CSS toàn bộ
├── ảnh thầy.png        # Ảnh Trung Caha (nền trắng, vest đen, cà vạt đỏ)
├── anh1.jpg            # Building AI Agents (bên trái thầy)
├── anh2.jpg            # Claude AI (bên trái thầy)
├── anh3.webp           # AI Digital Human (bên phải thầy)
├── anh4.jpg            # Google Antigravity (bên phải thầy)
├── anh5.jpg            # AI Robot Automation (bên phải thầy)
├── og-thumbnail.png    # Ảnh Open Graph (1200x630)
├── favicon.png         # Favicon
└── SKILL.md            # File này — quy trình thiết kế
```

---

## 3. Design System

### 3.1 Bảng Màu

| Token | Giá trị | Dùng cho |
|---|---|---|
| `--gold` | `#d4a853` | Subtitle, border, accent |
| `--gold-light` | `#e8c97a` | Hover, highlight |
| `#f5c842` | Vàng sáng rực | **Tiêu đề chính + chữ đậm nhấn mạnh** |
| `--bg-primary` | `#0a0a0a` | Nền chính |
| `--bg-secondary` | `#111111` | Nền section phụ |
| `--text-primary` | `#ffffff` | Chữ chính |
| `--text-secondary` | `rgba(255,255,255,0.7)` | Chữ phụ |
| `--border-gold` | `rgba(212,168,83,0.25)` | Viền vàng mờ |

### 3.2 Typography

- **Font:** Inter (Google Fonts) — weights: 300, 400, 500, 600, 700, 800, 900
- **Title:** `clamp(2.5rem, 6vw, 4.5rem)` — weight 900, letter-spacing 0.04em
- **Subtitle:** `clamp(0.85rem, 2vw, 1.15rem)` — weight 600, uppercase, letter-spacing 0.15em
- **Body:** 1rem, line-height 1.6

### 3.3 Effects

| Effect | Chi tiết |
|---|---|
| **Ambient Glow** | 3 radial-gradient blobs (left, right, center) — animation `glowPulse` 6s |
| **Particles** | JS tạo 20-40 dots vàng nhỏ, animation `particleFloat` |
| **Photo Float** | 3 keyframes khác nhau, 5-7.5s, rotate nhẹ ±6deg |
| **Banner Glow** | Border vàng pulse sáng/mờ 4s cycle |
| **Entrance** | Fade-in + slide-up, delay tăng dần (0.2s → 0.8s) |

---

## 4. Quy Trình Tạo Hero Section

### Bước 1: Chuẩn bị ảnh
- Ảnh thầy Trung Caha (`ảnh thầy.png`) — nền trắng/trong, chất lượng cao
- 5 ảnh công nghệ AI:
  - **Bên trái (2 ảnh):** anh1, anh2 — xếp chéo chồng nhẹ
  - **Bên phải (3 ảnh):** anh3, anh4, anh5 — xếp zig-zag chồng nhẹ
- Tất cả ảnh có **viền trắng** (`border: 3px solid rgba(255,255,255,0.85)`)

### Bước 2: Tạo HTML (index.html)
```
<section class="hero">
  ├── Ambient glow (3 div)
  ├── Particles container
  ├── hero__content
  │   ├── h1.hero__title         → "AI BUSINESS SYSTEM" (vàng sáng)
  │   ├── p.hero__subtitle       → Tagline (vàng gold, uppercase)
  │   ├── blockquote.hero__quote → Quote + strong vàng
  │   └── hero__showcase
  │       ├── photo-group--left  → anh1 (rotate -6°) + anh2 (rotate +4°)
  │       ├── hero__teacher      → ảnh thầy (center, z-index 5)
  │       └── photo-group--right → anh3 (+5°) + anh4 (-4°) + anh5 (+3°)
  └── hero__bottom-banner → Khung viền vàng mờ ảo
</section>
```

### Bước 3: Tạo CSS (style.css)
1. **Design tokens** (CSS variables) → màu, font, spacing
2. **Reset** → box-sizing, margin, padding
3. **Hero layout** → flex column, no min-height, justify flex-start
4. **Glow effects** → 3 blobs absolute, blur 80px
5. **Particles** → absolute, animation float
6. **Title/Subtitle/Quote** → entrance animation delay tăng dần
7. **Showcase** → relative container, height 520px, max-width 1000px
8. **Teacher image** → absolute center bottom, width 480px, drop-shadow
9. **Photo groups** → absolute left/right, top 50%
10. **Individual photos** → absolute position, border trắng, rotate, float animation
11. **Bottom banner** → khung glass, border gold glow animation
12. **Responsive** → 1024px, 768px, 480px breakpoints

### Bước 4: JavaScript
- `createParticles()` → tạo 20-40 particle dots
- `initScrollAnimations()` → IntersectionObserver cho `.reveal`
- Entrance class `loaded` sau 100ms

### Bước 5: Chạy localhost test
```bash
py -m http.server 8080
```
→ Mở `http://localhost:8080` để xem

---

## 5. Layout Ảnh Chi Tiết

### Bên trái thầy (2 ảnh chéo chồng)
```
Photo 1 (anh1): 260×170px, rotate(-6°), top: -90px, left: 0, z-index: 3
Photo 2 (anh2): 220×145px, rotate(+4°), top: 55px, left: 50px, z-index: 2
```
→ Ảnh 1 ở trên, nghiêng trái. Ảnh 2 chồng nhẹ góc dưới phải.

### Bên phải thầy (3 ảnh zig-zag)
```
Photo 3 (anh3): 230×150px, rotate(+5°), top: -110px, right: 0, z-index: 3
Photo 4 (anh4): 210×138px, rotate(-4°), top: 15px, right: 50px, z-index: 4
Photo 5 (anh5): 200×132px, rotate(+3°), top: 130px, right: 10px, z-index: 2
```
→ 3 ảnh xếp từ trên xuống, lệch ngang tạo zig-zag, chồng nhẹ góc.

---

## 6. Bottom Banner — Khung Viền Vàng Mờ Ảo

```css
.hero__bottom-banner {
  background: rgba(10, 10, 10, 0.7);        /* Nền dark glass */
  backdrop-filter: blur(12px);               /* Mờ ảo */
  border: 1px solid rgba(212,168,83,0.35);   /* Viền vàng */
  border-radius: 16px;
  box-shadow: 0 0 30px rgba(212,168,83,0.1); /* Glow */
  animation: bannerGlow 4s ease-in-out infinite; /* Pulse viền */
}
```

Nội dung banner:
- Chữ thường: `var(--text-secondary)` (trắng mờ)
- Chữ đậm (strong): `var(--gold-light)` (vàng sáng)
- Chữ nghiêng (em): `var(--gold)` (vàng)

---

## 7. Responsive Breakpoints

| Breakpoint | Teacher width | Photo scale | Ghi chú |
|---|---|---|---|
| Desktop (>1024px) | 480px | 100% | Full layout |
| Tablet (≤1024px) | 400px | ~75% | Ảnh nhỏ hơn |
| Mobile (≤768px) | 300px | ~55% | Ảnh thu gọn |
| Small (≤480px) | 240px | ~42% | Ẩn anh5, border 2px |

---

## 8. SEO Checklist

- [x] `<title>` mô tả đầy đủ
- [x] `<meta description>` compelling
- [x] Open Graph tags (og:title, og:description, og:image)
- [x] Twitter Card tags
- [x] Semantic HTML (`<section>`, `<h1>`, `<blockquote>`)
- [x] Font preconnect (Google Fonts)
- [x] `lang="vi"` trên `<html>`
- [ ] og-thumbnail.png (cần tạo)
- [ ] favicon.png (cần tạo)

---

## 9. Checklist Mở Rộng (Các Section Tiếp Theo)

- [ ] Pain Points section
- [ ] Giới thiệu AI Business System
- [ ] Lộ trình 3 ngày
- [ ] Bonus section
- [ ] Testimonials / Social Proof
- [ ] Pricing / Checkout
- [ ] FAQ
- [ ] Footer + CTA cuối

---

## 10. Lưu Ý Quan Trọng

> ⚠️ **KHÔNG generate khuôn mặt thật** — dùng `ảnh thầy.png` có sẵn  
> ⚠️ **Luôn lưu vào thư mục dự án** trên Google Shared Drive  
> ⚠️ **Font Inter** — không dùng framework CSS  
> ⚠️ **Thiết kế premium** — gradient, glassmorphism, micro-animation  
> ⚠️ **Tiếng Việt CÓ DẤU** trong mọi content
