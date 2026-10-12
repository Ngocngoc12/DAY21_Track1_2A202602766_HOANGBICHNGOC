# Bài phân tích rủi ro AI trong ngành Y tế

**Sinh viên:** Hoàng Bích Ngọc  
**Mã sinh viên/nhóm:** 2A202602766  
**Repository:** `Ngocngoc12/DAY21_Track1_2A202602766_HOANGBICHNGOC`  
**Ngành được chọn:** Y tế / Chăm sóc sức khỏe  

## 1. Industry Risk Snapshot

### 1.1. Lý do chọn ngành

Y tế là ngành có mức độ ảnh hưởng trực tiếp đến tính mạng, sức khỏe, quyền riêng tư và khả năng tiếp cận dịch vụ của con người. AI trong y tế có thể hỗ trợ sàng lọc, chẩn đoán, dự báo nguy cơ và phân bổ nguồn lực; tuy nhiên, lỗi của hệ thống có thể dẫn đến bỏ sót bệnh, điều trị sai, chậm cấp cứu hoặc phân biệt đối xử.

### 1.2. Đánh giá nhanh risk profile

| Tiêu chí | Mức đánh giá | Nhận xét |
|---|---:|---|
| Mức độ high-stakes | **Rất cao – 5/5** | Kết quả AI có thể ảnh hưởng đến chẩn đoán, điều trị, nhập viện và cơ hội được chăm sóc. |
| Tác hại nếu AI sai | **Rất cao – 5/5** | Có thể bỏ sót ca bệnh, báo động giả, trì hoãn điều trị, gây chi phí không cần thiết hoặc làm xấu đi chênh lệch sức khỏe. |
| Dữ liệu nhạy cảm | **Rất cao – 5/5** | Hồ sơ bệnh án, hình ảnh y tế, dữ liệu di truyền, thuốc đang dùng, thông tin bảo hiểm và dữ liệu định danh. |
| Rủi ro thiên lệch | **Cao – 4/5** | Hiệu năng có thể khác nhau theo chủng tộc, giới tính, tuổi, ngôn ngữ, điều kiện kinh tế và nơi cung cấp dữ liệu. |
| Khả năng giải thích | **Trung bình đến thấp – 2/5** | Một số mô hình khó giải thích nguyên nhân của dự đoán cho bác sĩ và người bệnh. |
| Nhu cầu human review | **Bắt buộc – 5/5** | AI chỉ nên hỗ trợ; bác sĩ/người có chuyên môn phải xác nhận các quyết định chẩn đoán và điều trị quan trọng. |
| Khả năng giám sát sau triển khai | **Cao – 4/5** | Cần theo dõi drift, tỷ lệ sai theo nhóm dân số, cảnh báo, khiếu nại và sự cố lâm sàng. |

### 1.3. Các tác hại chính cần ưu tiên

1. **Bỏ sót bệnh hoặc đánh giá thấp nguy cơ:** bệnh nhân có thể không được chuyển khám, xét nghiệm hoặc điều trị kịp thời.
2. **Báo động giả và quá tải:** quá nhiều cảnh báo không chính xác làm nhân viên y tế mất niềm tin hoặc bỏ qua cảnh báo quan trọng.
3. **Thiên lệch và phân biệt đối xử:** nếu nhãn mục tiêu hoặc dữ liệu lịch sử phản ánh bất bình đẳng, AI có thể phân bổ nguồn lực không công bằng.
4. **Xâm phạm quyền riêng tư:** dữ liệu y tế bị lộ, dùng sai mục đích hoặc chia sẻ khi chưa có sự đồng ý phù hợp.
5. **Tự động hóa quá mức:** nhân viên có thể phụ thuộc vào điểm số AI và giảm việc kiểm tra hồ sơ, triệu chứng hoặc bối cảnh thực tế.
6. **Thiếu trách nhiệm giải trình:** khi AI sai, cần xác định rõ trách nhiệm giữa nhà cung cấp phần mềm, cơ sở y tế và người sử dụng.

### 1.4. Nguyên tắc kiểm soát đề xuất

- Chỉ dùng AI trong đúng phạm vi đã được đánh giá và phê duyệt.
- Xác nhận độc lập các kết quả có ảnh hưởng đến chẩn đoán, điều trị hoặc phân bổ nguồn lực.
- Kiểm thử trước triển khai theo từng nhóm bệnh nhân và từng cơ sở y tế.
- Công khai mục đích sử dụng, giới hạn, dữ liệu đầu vào và cách xử lý khi AI không chắc chắn.
- Theo dõi định kỳ false negative, false positive và chênh lệch hiệu năng giữa các nhóm.
- Có cơ chế tạm dừng hoặc chuyển sang quy trình thủ công khi hệ thống hoạt động bất thường.

---

## 2. Brief Case Studies

### Case 1 – Epic Sepsis Model: dự đoán nhiễm trùng huyết trong bệnh viện

**Bối cảnh:** Epic Sepsis Model là mô hình cảnh báo sớm được triển khai rộng rãi để hỗ trợ nhận diện bệnh nhân có nguy cơ sepsis. Mục tiêu là giúp nhân viên y tế đánh giá sớm và can thiệp nhanh.

**Số liệu chính:** Một nghiên cứu xác nhận độc lập tại Michigan Medicine công bố trên *JAMA Internal Medicine* cho thấy mô hình có hiệu năng thấp hơn kỳ vọng trong môi trường thực tế. Mô hình đạt AUROC khoảng **0,63**, có giá trị dự đoán dương khoảng **12%** và bỏ sót khoảng **hai phần ba** các ca sepsis trong mẫu nghiên cứu. Kết quả cho thấy mô hình cần được xác nhận tại địa phương trước khi được tin cậy trong quy trình lâm sàng.

**Phân tích:**

- Mô hình có thể tạo nhiều cảnh báo giả, gây alert fatigue.
- Nếu điểm số thấp làm nhân viên bỏ qua bệnh nhân, hậu quả của false negative có thể rất nghiêm trọng.
- Hiệu năng trong dữ liệu bệnh viện khác có thể không giống hiệu năng khi triển khai tại cơ sở mới.
- Human review phải là bước bắt buộc; cảnh báo không được thay thế đánh giá lâm sàng.

**Nguồn:**
- Wong A, et al. *External Validation of a Widely Implemented Proprietary Sepsis Prediction Model in Hospitalized Patients*. JAMA Internal Medicine, 2021. [JAMA Network](https://jamanetwork.com/journals/jamainternalmedicine/fullarticle/2781307)
- [NHLBI/NIH – Widely used sepsis prediction tool is less effective than expected](https://www.nhlbi.nih.gov/news/2021/widely-used-sepsis-prediction-tool-less-effective-michigan-doctors-thought)

### Case 2 – Optum/Impact Pro: thuật toán phân bổ hỗ trợ chăm sóc và thiên lệch chủng tộc

**Bối cảnh:** Một thuật toán được dùng để xác định bệnh nhân có thể hưởng lợi từ các chương trình chăm sóc bổ sung. Thuật toán sử dụng chi phí chăm sóc y tế dự kiến làm biến đại diện cho nhu cầu sức khỏe.

**Số liệu chính:** Nghiên cứu đăng trên *Science* năm 2019 cho thấy tại cùng một mức điểm rủi ro, bệnh nhân Black có tình trạng bệnh nặng hơn bệnh nhân White. Nếu sửa cách chọn nhãn mục tiêu, tỷ lệ bệnh nhân Black được xác định để nhận hỗ trợ đặc biệt có thể tăng từ **17,7% lên 46,5%**.

**Phân tích:**

- Thuật toán không nhất thiết dùng biến chủng tộc trực tiếp nhưng vẫn tạo chênh lệch do dùng **chi phí** làm đại diện cho **nhu cầu sức khỏe**.
- Chi phí thấp hơn trong dữ liệu lịch sử có thể phản ánh việc tiếp cận chăm sóc không bình đẳng, chứ không phải bệnh nhân ít cần hỗ trợ hơn.
- Đây là ví dụ về proxy discrimination: biến tưởng như trung lập vẫn có thể tạo tác động khác nhau giữa các nhóm.
- Cần đánh giá fairness theo outcome lâm sàng và nhu cầu thực tế, không chỉ theo độ chính xác dự đoán chi phí.

**Nguồn:**
- Obermeyer Z, et al. *Dissecting racial bias in an algorithm used to manage the health of populations*. Science, 2019. [PubMed](https://pubmed.ncbi.nlm.nih.gov/31649194/)
- [Science News – A health care algorithm’s bias disproportionately hurts Black people](https://www.sciencenews.org/article/bias-common-health-care-algorithm-hurts-black-patients)

### Case 3 – IDx-DR: AI tự động phát hiện bệnh võng mạc tiểu đường

**Bối cảnh:** IDx-DR là hệ thống AI phân tích ảnh võng mạc để phát hiện bệnh võng mạc tiểu đường ở mức cần chuyển khám. Hệ thống hướng tới việc đưa sàng lọc chuyên khoa đến các cơ sở chăm sóc ban đầu.

**Số liệu chính:** Trong thử nghiệm then chốt với khoảng **900 người** mắc tiểu đường, hệ thống đạt độ nhạy **87,2%**, độ đặc hiệu **90,7%** và tỷ lệ ảnh có thể phân tích **96,1%** đối với bệnh võng mạc trên mức nhẹ. Hệ thống được FDA cho phép sử dụng trong phạm vi được chỉ định.

**Phân tích:**

- Đây là ví dụ tích cực về việc AI có thể mở rộng khả năng sàng lọc ở nơi thiếu bác sĩ chuyên khoa.
- Tuy nhiên, độ nhạy 87,2% vẫn có nghĩa là một số ca dương tính có thể bị bỏ sót.
- Chất lượng ảnh, thiết bị chụp, nhóm dân số và điều kiện triển khai có thể làm thay đổi hiệu năng.
- Kết quả “không phát hiện” không nên được hiểu là chắc chắn không có bệnh khi bệnh nhân có triệu chứng hoặc yếu tố nguy cơ cao.
- Cần có quy trình chuyển bác sĩ chuyên khoa, xử lý ảnh không đạt chất lượng và theo dõi các ca bị bỏ sót.

**Nguồn:**
- Abràmoff MD, et al. *Pivotal trial of an autonomous AI-based diagnostic system for detection of diabetic retinopathy in primary care offices*. npj Digital Medicine, 2018. [Nature](https://www.nature.com/articles/s41746-018-0040-6)
- [PubMed – Pivotal trial of an autonomous AI-based diagnostic system](https://pubmed.ncbi.nlm.nih.gov/31304320/)

---

## 3. Harm Map Worksheet

### Worksheet 1 – Epic Sepsis Model

| Trường | Phân tích |
|---|---|
| AI đang làm gì? | Tính điểm nguy cơ và phát cảnh báo bệnh nhân có khả năng phát triển sepsis. |
| Ai có thể bị ảnh hưởng? | Bệnh nhân nhập viện, bác sĩ, điều dưỡng, đội cấp cứu và bệnh viện. |
| Tác hại trực tiếp | Bỏ sót sepsis, chậm điều trị, hoặc phát cảnh báo giả dẫn đến xét nghiệm/can thiệp không cần thiết. |
| Tác hại gián tiếp | Alert fatigue, mất niềm tin vào hệ thống, tăng chi phí và phân tán nguồn lực. |
| Nhóm dễ bị ảnh hưởng hơn | Bệnh nhân có biểu hiện không điển hình, bệnh nền phức tạp, người cao tuổi hoặc nhóm ít đại diện trong dữ liệu huấn luyện. |
| Điểm phát sinh rủi ro | Dữ liệu đầu vào, ngưỡng cảnh báo, thay đổi quy trình bệnh viện và cách nhân viên diễn giải điểm số. |
| Mức độ nghiêm trọng | Rất cao vì false negative có thể liên quan đến trì hoãn cấp cứu. |
| Khả năng xảy ra | Trung bình đến cao nếu chưa xác nhận tại địa phương. |
| Kiểm soát cần có | Local validation, giám sát false negative/positive, cảnh báo có giải thích, bác sĩ xác nhận và quy trình fallback thủ công. |
| Người chịu trách nhiệm | Bệnh viện, nhóm lâm sàng, nhà cung cấp mô hình và bộ phận quản trị AI. |

### Worksheet 2 – Optum/Impact Pro

| Trường | Phân tích |
|---|---|
| AI đang làm gì? | Xếp hạng bệnh nhân theo nguy cơ để xác định ai có thể nhận hỗ trợ chăm sóc bổ sung. |
| Ai có thể bị ảnh hưởng? | Bệnh nhân, nhân viên quản lý ca, chương trình hỗ trợ và các nhóm dân cư khác nhau. |
| Tác hại trực tiếp | Bệnh nhân có nhu cầu cao nhưng bị điểm thấp có thể không được giới thiệu chương trình hỗ trợ. |
| Tác hại gián tiếp | Củng cố bất bình đẳng chăm sóc sức khỏe và làm sai lệch phân bổ nguồn lực. |
| Nhóm dễ bị ảnh hưởng hơn | Bệnh nhân Black và các nhóm có lịch sử tiếp cận dịch vụ y tế không bình đẳng. |
| Điểm phát sinh rủi ro | Chọn chi phí làm proxy cho nhu cầu; dữ liệu lịch sử phản ánh bất bình đẳng xã hội. |
| Mức độ nghiêm trọng | Cao vì ảnh hưởng đến cơ hội nhận chăm sóc và hỗ trợ sức khỏe. |
| Khả năng xảy ra | Cao nếu chỉ kiểm tra accuracy tổng thể mà không kiểm tra fairness theo nhóm. |
| Kiểm soát cần có | Dùng outcome sức khỏe phù hợp hơn, audit theo nhóm, kiểm tra equal opportunity, rà soát thủ công các trường hợp biên và công khai proxy được sử dụng. |
| Người chịu trách nhiệm | Nhà cung cấp thuật toán, đơn vị chi trả/bệnh viện và hội đồng công bằng dữ liệu. |

### Worksheet 3 – IDx-DR

| Trường | Phân tích |
|---|---|
| AI đang làm gì? | Phân tích ảnh võng mạc và đưa ra kết quả phát hiện bệnh cần chuyển khám. |
| Ai có thể bị ảnh hưởng? | Người mắc tiểu đường, nhân viên chăm sóc ban đầu, bác sĩ mắt và cơ sở triển khai. |
| Tác hại trực tiếp | False negative làm trì hoãn khám mắt; false positive làm tăng số lượt chuyển khám và lo lắng. |
| Tác hại gián tiếp | Phụ thuộc quá mức vào kết quả “không phát hiện”, đặc biệt khi ảnh kém chất lượng hoặc nhóm bệnh nhân khác dữ liệu thử nghiệm. |
| Nhóm dễ bị ảnh hưởng hơn | Người có ảnh khó chụp, bệnh mắt khác, thiết bị khác chuẩn, hoặc ít được đại diện trong dữ liệu đánh giá. |
| Điểm phát sinh rủi ro | Chất lượng ảnh, ngưỡng phân loại, khác biệt quần thể và thiếu quy trình theo dõi sau sàng lọc. |
| Mức độ nghiêm trọng | Cao vì bỏ sót bệnh có thể dẫn đến mất thị lực nếu không được điều trị. |
| Khả năng xảy ra | Trung bình; thử nghiệm cho kết quả tốt nhưng hiệu năng thực tế cần được giám sát liên tục. |
| Kiểm soát cần có | Từ chối ảnh không đạt chất lượng, chuyển bác sĩ với ca dương tính/không chắc chắn, kiểm tra hiệu năng theo nhóm và nhắc lịch khám định kỳ. |
| Người chịu trách nhiệm | Cơ sở y tế, nhân viên thực hiện chụp ảnh, nhà cung cấp hệ thống và bác sĩ tiếp nhận ca chuyển khám. |

---

## 4. Kết luận

Qua ba case study, AI trong y tế có thể tạo giá trị rõ ràng nhưng không nên được xem là công cụ thay thế hoàn toàn chuyên môn con người. Ba rủi ro nổi bật là **sai số lâm sàng**, **thiên lệch do proxy/dữ liệu lịch sử** và **khoảng cách giữa hiệu năng thử nghiệm với hiệu năng khi triển khai thực tế**.

Khuyến nghị chung là áp dụng mô hình **human-in-the-loop**: AI đưa ra tín hiệu hỗ trợ, còn người có chuyên môn chịu trách nhiệm xác minh và quyết định. Mỗi hệ thống cần được đánh giá trước triển khai, kiểm tra fairness, theo dõi sau triển khai, ghi nhận sự cố và có phương án chuyển về quy trình thủ công.

## Tài liệu tham khảo

1. Wong A, et al. *External Validation of a Widely Implemented Proprietary Sepsis Prediction Model in Hospitalized Patients*. JAMA Internal Medicine, 2021. https://jamanetwork.com/journals/jamainternalmedicine/fullarticle/2781307
2. Obermeyer Z, et al. *Dissecting racial bias in an algorithm used to manage the health of populations*. Science, 2019. https://pubmed.ncbi.nlm.nih.gov/31649194/
3. Abràmoff MD, et al. *Pivotal trial of an autonomous AI-based diagnostic system for detection of diabetic retinopathy in primary care offices*. npj Digital Medicine, 2018. https://www.nature.com/articles/s41746-018-0040-6
4. U.S. National Heart, Lung, and Blood Institute. *Widely used sepsis prediction tool is less effective than Michigan doctors thought*. https://www.nhlbi.nih.gov/news/2021/widely-used-sepsis-prediction-tool-less-effective-michigan-doctors-thought
5. FDA. *Artificial Intelligence-Enabled Medical Devices*. https://www.fda.gov/medical-devices/digital-health-center-excellence/artificial-intelligence-enabled-medical-devices
