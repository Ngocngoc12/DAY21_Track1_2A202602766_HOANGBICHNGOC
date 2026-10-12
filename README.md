# Lab 21 — Phân tích rủi ro AI qua case study thực tế

- Họ và tên: Hoàng Bích Ngọc
- MSSV / mã học viên: 2A202602766
- Lớp: [Chưa có dữ liệu trong repository]
- Ngành đã chọn: Giáo dục / AI tutor

### 1. Industry Risk Snapshot

| Nội dung | Đánh giá của tôi và lý do |
| --- | --- |
| Những tác hại chính có thể xảy ra | (1) **Misinformation**: AI tutor đưa lời giải/sự thật sai nhưng trình bày tự tin, học sinh học sai kiến thức. (2) **Over-reliance**: người học phụ thuộc gợi ý AI, giảm tự giải quyết bài. (3) **Fairness gap**: nhóm có thiết bị/mạng tốt dùng AI hiệu quả hơn, làm rộng chênh lệch học tập. |
| Mức độ high-stakes | **Trung bình đến cao**: kết quả học tập ảnh hưởng cơ hội thi cử/học bổng/nghề nghiệp; thường không tức thời như y tế cấp cứu, nhưng tích lũy theo thời gian và có thể tác động lớn đến lộ trình học của người học. |
| Dữ liệu nhạy cảm có thể được sử dụng | Dữ liệu học tập cá nhân (điểm, lịch sử làm bài, lỗi sai), dữ liệu định danh học sinh, trao đổi tự do với AI (có thể lộ thông tin gia đình/sức khỏe/tâm lý nếu nhập vào), metadata sử dụng hệ thống. |
| Nhu cầu human review | **Cao**: giáo viên/nhà trường cần kiểm tra các nội dung AI tạo ra ở các điểm quan trọng (chấm điểm, phản hồi học thuật, khuyến nghị năng lực) vì nguồn thực nghiệm cho thấy hiệu quả phụ thuộc mạnh vào cách triển khai và guardrail, không thể coi AI là nguồn đúng tuyệt đối. |

### 2. Case study 1 — Khanmigo trong chương trình toán bổ trợ ở trường công Tennessee (Mỹ)

#### Brief Case

- Tổ chức / sản phẩm AI: Khan Academy — **Khanmigo** (AI tutor tích hợp trong Khan Academy).
- Thời gian, địa điểm / bối cảnh: Thí nghiệm trường học kéo dài 2 năm tại bang Tennessee, Mỹ (khối middle school).
- AI được dùng để làm gì: Hỗ trợ học sinh trong các tiết toán bổ trợ hằng ngày (gợi ý học tập, đối thoại hỗ trợ giải bài).
- Vấn đề hoặc sự kiện đáng chú ý: Tỷ lệ “đã thử” rất cao nhưng mức sử dụng sâu thấp; hiệu quả học tập có tăng nhưng phụ thuộc mạnh vào mức độ tương tác thực tế của học sinh với tutor.
- Số liệu có nguồn: Nghiên cứu báo cáo can thiệp ở **18 trường**; **96%** học sinh ở nhóm can thiệp đã thử Khanmigo ít nhất một lần; mức cải thiện trung bình khoảng **1,3 bậc phân vị quốc gia mỗi học kỳ**; học sinh trung vị chỉ nhắn với AI khoảng **1/3** số buổi luyện tập và dùng AI ở khoảng **17%** tình huống sau khi làm sai (theo báo cáo nghiên cứu).
- Nguồn:  
  1) Guryan, Kim, Ludwig, Morrison, et al. (2026), **One Click Away: AI Tutoring with Khanmigo in a Two-Year School Experiment**, NBER Working Paper 35620 — https://www.nber.org/papers/w35620 (các phần mô tả thiết kế thí nghiệm, mức sử dụng và ước lượng tác động).  
  2) Hechinger Report (tóm tắt nghiên cứu, dẫn lại các chỉ số sử dụng và tác động) — *Proof Points: Khanmigo math AI tutor* — https://hechingerreport.org/proof-points-khanmigo-math-ai-tutor/
- Phân biệt bằng chứng và nhận định: **Nguồn xác nhận** các số liệu về phạm vi thử nghiệm, mức dùng và kết quả học tập trung bình. **Nhận định của tôi**: rủi ro chính ở case này là over-reliance không đúng chỗ (hoặc dùng hời hợt), làm AI chưa phát huy vai trò “tutor” sâu; đây là diễn giải từ dữ liệu hành vi sử dụng, không phải kết luận nhân quả duy nhất.

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Khi học sinh gặp lỗi trong bài toán và quyết định có dùng/không dùng gợi ý AI để sửa hiểu biết ngay tại thời điểm học. |
| Stakeholder bị ảnh hưởng | Học sinh (trực tiếp), giáo viên (chịu trách nhiệm chất lượng học), nhà trường/phụ huynh (kỳ vọng cải thiện kết quả). |
| Failure mode | Over-reliance / under-engagement: hoặc tin gợi ý AI mà không kiểm chứng, hoặc chỉ bấm dùng cho có nhưng không đối thoại học thuật đủ sâu. |
| Layer bắt đầu lỗi | **UX + Grounding (giả thuyết có căn cứ gián tiếp)**: nguồn công bố hành vi sử dụng, nhưng không công bố chi tiết kiến trúc đầy đủ để kết luận chắc chắn một layer duy nhất. |
| Harm xảy ra là gì? | **Đã quan sát được**: mức tương tác thấp làm giảm tiềm năng cải thiện học tập. **Nguy cơ**: người học lệ thuộc vào gợi ý ngắn, không xây nền tảng giải quyết vấn đề độc lập. |
| Harm lens | Opportunity loss (mất cơ hội học sâu), misinformation (nếu có gợi ý sai mà không được kiểm tra). |
| Severity | Medium |
| Scale | Medium (thử nghiệm ở nhiều trường, ảnh hưởng cấp lớp/trường; không phải toàn hệ thống giáo dục). |
| Probability | Medium (hành vi dùng hời hợt đã xuất hiện trong dữ liệu sử dụng). |
| Frequency | Medium (xảy ra lặp lại theo buổi học, nhưng mức độ tùy thói quen từng lớp/học sinh). |
| Vì sao? | Tôi chấm mức trung bình vì nguồn cho thấy tác động học tập dương nhưng nhỏ-trung bình và phụ thuộc engagement; bằng chứng chưa cho thấy hậu quả nghiêm trọng tức thời, nhưng có rủi ro tích lũy về chất lượng học nếu triển khai thiếu giám sát sư phạm. |

### 3. Case study 2 — GPT-4 tutor có/không guardrail trong toán THPT (Thổ Nhĩ Kỳ)

#### Brief Case

- Tổ chức / sản phẩm AI: Hệ thống tutor dùng **GPT-4** trong nghiên cứu thực nghiệm giáo dục (so sánh giao diện “GPT Base” và “GPT Tutor” có scaffold/guardrail học tập).
- Thời gian, địa điểm / bối cảnh: Nghiên cứu thực nghiệm ngẫu nhiên với học sinh THPT tại Thổ Nhĩ Kỳ.
- AI được dùng để làm gì: Hỗ trợ làm bài và học toán qua hội thoại.
- Vấn đề hoặc sự kiện đáng chú ý: Tăng điểm ngắn hạn khi có AI, nhưng nhóm dùng bản không guardrail giảm kết quả khi rút AI (dấu hiệu “crutch effect”).
- Số liệu có nguồn: Bài nghiên cứu báo cáo gần **1.000 học sinh**; khi có AI, nhóm GPT Base tăng hiệu suất làm bài khoảng **48%**, nhóm GPT Tutor khoảng **127%**; khi bỏ AI, nhóm GPT Base thấp hơn nhóm đối chứng khoảng **17%** trong bài kiểm tra không có AI.
- Nguồn:  
  1) Bastani et al. (2024), **Generative AI Without Guardrails Can Harm Learning: Evidence from High School Math**, SSRN — https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4895486 (thiết kế RCT, kết quả theo từng điều kiện can thiệp).  
  2) Bản trình bày/tóm tắt nghiên cứu của nhóm tác giả (nếu giảng viên cần đối chiếu nhanh): https://www.mindthedrift.com/research/bastani-2024-ai-without-guardrails/
- Phân biệt bằng chứng và nhận định: **Nguồn xác nhận** chênh lệch kết quả ngắn hạn và khi rút AI giữa các nhóm thí nghiệm. **Nhận định của tôi**: rủi ro giáo dục đến từ thiết kế tương tác (cho đáp án nhanh vs ép tư duy từng bước), không phải do “AI luôn xấu”; cần cảnh giác vì bằng chứng chủ yếu trong bối cảnh toán THPT cụ thể, chưa đại diện mọi môn/hệ.

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Khi học sinh luyện bài với AI trước kỳ kiểm tra và hình thành chiến lược phụ thuộc vào trợ giúp tức thời. |
| Stakeholder bị ảnh hưởng | Học sinh (năng lực thật), giáo viên/nhà trường (đánh giá sai mức nắm kiến thức), phụ huynh. |
| Failure mode | Over-reliance; harmful advice ở mức sư phạm (AI/giao diện có thể đưa “đường tắt” thay vì củng cố hiểu biết). |
| Layer bắt đầu lỗi | **UX + Safety policy ở tầng ứng dụng** theo mô tả “guardrail/scaffold”; chưa đủ bằng chứng công khai để quy kết chi tiết vào trọng số mô hình lõi. |
| Harm xảy ra là gì? | **Đã quan sát trong nghiên cứu**: nhóm dùng bản không guardrail giảm hiệu suất khi không còn AI hỗ trợ. **Nguy cơ mở rộng**: suy giảm năng lực tự học dài hạn nếu triển khai đại trà mà không thiết kế kiểm soát phụ thuộc. |
| Harm lens | Opportunity loss, misinformation (nếu người học tiếp thu bước giải sai mà không phản biện). |
| Severity | High |
| Scale | Medium (quy mô nghiên cứu cỡ hàng trăm đến gần nghìn học sinh; chưa đủ để suy rộng cho mọi quốc gia/môn học). |
| Probability | Medium-High (đã có tín hiệu định lượng trong điều kiện thí nghiệm). |
| Frequency | Medium (xảy ra trong các phiên học dùng AI không guardrail; tần suất thực tế ngoài đời phụ thuộc cách triển khai). |
| Vì sao? | Tôi chấm Severity cao vì tác hại nhắm trực tiếp vào mục tiêu cốt lõi của giáo dục (năng lực thật khi không có trợ giúp). Tuy vậy tôi không chấm Scale “High” vì bằng chứng hiện tại vẫn theo ngữ cảnh thử nghiệm cụ thể; cần thêm nghiên cứu tái lập ở môn khác và môi trường khác. |
