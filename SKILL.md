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

**Phân tích bề mặt** (mệnh đề phụ không thêm thông tin): *"…, qua đó thể hiện cam kết…"*, *"…, từ đó cho thấy sự chuyển dịch…"* → xóa hoặc thay bằng nội dung thật

**Các pattern nhỏ khác:**
- Copula avoidance: *"đóng vai trò là"* → đổi thành *"là"*
- Bộ ba ép buộc: ép ý vào nhóm 3 dù thực tế chỉ có 2 hoặc 4 ý
- Persuasive tropes: *"Điều thực sự quan trọng là / Bản chất của vấn đề là"* → câu theo sau thường chỉ nhắc lại điều đã nói
- Lặp luận điểm nhiều đoạn, chỉ đổi cách diễn đạt, không thêm thông tin mới

### Dấu hiệu 2 — Format rối, bullet quá nhiều

- **Bullet nông:** mở đầu *"Dưới đây là một số…"*, các ý chung chung, trùng lặp, dùng list ở chỗ nên viết đoạn văn
- **Inline-header list:** `- **Tốc độ:** Nhanh hơn…` → câu sau tiêu đề chỉ nhắc lại tiêu đề
- **Bold thừa:** in đậm trang trí thay vì nhấn mạnh thật sự
- **Emoji trang trí:** `🚀 **Giai đoạn 1:**`, `✅ **Kết quả:**` → xóa hết
- **Header + câu lặp:** tiêu đề ngay sau là một câu chỉ nhắc lại tiêu đề → xóa câu lặp

### Dấu hiệu 3 — Em-dash (—) xuất hiện nhiều

Dấu `—` (dài, khác dấu gạch nối `-`) từ 2 lần trở lên trong đoạn ngắn là tín hiệu rõ, đặc biệt dạng đôi: *"chiến dịch này — được triển khai vào quý 3 — đã đạt…"*

Thay bằng: dấu phẩy, dấu chấm (tách câu), dấu hai chấm, hoặc ngoặc đơn.
**Quy tắc cứng:** bản sau chỉnh sửa không được chứa `—` hay `–`. Scan lại trước khi xuất.

### Dấu hiệu 4 — Sót giọng chatbot

- **Prompt còn sót:** *"Bạn đã hỏi tôi về…"*, *"Chắc chắn rồi! Tất nhiên! Được thôi…"*
- **Giọng xu nịnh:** *"Đây là câu hỏi rất hay!"*, *"Bạn hoàn toàn đúng khi…"*
- **Kết bài chatbot:** *"Hy vọng bài viết hữu ích!"*, *"Hãy để lại bình luận nếu có câu hỏi!"* → xóa toàn bộ

### Dấu hiệu 5 — Cấu trúc câu yếu, từ lấp chỗ trống

- **Synonym cycling:** *"chiến dịch… kế hoạch… chương trình… hoạt động…"* (cùng chỉ một thứ) → chọn một từ nhất quán
- **False ranges:** *"từ chiến lược đến thực thi / từ người mới đến chuyên gia"* → nghe toàn diện nhưng vô nghĩa → viết thẳng
- **Excessive hedging:** chồng nhiều từ phòng thủ: *"có thể có lẽ dường như…"* → giữ tối đa một từ mỗi câu
- **Passive voice thừa:** *"Kết quả được ghi nhận là…", "Điều này được xem là…"* → chuyển chủ động khi rõ chủ thể
- **Filler phrases:** *"Trong bối cảnh đó / Nhìn vào thực tế / Điều quan trọng cần lưu ý là"* → xóa
- **Mục "Thách thức và Triển vọng" khuôn:** *"Mặc dù… vẫn còn thách thức… nhưng tương lai sáng"* → tích hợp vào bài hoặc xóa

---

## False positives — KHÔNG gắn cờ khi đứng một mình

Văn phạm đúng, một từ nối, một dấu `—`, thuật ngữ chuyên ngành, chi tiết lạ và cụ thể (địa chỉ thật, số liệu có nguồn rõ, trích dẫn kỳ quặc) — những thứ này là tín hiệu của người viết thật.

---

## Bước 2: Báo cáo

```
**Mức độ "mùi AI":** Thấp / Trung bình / Cao
(Thấp: 1-2 dấu hiệu đơn lẻ | Trung bình: 3-4 dấu hiệu | Cao: cụm nhiều dấu hiệu rõ)

Dấu hiệu tìm thấy:
- Dấu hiệu X.x: "[trích dẫn]" → giải thích ngắn

Dấu hiệu không tìm thấy: [liệt kê]
```

---

## Bước 3: Chỉnh sửa

Hỏi *"Bạn có muốn tôi chỉnh sửa không?"* — trừ khi người dùng đã yêu cầu rõ từ đầu.

**Bảng sửa nhanh:**

| Dấu hiệu | Cách sửa |
|----------|----------|
| Câu mở đầu khuôn | Thay bằng câu dẫn vào vấn đề trực tiếp |
| Từ nối / filler / AI vocab | Xóa hoặc thay bằng từ cụ thể hơn |
| Ngôn ngữ quảng cáo | Thay bằng mô tả cụ thể hoặc xóa |
| Signposting | Xóa — đi thẳng vào nội dung |
| Mệnh đề phụ bề mặt | Xóa hoặc thay bằng câu có nội dung thật |
| Bullet list nông | Gộp thành đoạn văn |
| Bold / emoji thừa | Xóa hết |
| Em-dash | Dấu phẩy, dấu chấm, hoặc tách câu — không để lại `—` |
| Giọng chatbot / xu nịnh | Xóa toàn bộ |
| Synonym cycling | Chọn một từ nhất quán |
| Passive voice thừa | Chuyển chủ động |
| Kết bài sáo | Thay bằng kết bài có luận điểm riêng |

---

## Bước 4: Xuất bản

```
## Bản đã chỉnh sửa
[Toàn bộ văn bản sau khi sửa]

---
Tóm tắt thay đổi:
- [mỗi dòng một thay đổi chính]
```

Nếu bài dài hơn 1.500 từ, hỏi người dùng muốn bắt đầu từ phần nào.
