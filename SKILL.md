---
name: viet-ai-humanizer
description: "Kiểm tra và chỉnh sửa văn bản tiếng Việt để loại bỏ dấu hiệu AI. Dùng khi người dùng muốn: kiểm tra bài có phải AI viết không, humanize văn bản, làm bài bớt 'mùi AI', chuẩn bị bài đăng Brands Vietnam. Trigger: 'kiểm tra AI', 'chỉnh bài AI', 'humanize', 'bớt mùi AI', 'viết lại tự nhiên hơn', hoặc người dùng paste đoạn văn tiếng Việt hỏi có vẻ AI không."
---

# Viet AI Humanizer

Phát hiện và loại bỏ dấu hiệu AI trong văn bản tiếng Việt. Giữ nguyên ý nghĩa và giọng văn gốc — chỉ can thiệp chỗ "lộ AI".

> **Quan trọng:** Một dấu hiệu đơn lẻ không đủ kết luận là AI. Tìm **cụm** dấu hiệu — càng nhiều cùng xuất hiện, xác suất AI càng cao.

---

## Bước 1: Phân tích 5 nhóm dấu hiệu

Trích dẫn đoạn cụ thể với mỗi dấu hiệu tìm được.

### Dấu hiệu 1 — Diễn đạt máy móc, ngôn ngữ sáo

**Câu khuôn:** *"Trong bối cảnh [X] đang phát triển không ngừng…"*, *"Trong thời đại số hiện nay…"*, kết bài bằng *"Tóm lại / Kết luận là / Nhìn chung"*

**Từ nối sáo:** Hơn nữa, Thêm vào đó, Bên cạnh đó, Không những vậy (xuất hiện liên tục)

**AI vocabulary** (đáng lo khi xuất hiện cụm): *tạo ra giá trị, đồng bộ hoá, tối ưu hoá, nâng cao trải nghiệm, thúc đẩy tăng trưởng, tiên phong, đột phá, toàn diện, bền vững, then chốt, cốt lõi, hệ sinh thái (abstract), hành trình (abstract)*

**Ngôn ngữ quảng cáo:** độc đáo, ấn tượng, vượt trội, năng động; câu kiểu *"đóng vai trò then chốt trong / là minh chứng cho / đánh dấu bước ngoặt"*

**Signposting** (thông báo thay vì làm): *"Hãy cùng tìm hiểu…"*, *"Dưới đây chúng ta sẽ khám phá…"*

**Phân tích bề mặt** (mệnh đề phụ không thêm thông tin): *"…, qua đó thể hiện cam kết…"*, *"…, từ đó cho thấy sự chuyển dịch…"*

**Các pattern nhỏ khác:**
- Copula avoidance: *"đóng vai trò là"* → đổi thành *"là"*
- Bộ ba ép buộc: ép ý vào nhóm 3 dù thực tế chỉ có 2 hoặc 4 ý
- Persuasive tropes: *"Điều thực sự quan trọng là / Bản chất của vấn đề là"* → câu theo sau thường chỉ nhắc lại điều đã nói
- Lặp luận điểm nhiều đoạn, chỉ đổi cách diễn đạt, không thêm thông tin mới

### Dấu hiệu 2 — Format rối, bullet quá nhiều

- **Bullet nông:** mở đầu *"Dưới đây là một số…"*, các ý chung chung, trùng lặp, dùng list ở chỗ nên viết đoạn văn
- **Inline-header list:** `- **Tốc độ:** Nhanh hơn…` → câu sau tiêu đề chỉ nhắc lại tiêu đề
- **Bold thừa:** in đậm trang trí thay vì nhấn mạnh thật sự
- **Emoji trang trí:** `🚀 **Giai đoạn 1:**`, `✅ **Kết quả:**`
- **Header + câu lặp:** tiêu đề ngay sau là một câu chỉ nhắc lại tiêu đề

### Dấu hiệu 3 — Em-dash (—) xuất hiện nhiều

Dấu `—` (dài, khác dấu gạch nối `-`) từ 2 lần trở lên trong đoạn ngắn là tín hiệu rõ, đặc biệt dạng đôi: *"chiến dịch này — được triển khai vào quý 3 — đã đạt…"*

### Dấu hiệu 4 — Sót giọng chatbot

- **Prompt còn sót:** *"Bạn đã hỏi tôi về…"*, *"Chắc chắn rồi! Tất nhiên! Được thôi…"*
- **Giọng xu nịnh:** *"Đây là câu hỏi rất hay!"*, *"Bạn hoàn toàn đúng khi…"*
- **Kết bài chatbot:** *"Hy vọng bài viết hữu ích!"*, *"Hãy để lại bình luận nếu có câu hỏi!"*

### Dấu hiệu 5 — Cấu trúc câu yếu, từ lấp chỗ trống

- **Synonym cycling:** *"chiến dịch… kế hoạch… chương trình… hoạt động…"* (cùng chỉ một thứ)
- **False ranges:** *"từ chiến lược đến thực thi / từ người mới đến chuyên gia"* → nghe toàn diện nhưng vô nghĩa
- **Excessive hedging:** chồng nhiều từ phòng thủ: *"có thể có lẽ dường như…"*
- **Passive voice thừa:** *"Kết quả được ghi nhận là…", "Điều này được xem là…"*
- **Filler phrases:** *"Trong bối cảnh đó / Nhìn vào thực tế / Điều quan trọng cần lưu ý là"*
- **Mục "Thách thức và Triển vọng" khuôn:** *"Mặc dù… vẫn còn thách thức… nhưng tương lai sáng"*

---

## False positives — KHÔNG gắn cờ khi đứng một mình

Văn phạm đúng, một từ nối, một dấu `—`, thuật ngữ chuyên ngành, chi tiết lạ và cụ thể (địa chỉ thật, số liệu có nguồn rõ, trích dẫn kỳ quặc) — những thứ này là tín hiệu của người viết thật.

---

## Bước 2: Liệt kê dấu hiệu + cách sửa

Sau khi phân tích, xuất danh sách theo dạng:

```
Dấu hiệu tìm thấy:
1. [Loại]: "[trích dẫn gốc]" → [cách sửa cụ thể theo bảng dưới]
2. [Loại]: "[trích dẫn gốc]" → [cách sửa cụ thể theo bảng dưới]
```

**Cách sửa theo từng loại — áp dụng cứng, không hỏi lại:**

| Dấu hiệu | Cách sửa |
|----------|----------|
| Câu mở đầu khuôn | Xóa hẳn, viết thẳng vào ý chính |
| Từ nối / filler / AI vocab | Xóa nếu câu vẫn đủ nghĩa; thay từ cụ thể hơn nếu cần nối ý |
| Ngôn ngữ quảng cáo | Thay bằng mô tả cụ thể |
| Signposting | Xóa |
| Mệnh đề phụ bề mặt | Xóa |
| Bullet list nông | Luôn gộp thành đoạn văn |
| Bold / emoji thừa | Xóa hết |
| Em-dash (`—` hoặc `–`) | Thay bằng dấu phẩy hoặc tách thành 2 câu. **Không để lại dấu `—` nào trong bản sau.** |
| Giọng chatbot / xu nịnh | Xóa toàn bộ, không thay |
| Kết bài sáo | Viết lại câu kết có luận điểm riêng |
| Synonym cycling | Chọn từ đầu tiên xuất hiện, dùng nhất quán xuyên suốt |
| Passive voice thừa | Chuyển chủ động khi rõ chủ thể |

---

## Bước 3: Xuất bản

Áp dụng tất cả các sửa đổi và xuất:

```
## Bản đã chỉnh sửa
[Toàn bộ văn bản sau khi sửa]

---
Thay đổi:
- [mỗi dòng một thay đổi chính]
```

Nếu bài dài hơn 1.500 từ, hỏi người dùng muốn bắt đầu từ phần nào.
