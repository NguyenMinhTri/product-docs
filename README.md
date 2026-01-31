# Hướng Dẫn Chuyển Đổi Tài Liệu Word sang HTML

## 📁 Cấu Trúc Thư Mục

Mỗi file Word `.docx` sẽ có **1 folder riêng** với cấu trúc:

```
c:\Users\Tri\Docs\
├── [TenTaiLieu]/
│   ├── index.html          ← File HTML chính
│   ├── images/             ← Thư mục chứa hình ảnh
│   │   ├── image1.png
│   │   ├── image2.png
│   │   └── ...
│   └── README.md           ← (Tùy chọn) Ghi chú riêng cho tài liệu
│
├── [TenTaiLieu2]/
│   ├── index.html
│   └── images/
│
└── [TenTaiLieu].docx       ← File Word gốc (giữ lại để tham khảo)
```

---

## 🔄 Quy Trình Chuyển Đổi

### Bước 1: Trích xuất nội dung từ Word

```python
from docx import Document
import zipfile, os, shutil

docx_path = 'TenFile.docx'
output_folder = 'TenFile'

# Tạo thư mục
os.makedirs(f'{output_folder}/images', exist_ok=True)

# Trích xuất hình ảnh
with zipfile.ZipFile(docx_path, 'r') as z:
    for f in z.namelist():
        if 'media/' in f:
            z.extract(f, f'{output_folder}/images')
            src = os.path.join(f'{output_folder}/images', f)
            dst = os.path.join(f'{output_folder}/images', os.path.basename(f))
            shutil.copy2(src, dst)

# Đọc text
doc = Document(docx_path)
for para in doc.paragraphs:
    print(para.text)

# Đọc tables
for table in doc.tables:
    for row in table.rows:
        print([cell.text for cell in row.cells])
```

### Bước 2: Tạo file HTML

- Tạo file `index.html` trong folder
- Đường dẫn hình ảnh: `src="images/image1.png"`
- Sử dụng CSS inline hoặc trong `<style>` tag

### Bước 3: Design Guidelines

#### Font & Colors
```css
/* Font: Google Fonts - Be Vietnam Pro */
@import url('https://fonts.googleapis.com/css2?family=Be+Vietnam+Pro:wght@300;400;500;600;700&display=swap');

/* Màu sắc cơ bản */
:root {
    --primary: #1565C0;      /* Xanh dương cho title */
    --secondary: #00875A;    /* Xanh lá cho accent */
    --text-primary: #1A2B3C;
    --text-secondary: #5F6C7B;
    --border: #E4E8EC;
}
```

#### Layout Components
- **Header**: Gradient background + logo + tiêu đề
- **Section**: Border + border-radius + padding
- **Tables**: Header có gradient, rows xen kẽ màu
- **Steps**: Numbered circles + content
- **Device Cards**: Grid 3 cột với hình ảnh + specs
- **Info Box**: Background vàng nhạt + border-left

#### Print Optimization
```css
@media print {
    .section { break-inside: avoid; }
    th, .header { -webkit-print-color-adjust: exact; print-color-adjust: exact; }
}
```

---

## ✏️ Cập Nhật Tài Liệu

Khi cần cập nhật:
1. Mở file `[TenTaiLieu]/index.html`
2. Sửa trực tiếp HTML/CSS
3. Thêm hình mới vào folder `images/`
4. **KHÔNG** cần làm lại từ đầu

---

## 📋 Checklist Khi Tạo Mới

- [ ] Tạo folder mới với tên tài liệu
- [ ] Tạo subfolder `images/`
- [ ] Trích xuất hình ảnh từ Word vào `images/`
- [ ] Tạo `index.html` với đường dẫn `images/...`
- [ ] Kiểm tra hiển thị trong browser
- [ ] Kiểm tra Print Preview

---

## 📄 Danh Sách Tài Liệu Hiện Có

| Folder | Mô tả | Hình ảnh |
|--------|-------|----------|
| `HDSD-TU-NHIET-DO-IOT/` | Hướng dẫn sử dụng tủ giám sát nhiệt độ IoT | 7 |
| `NavisMod_NM03_manual/` | Hướng dẫn kết nối Navis Mod với biến tần FRECON | 13 |

---

## 🗑️ Dọn Dẹp

Sau khi tạo xong folder, có thể xóa:
- File `.html` bên ngoài folder
- Folder `extracted_images/`, `nm03_images/`
- Script Python tạm: `extract_*.py`, `organize_files.py`
