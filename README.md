# Lab 21 — Phân tích rủi ro AI qua case study thực tế

- Họ và tên: **Hoàng Bích Ngọc**
- MSSV / mã học viên: **2A202602766** *(suy ra từ tên repository, vui lòng xác nhận lại với hồ sơ lớp nếu cần)*
- Lớp: **[Điền lớp]**
- Ngành đã chọn: **Giáo dục / AI tutor**

## 1. Industry Risk Snapshot

| Nội dung | Đánh giá của tôi và lý do |
| --- | --- |
| Những tác hại chính có thể xảy ra | **Thông tin sai/hallucination, lời khuyên học tập sai, lộ dữ liệu học sinh, over-reliance**. Người học có thể học sai kiến thức; nhà trường có thể vi phạm bảo mật dữ liệu. |
| Mức độ high-stakes | **Cao**. AI tutor tác động trực tiếp đến chất lượng học tập, cơ hội thi cử và quyết định học tập dài hạn; với học sinh nhỏ tuổi, sai lệch kéo dài khó tự phát hiện. |
| Dữ liệu nhạy cảm có thể được sử dụng | Dữ liệu học sinh (họ tên, lớp, lịch sử học tập, điểm, hành vi tương tác, có thể gồm thông tin hỗ trợ tâm lý/tư vấn). Đây là dữ liệu giáo dục nhạy cảm, cần giới hạn truy cập và mục đích sử dụng. |
| Nhu cầu human review | **Cao**. Cần giáo viên/cố vấn kiểm tra ở các bước: (1) nội dung AI giải thích kiến thức cốt lõi, (2) khuyến nghị can thiệp học tập, (3) xử lý dữ liệu cá nhân và tình huống nhạy cảm. |

## 2. Case study 1 — LAUSD “Ed” chatbot (Mỹ, 2024)

### Brief Case

- Tổ chức / sản phẩm AI: Los Angeles Unified School District (LAUSD) và chatbot hỗ trợ học tập/phụ huynh tên **“Ed”** do startup AllHere triển khai.
- Thời gian, địa điểm / bối cảnh: Los Angeles, Mỹ; triển khai năm 2024 trong bối cảnh trường học muốn tăng hỗ trợ học tập sau giai đoạn gián đoạn vì COVID-19.
- AI được dùng để làm gì: Trợ lý hội thoại cho học sinh/phụ huynh để hỏi thông tin học tập, điều hướng dịch vụ và hỗ trợ tương tác với hệ thống trường.
- Vấn đề hoặc sự kiện đáng chú ý: Dự án gặp sự cố lớn sau khi triển khai; xuất hiện cáo buộc xử lý dữ liệu học sinh không phù hợp và dự án bị dừng.
- Số liệu có nguồn: Hợp đồng được công bố ở mức **tối đa 6 triệu USD/5 năm**; hệ thống nhắm tới quy mô khoảng **500.000 học sinh K-12** của LAUSD trong giai đoạn 2024.
- Nguồn:
  - EdSource (2024), *Communities demand transparency after Ed, LAUSD’s AI chatbot, fails*: https://edsource.org/2024/communities-demand-transparency-after-ed-lausds-ai-chatbot-fails/717772
  - The 74 (2024), *L.A. Schools Probe Charges its Hyped, Now-Defunct AI Chatbot Misused Student Data*: https://www.the74million.org/article/chatbot-los-angeles-whistleblower-allhere-ai/
- Phân biệt bằng chứng và nhận định:
  - **Bằng chứng từ nguồn**: quy mô triển khai lớn, dự án thất bại/dừng, và có điều tra/liên quan đến quản trị dữ liệu.
  - **Nhận định của tôi**: rủi ro hệ thống nằm không chỉ ở model mà còn ở quản trị nhà cung cấp, tích hợp dữ liệu và quy trình giám sát vận hành.

### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Khi học sinh/phụ huynh gửi truy vấn có thông tin cá nhân vào chatbot trong vận hành thực tế toàn quận. |
| Stakeholder bị ảnh hưởng | Học sinh, phụ huynh, giáo viên, nhà trường/quận học chánh, đội tuân thủ pháp lý. |
| Failure mode | Privacy leak, governance failure, potential misinformation do chatbot trong bối cảnh học đường. |
| Layer bắt đầu lỗi | **Grounding + Safety + vận hành tích hợp dữ liệu**. Có dấu hiệu lỗi ở cách kết nối dữ liệu/luồng xử lý và cơ chế kiểm soát triển khai; không đủ bằng chứng công khai để quy trách nhiệm chính xác cho riêng “Model”. |
| Harm xảy ra là gì? | **Đã xác nhận**: dự án gián đoạn, mất ổn định dịch vụ và phát sinh điều tra. **Nguy cơ**: lộ/lạm dụng dữ liệu học sinh và giảm niềm tin vào AI trong giáo dục. |
| Harm lens | Privacy loss, opportunity loss, misinformation risk. |
| Severity | **High** (vì liên quan dữ liệu học sinh ở quy mô lớn và dịch vụ hỗ trợ học tập cấp quận). |
| Scale | **High** (quy mô mục tiêu toàn hệ thống LAUSD, hàng trăm nghìn học sinh). |
| Probability | **Medium–High** trong các triển khai gấp nếu thiếu kiểm định dữ liệu và giám sát vendor. |
| Frequency | **Low–Medium** theo sự kiện công khai (không phải ngày nào cũng xảy ra, nhưng khi xảy ra thì tác động rộng). |
| Vì sao? | Số liệu quy mô và giá trị hợp đồng cho thấy bề mặt tác động lớn; nguồn báo chí giáo dục uy tín ghi nhận dự án thất bại và tranh cãi dữ liệu. Giới hạn: chưa có báo cáo kỹ thuật đầy đủ để định lượng chính xác mức lộ dữ liệu thực tế theo từng bản ghi. |

## 3. Case study 2 — Ảnh hưởng của câu trả lời chatbot đúng/sai tới quyết định người học (nghiên cứu thực nghiệm, 2025)

### Brief Case

- Tổ chức / sản phẩm AI: Nghiên cứu thực nghiệm về người học tương tác với chatbot AI trong bối cảnh học tập (công bố tại IEEE ICCAI 2025).
- Thời gian, địa điểm / bối cảnh: Năm 2025; bối cảnh giáo dục đại học với thiết kế thực nghiệm kiểm soát.
- AI được dùng để làm gì: Trả lời câu hỏi học thuật như một công cụ hỗ trợ học tập/tutor.
- Vấn đề hoặc sự kiện đáng chú ý: Khi chatbot đưa ra câu trả lời sai nhưng tự tin, một phần người học có xu hướng chấp nhận thông tin sai.
- Số liệu có nguồn: Nghiên cứu thực hiện trên **144 sinh viên đại học** (nêu rõ trong bài công bố) để đo ảnh hưởng của nội dung chatbot chính xác vs không chính xác lên lựa chọn của sinh viên.
- Nguồn:
  - IEEE (ICCAI 2025), *Student use of accurate and inaccurate chatbot content: an empirical study*: https://www.computer.org/csdl/proceedings-article/iccai/2025/249100a374/295OIVQ5pQc
- Phân biệt bằng chứng và nhận định:
  - **Bằng chứng từ nguồn**: có thiết kế thực nghiệm và cỡ mẫu 144 sinh viên; kết quả cho thấy nội dung chatbot ảnh hưởng đến quyết định người học.
  - **Nhận định của tôi**: trong triển khai AI tutor đại trà, rủi ro over-reliance có thể tăng mạnh nếu giao diện không buộc người học kiểm chứng nguồn/cách giải.

### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Khi sinh viên dùng câu trả lời chatbot để chốt đáp án/nộp bài mà không đối chiếu tài liệu chuẩn. |
| Stakeholder bị ảnh hưởng | Sinh viên, giảng viên, đơn vị đào tạo, hệ sinh thái đánh giá học thuật. |
| Failure mode | Hallucination + over-reliance + automation bias. |
| Layer bắt đầu lỗi | **Model + UX**. Model có thể tạo nội dung sai; UX nếu trình bày quá thuyết phục mà thiếu cảnh báo/nguồn sẽ làm người học tin quá mức. |
| Harm xảy ra là gì? | **Đã xác nhận trong nghiên cứu**: quyết định học tập bị ảnh hưởng bởi chất lượng câu trả lời chatbot. **Nguy cơ mở rộng**: suy giảm năng lực tự kiểm chứng và tăng lỗi học thuật trên diện rộng. |
| Harm lens | Misinformation, opportunity loss, dignity loss (khi người học bị đánh giá kém do tin sai). |
| Severity | **Medium–High** (thường không gây tổn hại thể chất trực tiếp nhưng ảnh hưởng kết quả học tập và năng lực dài hạn). |
| Scale | **Medium** trong phạm vi thí nghiệm; **có thể High** nếu áp dụng đại trà trong hệ thống học tập số. |
| Probability | **Medium** (đã có bằng chứng thực nghiệm về xu hướng bị ảnh hưởng, nhưng mức độ phụ thuộc bối cảnh môn học và thiết kế hệ thống). |
| Frequency | **Medium** (tương tác AI tutor diễn ra thường xuyên trong học tập số; nguy cơ lặp lại mỗi lần hỏi-đáp). |
| Vì sao? | Cỡ mẫu 144 cho phép quan sát hiệu ứng hành vi có ý nghĩa thực hành trong bối cảnh học tập. Giới hạn: đây là bối cảnh thực nghiệm, chưa phải toàn bộ hệ thống K-12; do đó cần thận trọng khi ngoại suy xác suất/tần suất sang mọi nhóm người học. |

---

## 4. Tổng kết ngắn

- Ngành **Giáo dục / AI tutor** có lợi ích rõ rệt nhưng rủi ro cao ở 3 điểm: **độ đúng kiến thức**, **hành vi phụ thuộc AI**, và **an toàn dữ liệu người học**.
- Cần thiết kế human-in-the-loop bắt buộc, cùng cơ chế minh bạch nguồn và kiểm định vendor trước khi mở rộng quy mô.
