# 📘 OMWATER — CHUẨN TÀI LIỆU KỸ THUẬT CHO AI

> **Mục đích file này:** Khi có dự án mới, AI đọc file này để hiểu đầy đủ về công ty, quy chuẩn thiết kế, quy trình an toàn, thiết bị thường dùng, và cấu trúc tài liệu HTML chuẩn — từ đó tạo tài liệu hướng dẫn thi công / lắp đặt / vận hành chuyên nghiệp.
>
> **Cập nhật lần cuối:** 09/06/2026

---

## 1. THÔNG TIN CÔNG TY

### 1.1 Tên công ty

| Dạng | Giá trị |
|------|---------|
| **Tên đầy đủ** | CÔNG TY TNHH THƯƠNG MẠI DỊCH VỤ KỸ THUẬT SẢN XUẤT O & M |
| **Tên viết tắt (DÙNG CHÍNH)** | **CÔNG TY TNHH TM DV KT SX O & M** |
| **Tên thương hiệu** | OMWater / O&M Water |
| **Thương hiệu IoT** | NAVIS IoT / Navis Smart Industrial |

### 1.2 Website & Liên hệ

| Thông tin | Giá trị |
|-----------|---------|
| **Website chính** | [omwater.vn](https://omwater.vn) |
| **Website IoT** | [navis.iotdaiviet.com](https://navis.iotdaiviet.com) |
| **Website IoT 2** | [iotdaiviet.com](https://iotdaiviet.com) |
| **Email** | omwater.vn@gmail.com |

### 1.3 Nhân sự kỹ thuật

| Tên | Vai trò | SĐT | Ghi chú |
|-----|---------|-----|---------|
| **Trí Nguyễn** | Kỹ thuật IoT, lập trình | 0387 226 446 | Liên hệ cấu hình IoT / Modbus / Dashboard |
| **Mr. Cường** | Kỹ thuật, kinh doanh | 0932 786 579 | Hotline/Zalo chính |

### 1.4 Logo & Hình ảnh

| File | Đường dẫn chuẩn | Dùng khi |
|------|-----------------|----------|
| **Logo OMWater** | `LOGO-omwater.png` | Header + Footer tất cả tài liệu |
| **Logo Navis** | `navis-logo.png` | Tài liệu liên quan IoT/Navis |

> ⚠️ **Quy tắc:** Luôn đặt logo ở **header** (góc phải) và **footer** (góc trái). Logo nền trắng, max-height 60px.

---

## 2. DESIGN SYSTEM — CHUẨN CSS

### 2.1 Template chính — Tài liệu kỹ thuật (in được, print-friendly)

Đây là template dùng cho **hướng dẫn thi công, lắp đặt, đấu dây, test** — chiếm ~80% tài liệu.

```css
/* Google Fonts */
@import url('https://fonts.googleapis.com/css2?family=Be+Vietnam+Pro:wght@300;400;500;600;700;800&display=swap');

:root {
    /* ── Màu chủ đạo xanh lá (OMWater Green) ── */
    --primary: #0F766E;           /* Teal chính */
    --primary-light: #14B8A6;     /* Teal nhạt */
    --primary-dark: #0D5E58;      /* Teal đậm */

    /* ── Màu phụ ── */
    --secondary: #1565C0;         /* Xanh dương */

    /* ── Màu cảnh báo ── */
    --danger: #DC2626;            /* Đỏ nguy hiểm */
    --danger-bg: #FEF2F2;
    --warning: #EA580C;           /* Cam cảnh báo */
    --warning-bg: #FFF7ED;
    --success: #16A34A;           /* Xanh lá thành công */
    --success-bg: #F0FDF4;
    --info-bg: #EFF6FF;           /* Xanh dương nhạt */

    /* ── Nền & Text ── */
    --background: #FFFFFF;
    --surface: #F8FAFC;
    --text-primary: #0F172A;
    --text-secondary: #64748B;
    --border: #E2E8F0;

    /* ── Gradient ── */
    --accent-gradient: linear-gradient(135deg, #0F766E 0%, #14B8A6 100%);
    --danger-gradient: linear-gradient(135deg, #DC2626 0%, #EF4444 100%);
}
```

> **Lưu ý:** Một số tài liệu cũ dùng `--primary: #00875A` (xanh lá đậm hơn). Template mới chuẩn hóa sang **Teal `#0F766E`**.

### 2.2 Font chữ

- **Font chính:** `'Be Vietnam Pro', sans-serif` — dùng cho tất cả tài liệu kỹ thuật
- **Font code/pin:** `'Consolas', monospace` — dùng cho label chân PLC, giá trị kỹ thuật
- **Font-size cơ sở:** `12px` (body), `11px` (nội dung step), `10px` (label nhỏ)

### 2.3 Layout chuẩn

```
Container: max-width 900-920px, margin auto, padding 12-16px
Header:    gradient accent, border-radius 10-12px, logo phải
Section:   background white, border 1px solid border, border-radius 8-10px, padding 14px 18px
Footer:    text-align center, border-top, logo + tên cty + website
```

### 2.4 Các component chuẩn

#### Section với số thứ tự
```html
<div class="section">
    <h2><span class="section-num">1</span>Tiêu Đề Section</h2>
    <!-- nội dung -->
</div>
```

#### Alert boxes
```html
<!-- Nguy hiểm (đỏ) — dùng cho cảnh báo an toàn điện -->
<div class="alert-danger">
    <strong>⚠️ CẢNH BÁO:</strong> Nội dung cảnh báo...
</div>

<!-- Nguy hiểm nổi bật (gradient đỏ, text trắng) — dùng cho cảnh báo tối quan trọng -->
<div class="alert-danger-full">
    <strong>⚡ CẢNH BÁO NGUY HIỂM</strong>
</div>

<!-- Cảnh báo (cam) — dùng cho lưu ý quan trọng -->
<div class="alert-warning">
    <strong>⚠️ LƯU Ý:</strong> Nội dung lưu ý...
</div>

<!-- Thông tin (xanh lá) — dùng cho mẹo, ghi chú tích cực -->
<div class="info-box">
    <strong>✅ Ghi chú:</strong> Nội dung...
</div>

<!-- Thông tin (xanh dương) — dùng cho thông số kỹ thuật, bối cảnh -->
<div class="info-blue">
    <strong>📌 Thông tin:</strong> Nội dung...
</div>
```

#### Step items (bước thực hiện)
```html
<div class="step-item">
    <div class="step-num-small">1</div>    <!-- Xanh: bước thường -->
    <div><b>Tên bước</b> — Chi tiết hành động.</div>
</div>

<div class="step-item">
    <div class="step-num-danger">1</div>   <!-- Đỏ: bước an toàn -->
    <div><b>Tên bước an toàn</b> — ...</div>
</div>

<div class="step-item">
    <div class="step-num-blue">1</div>     <!-- Xanh dương: bước phần mềm -->
    <div><b>Tên bước phần mềm</b> — ...</div>
</div>
```

#### Wire/Pin labels (nhãn dây/chân)
```html
<span class="wire-red">Đỏ (+)</span>      <!-- Nền đỏ nhạt -->
<span class="wire-black">Đen (GND)</span>  <!-- Nền đen -->
<span class="wire-yellow">Vàng (Signal)</span>  <!-- Nền vàng nhạt -->
<span class="pin-label">X0</span>          <!-- Nền xanh dương nhạt -->
```

#### Phase banners (phân chia giai đoạn thi công)
```html
<div class="phase-banner phase-prep">   <!-- Xanh dương: chuẩn bị -->
<div class="phase-banner phase-work">   <!-- Vàng: thao tác chính -->
<div class="phase-banner phase-test">   <!-- Xanh lá: kiểm tra -->
```

#### Device cards (thẻ thiết bị)
```html
<div class="device-grid">  <!-- grid 3 cột -->
    <div class="device-card">
        <h4>💧 Tên Thiết Bị</h4>
        <div class="specs">
            <div><b>Model:</b> ABC-123</div>
            <div><b>Nguồn:</b> 24VDC</div>
        </div>
    </div>
</div>
```

#### Checklist 2 cột
```html
<div class="two-col">
    <div>
        <h3>🔧 Trước khi đi</h3>
        <ul class="checklist">
            <li>Item 1</li>  <!-- tự thêm ☐ qua CSS -->
        </ul>
    </div>
    <div>
        <h3>✅ Sau khi xong</h3>
        <ul class="checklist">
            <li>Item 1</li>
        </ul>
    </div>
</div>
```

#### Contact box (liên hệ hỗ trợ)
```html
<div class="contact-box">
    <strong>☁️ LIÊN HỆ HỖ TRỢ:</strong> Mô tả...
    <div style="margin-top: 8px;">
        <div style="font-size: 13px; font-weight: 600;">👤 Trí Nguyễn — Kỹ thuật IoT</div>
        <div class="phone" style="margin-top: 4px;">📞 0387 226 446</div>
    </div>
</div>
```

### 2.5 Canvas — Sơ đồ kỹ thuật bằng JavaScript

Khi cần sơ đồ đấu dây / kiến trúc hệ thống, dùng `<canvas>` + JS với các helper functions chuẩn:

```javascript
// Helpers chuẩn dùng lại
function roundRect(x, y, w, h, r, fill, stroke, lineW) { /* vẽ hình chữ nhật bo góc */ }
function txt(text, x, y, color, size, align, bold) { /* vẽ text */ }
function drawWire(points, color, width) { /* vẽ dây nối qua nhiều điểm */ }
function drawArrow(fromX, fromY, toX, toY, color, width) { /* vẽ mũi tên */ }

// Luôn hỗ trợ HiDPI
const dpr = window.devicePixelRatio || 1;
canvas.width = WIDTH * dpr;
canvas.height = HEIGHT * dpr;
canvas.style.width = WIDTH + 'px';
canvas.style.height = HEIGHT + 'px';
ctx.scale(dpr, dpr);
```

### 2.6 Print Optimization (luôn thêm)

```css
@media print {
    body { font-size: 9pt; }
    .container { padding: 8px; }
    .section { break-inside: avoid; }
    .header, th, .alert-danger-full, .phase-banner {
        -webkit-print-color-adjust: exact;
        print-color-adjust: exact;
    }
}
```

### 2.7 Ảnh thực tế trong tài liệu

Khi user cung cấp ảnh thực tế (chụp hiện trường, thiết bị, sơ đồ), dùng gallery:

```html
<div class="photo-gallery">  <!-- grid 2 cột -->
    <div class="photo-card">
        <img src="images/anh1.png" alt="Mô tả">
        <div class="photo-caption">
            <span class="photo-num">1</span> Caption mô tả
        </div>
    </div>
</div>
```

---

## 3. AN TOÀN ĐIỆN — QUY TẮC BẮT BUỘC

> ⚡ **Mọi tài liệu thi công trong tủ điện PHẢI có phần An Toàn Điện.** Đây là yêu cầu bắt buộc, không được bỏ qua.

### 3.1 Các cảnh báo chuẩn (LUÔN SỬ DỤNG)

1. **Ngắt nguồn trước khi thao tác:**
   > ⚠️ QUAN TRỌNG: Ngắt toàn bộ nguồn điện tủ trước khi thao tác đấu dây!

2. **Dây input vẫn có điện:**
   > ⚡ CẢNH BÁO: Khi cúp CB, dây điện INPUT (nguồn vào tủ) VẪN CÒN ĐIỆN! Phải luôn né tránh dây điện input trong quá trình làm việc.

3. **Kiểm tra trước khi cấp nguồn:**
   > PHẢI kiểm tra tránh chập mạch trước khi cấp nguồn.

4. **Không đấu trực tiếp khi sai loại tín hiệu:**
   > KHÔNG ĐẤU TRỰC TIẾP cảm biến NPN vào PLC PNP (hoặc ngược lại). Phải qua bộ chuyển đổi.

### 3.2 Quy trình an toàn chuẩn (5 bước)

| Bước | Hành động | Chi tiết |
|------|-----------|----------|
| 1 | **Xác định CB** | Tìm đúng CB đang cấp nguồn cho mạch cần thao tác |
| 2 | **CÚP CB** | Ngắt CB, đợi ít nhất **10 giây** |
| 3 | **Kiểm tra bút thử điện** | Kiểm tra tất cả dây sẽ chạm — chắc chắn KHÔNG CÒN ĐIỆN |
| 4 | **Né dây input** | Dây nguồn input (trước CB tổng) LUÔN CÓ ĐIỆN — tuyệt đối không chạm |
| 5 | **Tay khô, nền khô** | Đảm bảo tay khô, đứng trên nền khô, không đeo nhẫn/đồ kim loại |

### 3.3 Phân biệt điện áp trong tủ

| Loại | Điện áp | Mức nguy hiểm | Vị trí thường gặp |
|------|---------|---------------|-------------------|
| **Nguồn AC** | 220VAC / 380VAC | ☠️ **CỰC KỲ NGUY HIỂM** | CB tổng, contactor, dây input |
| **Nguồn DC** | 24VDC | ⚠️ An toàn hơn nhưng vẫn cần cẩn thận | Nguồn cấp PLC, cảm biến, relay |
| **Tín hiệu** | 5-24VDC / 4-20mA | ✅ An toàn | Dây cảm biến, Modbus RS485 |

---

## 4. DỤNG CỤ & VẬT TƯ CHUẨN

### 4.1 Dụng cụ cơ bản (luôn mang theo)

| Loại | Danh sách |
|------|-----------|
| **Đo lường** | Đồng hồ vạn năng (VOM), Bút thử điện, Ampe kìm |
| **Cơ khí** | Tua vít dẹt (2mm, 4mm), Tua vít bake (+, −), Kìm cắt, Kìm tuốt dây, Kìm bấm đầu cos |
| **Vật tư tiêu hao** | Dây điện 0.5~1.0mm², Đầu cos pin/Y, Băng keo điện, Dây rút (cable ties), Ống gen co nhiệt |

### 4.2 Dụng cụ chuyên biệt (tùy dự án)

| Dụng cụ | Khi nào cần |
|---------|------------|
| Cáp USB lập trình PLC | Nạp code PLC Delta / XINJE |
| Cáp USB lập trình HMI | Nạp giao diện HMI Wecon |
| Laptop + phần mềm | ISPSoft, WPLSoft, PIStudio |
| Dây Modbus RS485 (xoắn đôi có shield) | Khi kéo đường truyền thông Modbus |
| Máy in đầu tag | Đánh nhãn dây trong tủ |

---

## 5. THIẾT BỊ THƯỜNG SỬ DỤNG

### 5.1 Bộ điều khiển & Gateway

| Thiết bị | Model | Chức năng | Ghi chú |
|----------|-------|-----------|---------|
| **PLC Delta** | DVP series | Điều khiển logic, đọc xung HSC | Phần mềm: ISPSoft / WPLSoft |
| **PLC XINJE** | XD2-16R-E, XD3 | Điều khiển logic | Dùng trong tủ EC-IoT |
| **HMI Wecon** | — | Giao diện người dùng | Phần mềm: PIStudio |
| **Navis Mod NM03** | NM03 | IoT Gateway, Modbus Master | WiFi / 4G → Cloud, RS485 |

### 5.2 Nguồn & Bảo vệ

| Thiết bị | Model | Thông số |
|----------|-------|----------|
| **Nguồn 24VDC** | Meanwell MDR-60-24 | 24VDC, 2.5A, DIN Rail |
| **CB** | CHINT NXB-63 | 1P, 10A |

### 5.3 Cảm biến & Bộ chuyển đổi

| Thiết bị | Loại tín hiệu | Ghi chú |
|----------|---------------|---------|
| **Cảm biến lưu lượng xung** | NPN, Hall Effect, 5-24VDC | 3 dây: Đỏ(+), Đen(GND), Vàng(Signal) |
| **Cảm biến EC (độ dẫn điện)** | 4-20mA | Dùng với DAM3102 |
| **Cảm biến nhiệt độ/độ ẩm** | Multispan | 4-20mA hoặc Modbus |
| **Bộ chuyển đổi NPN→PNP** | MRI-24TR/INV | Khi PLC PNP + cảm biến NPN |
| **Bộ chuyển đổi 4-20mA→Modbus** | DAM3102 | 2 kênh analog → Modbus RTU |
| **Bộ chuyển đổi xung→Modbus** | DI JIANG (epcb.vn) | 8CH, 5-24VDC, 115200bps, RS485 |
| **Biến tần** | FRECON FR150A-2S-0.7B-H | Điều khiển motor bơm |

### 5.4 Vỏ tủ & Phụ kiện

| Thiết bị | Model | Ghi chú |
|----------|-------|---------|
| **Tủ nhựa IP67** | Boxco BC-AGQ-203018G | Dùng cho tủ ngoài trời |

---

## 6. GIAO THỨC TRUYỀN THÔNG

### 6.1 Modbus RTU (RS485) — Giao thức chính

| Thông số | Giá trị mặc định | Ghi chú |
|----------|-------------------|---------|
| **Baudrate** | 9600 bps (Navis) / 115200 bps (DI JIANG) | Phải khớp giữa Master-Slave |
| **Data Bits** | 8 | — |
| **Parity** | None | — |
| **Stop Bits** | 1 | — |
| **Slave Address** | 1 (mặc định) | Mỗi thiết bị 1 địa chỉ khác nhau |

### 6.2 Đấu dây RS485 chuẩn

| Chân | Ký hiệu | Màu thường dùng |
|------|---------|-----------------|
| Data + | A+ | Đỏ hoặc Trắng |
| Data − | B− | Đen hoặc Xanh |
| GND (Shield) | GND | Nối 1 đầu (phía Master) |

> **Quy tắc:** A+ nối A+, B− nối B−. Nếu không nhận — thử đảo A↔B. Dùng dây xoắn đôi có shield.

### 6.3 Kiến trúc hệ thống IoT

```
Cảm biến → [Modbus RTU / 4-20mA] → Bộ chuyển đổi → [Modbus RS485] → Navis NM03 → [4G/WiFi] → Cloud → App/Dashboard
```

---

## 7. CẤU TRÚC TÀI LIỆU HTML CHUẨN

### 7.1 Template tổng quát

Mỗi tài liệu hướng dẫn thi công nên có các section sau (tuỳ dự án bỏ bớt hoặc thêm):

```
1. Tổng Quan Dự Án
   - Bối cảnh / Lý do
   - Tóm tắt công việc
   - Hình ảnh hiện trạng (gallery 2x2)

2. Dụng Cụ & Vật Tư Cần Chuẩn Bị
   - Grid 3 cột: Đo lường / Cơ khí / Vật tư
   - Device cards cho thiết bị chính

3. Thông Số Kỹ Thuật
   - Bảng spec thiết bị mới
   - Sơ đồ đấu dây (bảng + ảnh/canvas)

4. An Toàn Điện
   - Alert-danger-full: cảnh báo tối quan trọng
   - 5 bước an toàn chuẩn (step-num-danger)
   - Alert-warning: lưu ý thêm

5. Quy Trình Thi Công Chi Tiết
   - Phase A: Dò dây & Chuẩn bị (phase-prep)
   - Phase B: Cúp điện & Đấu dây (phase-work)
   - Phase C: Đóng điện & Kiểm tra (phase-test)
   - Mỗi phase có các step-item chi tiết
   - Bảng đấu dây inline

6. Cấu Hình Phần Mềm / Modbus
   - Thông số Modbus
   - Link download phần mềm (nếu có)
   - Contact box liên hệ hỗ trợ từ xa

7. Xử Lý Sự Cố (Troubleshooting)
   - Bảng: Hiện tượng / Nguyên nhân / Cách khắc phục

8. Checklist Hoàn Thành
   - 2 cột: Trước khi đi / Sau khi xong
```

### 7.2 Quy tắc đặt tên file

```
HDSD-[Chủ-đề-ngắn-gọn].html
```

**Ví dụ:**
- `HDSD-KetNoi-CamBien-LuuLuong.html`
- `HDSD-ThayThe-BoChuyenDoi-Xung-Modbus.html`
- `HDSD-Lap-Rap-va-Test-Tu-EC-IoT.html`

### 7.3 Quy tắc lưu ảnh

```
c:\Users\Tri\Docs\
├── images/                          ← Ảnh dùng chung
│   ├── anh1-cambien-luuluong.png
│   └── ...
├── [TenTaiLieu]/                    ← Folder riêng nếu nhiều ảnh
│   ├── index.html
│   └── images/
└── LOGO-omwater.png                 ← Logo ở root
```

### 7.4 Header chuẩn

```html
<div class="header">
    <div class="header-text">
        <h1>🔧 TIÊU ĐỀ TÀI LIỆU</h1>
        <p class="subtitle">Mô tả ngắn gọn</p>
        <p class="meta">CÔNG TY TNHH TM DV KT SX O & M | Phiên bản 1.0 | Ngày: DD/MM/YYYY</p>
    </div>
    <img src="LOGO-omwater.png" alt="O&M Water Logo">
</div>
```

### 7.5 Footer chuẩn

```html
<div class="footer">
    <img src="LOGO-omwater.png" alt="O&M Water">
    <strong>CÔNG TY TNHH TM DV KT SX O & M</strong> |
    <a href="https://omwater.vn">omwater.vn</a>
    <div style="margin-top: 4px;">Tài liệu nội bộ — Không phổ biến ra bên ngoài</div>
</div>
```

---

## 8. EMOJI CHUẨN DÙNG TRONG TÀI LIỆU

| Emoji | Dùng cho |
|-------|----------|
| 🔧 | Tiêu đề hướng dẫn thi công / lắp ráp |
| 📊 | Tiêu đề tài liệu giám sát / đo lường |
| 📋 | Dự án, tổng quan |
| ⚡ | Cảnh báo điện nguy hiểm |
| ⚠️ | Cảnh báo chung, lưu ý |
| ✅ | Hoàn thành, ghi chú tích cực |
| 📌 | Bối cảnh, thông tin quan trọng |
| 💧 | Cảm biến lưu lượng / nước |
| 🔄 | Bộ chuyển đổi |
| 📡 | IoT Gateway, truyền thông |
| 🔌 | Dụng cụ đo điện |
| 📦 | Vật tư, đóng gói |
| 📸 | Chụp ảnh (mẹo) |
| 📥 | Download file |
| ☁️ | Cloud, cập nhật từ xa |
| 👤 | Người liên hệ |
| 📞 | Số điện thoại |
| 🎯 | Mục đích, mục tiêu |
| ⚙️ | Thiết bị, cấu hình |
| 🔍 | Dò dây, khảo sát |

---

## 9. NHÀ CUNG CẤP THƯỜNG LÀM VIỆC

| Nhà cung cấp | Liên hệ | Sản phẩm |
|---------------|---------|----------|
| **Trường Thịnh** | Mr. Hiếu — 0915 030 220 | Tụ bù, thiết bị điện |
| **Humatic** | Hùng — 098 8020646 | Cảm biến, thiết bị đo |
| **Toàn Cầu** | Vũ Ngọc Nguyên — 0986 830 800 | PLC, HMI, biến tần |
| **epcb.vn** | — | Bộ chuyển đổi DI JIANG |
| **Đại Việt IoT** | — | Navis IoT Gateway |

---

## 10. QUY TRÌNH LÀM TÀI LIỆU MỚI (CHO AI)

Khi user yêu cầu tạo tài liệu hướng dẫn thi công cho dự án mới:

### Bước 1: Thu thập thông tin
- Hỏi user về: **dự án gì, thiết bị nào, thay gì, đấu dây sao**
- Yêu cầu **ảnh hiện trường** (cảm biến, tủ điện, thiết bị mới, sơ đồ)
- Xác nhận **giao thức truyền thông** (Modbus? 4-20mA? Digital?)

### Bước 2: Tạo file HTML
1. Copy images vào `c:\Users\Tri\Docs\images\` (đặt tên mô tả)
2. Tạo file HTML theo template Section 7.1
3. Đặt tên theo quy tắc `HDSD-[Chủ-đề].html`
4. Luôn thêm section **An Toàn Điện** (Section 3 trong file này)
5. Luôn thêm **Checklist** ở cuối
6. Luôn có **Canvas sơ đồ đấu dây** nếu có thông tin đấu dây
7. Dùng **photo-gallery** để chèn ảnh user cung cấp

### Bước 3: Kiểm tra
- Header có logo + tên công ty
- Footer có logo + tên công ty + website
- Print preview OK (mở file → Ctrl+P)
- Ảnh hiển thị đúng
- Sơ đồ canvas render đúng

---

## 11. DANH SÁCH TÀI LIỆU ĐÃ TẠO

| File | Mô tả | Ngày tạo |
|------|-------|----------|
| `HDSD-KetNoi-CamBien-LuuLuong.html` | Hướng dẫn kết nối cảm biến lưu lượng NPN qua bộ chuyển đổi MRI-24TR/INV | — |
| `HDSD-ThayThe-BoChuyenDoi-Xung-Modbus.html` | Thay thế PLC đọc xung bằng bộ DI JIANG → Modbus RS485 → Navis | 09/06/2026 |
| `HDSD-Lap-Rap-va-Test-Tu-EC-IoT.html` | Hướng dẫn lắp ráp và test tủ EC-IoT | — |
| `HDSD-Test-Tu-EC-IoT.html` | Hướng dẫn test tủ EC-IoT | — |
| `HDSD-TU-NHIET-DO-IOT.html` | Hướng dẫn sử dụng tủ giám sát nhiệt độ/độ ẩm | — |
| `NavisMod_NM03_manual.html` | Hướng dẫn Navis Mod NM03 | — |
| `PhuongAn_KyThuat_IoT_GiamSatNuocThai.html` | Phương án kỹ thuật IoT giám sát nước thải | — |
| `HoSo_KyThuat_GiamSat_4Kho.html` | Hồ sơ kỹ thuật giám sát 4 kho nhiệt độ/độ ẩm | — |
| `BaoTri_HT_RO_OMWater.html` | Hướng dẫn bảo trì hệ thống RO | — |

---

> **📌 Ghi nhớ cho AI:** File này là "bộ não" chuẩn. Khi tạo tài liệu mới, đọc file này TRƯỚC, sau đó tạo HTML theo đúng design system, cấu trúc, và quy tắc an toàn đã định nghĩa ở trên. Đảm bảo tài liệu **nhất quán** về giao diện, chuyên nghiệp, và **print-friendly**.
