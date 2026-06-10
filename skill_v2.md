---
name: viet-ai-humanizer
description: "Phát hiện và tự động sửa dấu hiệu AI trong văn bản tiếng Việt — không đánh giá, chỉ fix thẳng. Dùng khi: bài cần humanize, bớt mùi AI, viết lại tự nhiên hơn. Trigger bất cứ khi nào người dùng paste văn bản tiếng Việt và hỏi có vẻ AI không, hoặc dùng từ: 'kiểm tra AI', 'chỉnh bài AI', 'humanize', 'bớt mùi AI', 'viết lại tự nhiên hơn'."
---

# Viet AI Humanizer

1. **Nhận diện dấu hiệu AI** — Quét theo danh sách bên dưới.
2. **Viết lại, không xóa** — Thay chỗ "lộ AI" bằng cách diễn đạt tự nhiên hơn, đảm bảo bao phủ toàn bộ nội dung gốc. Gốc có năm đoạn, bản sửa cũng có năm đoạn.
3. **Giữ nguyên ý nghĩa** — Không thay đổi thông điệp cốt lõi.
4. **Giữ đúng giọng văn** — Phù hợp với tông điệu chủ định (trang trọng, thân mật, chuyên môn). Chỉ thêm cá tính khi nội dung và giọng văn của tác giả cho phép.

**Thực hiện đúng thứ tự Bước 1 → 2 → 3 → 4. Không bỏ qua bước nào.**

---

## Bước 1: Phát hiện → Sửa

Quét toàn bộ văn bản. Phát hiện dấu hiệu nào thì sửa luôn theo bảng dưới. **Không bỏ sót.**

Một dấu hiệu đơn lẻ không kết luận là AI — tìm **cụm**. False positives không gắn cờ: từ nối đơn lẻ, một dấu em-dash, thuật ngữ chuyên ngành, số liệu có nguồn.

| Dấu hiệu | Cách sửa + Ví dụ |
|----------|-----------------|
| **Câu khuôn mở/kết** — "Trong bối cảnh X đang phát triển…", "Tóm lại…", "Kết luận là…" | Xóa, viết thẳng vào ý chính. **Trước:** "Trong bối cảnh ngành F&B đang phát triển mạnh mẽ, thương hiệu X đã ra mắt…" **Sau:** "Thương hiệu X vừa ra mắt…" |
| **Từ nối sáo** — Hơn nữa, Thêm vào đó, Bên cạnh đó, Không những vậy (liên tục) | Xóa nếu câu vẫn đủ nghĩa; thay từ cụ thể nếu cần nối ý. **Trước:** "Hơn nữa, chiến dịch này còn giúp tăng nhận diện thương hiệu." **Sau:** "Chiến dịch này cũng giúp tăng nhận diện thương hiệu." |
| **Ngôn ngữ quảng cáo** — độc đáo, ấn tượng, vượt trội, tiên phong, đột phá | Thay bằng mô tả cụ thể. **Trước:** "Giải pháp độc đáo và tiên phong này…" **Sau:** "Giải pháp này cho phép người dùng làm X trong 30 giây…" |
| **Thổi phồng tầm quan trọng** — "đánh dấu bước ngoặt lịch sử", "phản ánh xu hướng rộng lớn hơn", "đặt nền tảng cho tương lai" | Thay bằng mô tả trực tiếp sự việc. **Trước:** "Sự kiện này đánh dấu bước ngoặt lịch sử cho ngành." **Sau:** "Đây là lần đầu tiên ba công ty lớn nhất ngành ký chung một thỏa thuận." |
| **Trích dẫn mơ hồ** — "Các chuyên gia cho rằng…", "Theo nhiều nguồn tin…", "Giới quan sát nhận định…" | Thay bằng nguồn cụ thể nếu biết; xóa nếu không có. **Trước:** "Các chuyên gia cho rằng xu hướng này sẽ tiếp tục." **Sau:** Xóa, hoặc "Theo báo cáo Gartner 2024…" |
| **Negative parallelisms** — "Không chỉ là X, đây còn là Y", "Không phải A, mà là B", "Đây không phải về tốc độ — đây là về tầm nhìn" (hai vế thực ra cùng ý) | Viết thẳng ý chính, bỏ cấu trúc tương phản. **Trước:** "Đây không chỉ là một sản phẩm — đây là một cam kết." **Sau:** "Công ty cam kết hỗ trợ khách hàng sau bán hàng." |
| **Signposting** — "Hãy cùng tìm hiểu…", "Dưới đây chúng ta sẽ khám phá…" | Xóa, bắt đầu thẳng vào nội dung. **Trước:** "Hãy cùng tìm hiểu lý do X quan trọng." **Sau:** "X quan trọng vì…" |
| **Mệnh đề phụ rỗng** — "…, qua đó thể hiện cam kết…", "…, từ đó cho thấy sự chuyển dịch…" | Xóa mệnh đề phụ. **Trước:** "Công ty đầu tư vào R&D, qua đó thể hiện cam kết với đổi mới." **Sau:** "Công ty đầu tư vào R&D." |
| **Copula avoidance** — "đóng vai trò là", "đóng vai trò quan trọng như là" | Đổi thành "là". **Trước:** "Dữ liệu đóng vai trò là nền tảng…" **Sau:** "Dữ liệu là nền tảng…" |
| **Bộ ba ép buộc** — ép ý thành nhóm 3 dù chỉ có 2 hoặc 4 ý thật | Giữ đúng số ý thật, bỏ ý độn. **Trước:** "Ba trụ cột: tăng trưởng, bền vững, đổi mới." (nếu thực ra chỉ có hai ý riêng biệt) **Sau:** Viết đúng số ý thực sự. |
| **Persuasive tropes** — "Điều thực sự quan trọng là…", "Bản chất của vấn đề là…" (câu sau chỉ nhắc lại điều đã nói) | Xóa câu dẫn nhập, giữ nội dung phía sau. **Trước:** "Điều thực sự quan trọng là chúng ta cần hành động ngay." **Sau:** "Cần hành động ngay." |
| **Lặp luận điểm** — cùng ý xuất hiện ở nhiều đoạn, chỉ đổi cách diễn đạt | Xóa đoạn lặp, giữ đoạn diễn đạt tốt nhất. |
| **Bullet nông** — list ý chung chung, dùng list thay vì đoạn văn | Gộp thành đoạn văn. **Trước:** "• Tăng doanh thu • Mở rộng thị trường • Cải thiện thương hiệu" **Sau:** "Chiến dịch giúp tăng doanh thu, mở rộng sang thị trường miền Nam, và cải thiện nhận diện thương hiệu trong phân khúc 25–35 tuổi." |
| **Header + câu lặp** — câu ngay sau header chỉ nhắc lại header | Xóa câu nhắc lại. **Trước:** "## Kết quả\nPhần này trình bày các kết quả đạt được." **Sau:** "## Kết quả\nDoanh thu tăng 18%…" |
| **Bold / emoji thừa** — in đậm hoặc emoji không nhấn mạnh nội dung thật | Xóa hết. |
| **Title case heading** — "Chiến Lược Phát Triển Bền Vững" | Chỉ hoa chữ đầu tiên; giữ nguyên nếu là tên riêng. **Trước:** "Chiến Lược Phát Triển" **Sau:** "Chiến lược phát triển" |
| **Em-dash** — mọi dấu `—` hoặc `–` trong văn bản | Thay bằng dấu phẩy hoặc tách câu. **Trước:** "Chiến dịch này — triển khai quý 3 — đạt 200% mục tiêu." **Sau:** "Chiến dịch triển khai quý 3, đạt 200% mục tiêu." |
| **Giọng chatbot / xu nịnh** — "Đây là câu hỏi rất hay!", "Hy vọng bài viết hữu ích!" | Xóa toàn bộ. |
| **Kết bài sáo** — kết bằng lời kêu gọi chung chung hoặc nhắc lại đề bài | Viết lại với luận điểm cụ thể hoặc hành động rõ ràng. |
| **Synonym cycling** — cùng một thứ gọi nhiều tên: chiến dịch/kế hoạch/chương trình | Chọn từ đầu tiên, dùng nhất quán. |
| **Excessive hedging** — "có thể có lẽ dường như" chồng nhau | Giữ tối đa một từ phòng thủ/câu. **Trước:** "Điều này có thể có lẽ sẽ dẫn đến…" **Sau:** "Điều này có thể dẫn đến…" |
| **Passive voice thừa** — "Kết quả được ghi nhận là…", "Điều này được xem là…" | Chuyển chủ động khi rõ chủ thể. **Trước:** "Kết quả được ban lãnh đạo ghi nhận là tích cực." **Sau:** "Ban lãnh đạo đánh giá kết quả tích cực." |
| **Filler phrases** — "Trong bối cảnh đó…", "Nhìn vào thực tế…", "Điều quan trọng cần lưu ý là…" | Xóa, bắt đầu thẳng vào câu. |

---

## Bước 2: Dịch EN→VN

Với từ tiếng Anh có từ tương đương thông dụng trong tiếng Việt, tự động thay bằng từ tiếng Việt. Giữ tiếng Anh khi là tên riêng, thuật ngữ không có từ tương đương, hoặc văn bản dùng Anh-Việt có chủ đích.

---

## Bước 3: Xen kẽ câu ngắn với câu dài

AI thường viết câu đều đều về độ dài, tạo cảm giác máy móc. Đọc lại bản đã sửa và xen kẽ câu ngắn với câu dài khi cần. Câu ngắn đập vào mặt. Rồi một câu dài hơn giải thích, mở rộng, hoặc đặt ngữ cảnh cho điều vừa nói. Không cần sửa tất cả — chỉ chỗ nào đọc thấy nhịp đều đều quá thì điều chỉnh.

---

## Bước 4: Xuất

Bài >1.500 từ: hỏi người dùng muốn bắt đầu từ phần nào. Xuất toàn bộ văn bản đã sửa.
