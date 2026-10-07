# Lab 21 — Phân tích rủi ro AI qua case study thực tế

- Họ và tên: Hoàng Anh Tài
- MSSV / mã học viên: 2A202602612
- Lớp: H201
- Ngành đã chọn: Giáo dục / AI tutor

---

### 1. Industry Risk Snapshot

| Nội dung | Đánh giá của tôi và lý do |
| --- | --- |
| Những tác hại chính có thể xảy ra | **1. Tiếp nhận tri thức sai lệch (Epistemic Harm):** AI tutor tạo ảo giác (hallucination), giải sai bài toán hoặc cung cấp sai sự thật khiến học sinh hiểu sai bản chất kiến thức.<br>**2. Suy giảm năng lực tư duy độc lập (Cognitive Crutch):** Học sinh lạm dụng AI giải bài trực tiếp, triệt tiêu quá trình tư duy nỗ lực (productive struggle), dẫn đến suy giảm năng lực khi kiểm tra độc lập.<br>**3. Lệ thuộc tâm lý & nội dung không phù hợp (Psychological Harm):** Học sinh vị thành niên tin tưởng mù quáng vào chatbot (nhân hóa AI), có nguy cơ tiếp xúc với phản hồi lệch chuẩn.<br>**4. Đánh giá sai lệch và bất công học đường (Evaluation Harm):** Thuật toán AI chấm điểm tự động mắc lỗi kỹ thuật hoặc thiên kiến làm sai lệch kết quả đánh giá học sinh.<br>*Đối tượng bị ảnh hưởng:* Học sinh (đặc biệt là lứa tuổi K-12), giáo viên, phụ huynh và cơ sở giáo dục. |
| Mức độ high-stakes | **Phụ thuộc vào Use Case cụ thể (Medium to High):**<br>- **Trung bình (Medium)** đối với AI tutor đóng vai trò kèm cặp, hỗ trợ học tập và giải bài tập hàng ngày (tác động nhận thức và kiến thức nền tảng, có thể phát hiện và điều chỉnh qua can thiệp sư phạm).<br>- **Cao (High)** khi AI được sử dụng trong đánh giá chuẩn hóa, chấm điểm thi, xếp loại hoặc ra các quyết định ảnh hưởng trực tiếp đến bằng cấp, điều kiện tốt nghiệp và cơ hội học tập tương lai của học sinh. |
| Dữ liệu nhạy cảm có thể được sử dụng | **Dữ liệu trẻ vị thành niên và hồ sơ học tập cá nhân (Tuân thủ FERPA / COPPA):**<br>- *Dữ liệu định danh cá nhân học sinh (PII vị thành niên):* Họ tên, ngày sinh, trường lớp, hình ảnh khuôn mặt/webcam, giọng nói.<br>- *Dữ liệu năng lực và tiến độ học tập:* Điểm số, lịch sử bài làm sai, điểm yếu nhận thức, nhật ký giải bài tập.<br>- *Dữ liệu hội thoại và biểu hiện hành vi:* Lịch sử câu hỏi thắc mắc, tâm tư tình cảm hoặc khó khăn tâm lý mà học sinh bộc lộ với trợ lý AI trong các phiên đối thoại 1-1. |
| Nhu cầu human review | **Cao (High):**<br>*Ai kiểm tra:* Giáo viên bộ môn, chuyên gia sư phạm và phụ huynh học sinh.<br>*Ở bước nào:*<br>1. *Tiền kiểm (Pre-deployment):* Thẩm định giáo trình, hệ thống prompt/guardrails và độ chính xác của cơ sở tri thức trước khi đưa vào lớp học.<br>2. *Giám sát thời gian thực (Real-time monitoring):* Dashboard cảnh báo tự động khi AI gặp lỗi tính toán hoặc khi học sinh hỏi các chủ đề bất thường/nhạy cảm.<br>3. *Hậu kiểm (Post-assessment):* Giáo viên trực tiếp kiểm tra và phê duyệt đối với các quyết định chấm điểm, xếp loại có ảnh hưởng đáng kể đến kết quả học tập của học sinh.<br>*Vì sao:* Mô hình AI mang bản chất suy luận xác suất thống kê nên không thể cam đoan 100% tính đúng đắn; con người vẫn cần chịu trách nhiệm giám sát và phê duyệt cuối cùng đối với các quyết định có ảnh hưởng đáng kể đến kết quả học tập và quyền lợi của học sinh. |

---

### 2. Case study 1 — Nghiên cứu thực nghiệm Wharton (UPenn) về việc AI Tutor làm giảm năng lực học sinh (Bastani et al., 2024)

#### Brief Case

- Tổ chức / sản phẩm AI: Trường Kinh doanh Wharton (Đại học Pennsylvania) / Mô hình trợ lý học tập AI dựa trên GPT-4 (gồm 2 phiên bản thử nghiệm: "GPT Base" - giải bài trực tiếp và "GPT Tutor" - gợi ý sư phạm có rào chắn).
- Thời gian, địa điểm / bối cảnh: Năm học 2023–2024, thử nghiệm kiểm soát ngẫu nhiên (RCT) trên gần 1.000 học sinh THPT (mẫu nghiên cứu công bố gồm 993 học sinh các lớp 9, 10, 11) tại Thổ Nhĩ Kỳ trong môn Toán.
- AI được dùng để làm gì: Đóng vai trò gia sư AI (AI Tutor) hỗ trợ học sinh giải các bài toán trung học theo thời gian thực trong các buổi tự luyện tập.
- Vấn đề hoặc sự kiện đáng chú ý: Nghiên cứu phát hiện hiện tượng "chiếc nạng nhận thức" (Cognitive crutch): Khi được dùng AI tutor giải bài trực tiếp, học sinh làm bài tập thực hành rất nhanh và đúng nhiều hơn, nhưng bị mất đi quá trình tư duy nỗ lực (productive struggle). Khi bước vào bài kiểm tra độc lập (không còn AI), năng lực giải quyết vấn đề của học sinh bị suy giảm nghiêm trọng so với nhóm không dùng AI.
- Số liệu có nguồn: Trong bài kiểm tra độc lập không có AI hỗ trợ, nhóm học sinh từng sử dụng GPT Base làm bài **kém hơn 17%** so với nhóm đối chứng (học sinh không bao giờ dùng AI), dù trước đó trong lúc luyện tập có AI, nhóm GPT Base giải đúng nhiều hơn 48% (theo nghiên cứu thực nghiệm của Bastani et al., Đại học Pennsylvania, công bố tháng 07/2024).
- Nguồn: Hamsa Bastani, Osbert Bastani, Alp Sungu, Haosen Ge, Özge Kabakcı, Rei Mariman — *"Generative AI Can Harm Learning"* — Wharton School, University of Pennsylvania / SSRN — Ngày công bố: 16/07/2024 — URL: https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4880692 — Trang 1–18.
- Phân biệt bằng chứng và nhận định:
  - *Điều nguồn xác nhận (Evidence):* Thử nghiệm thực nghiệm chứng minh học sinh dùng phiên bản GPT Base (giải bài trực tiếp) đạt điểm thi độc lập thấp hơn 17% so với nhóm không dùng AI; học sinh có xu hướng ỷ lại và mắc lỗi số học nhiều hơn vì tin vào kết luận của AI.
  - *Điều tôi suy luận hoặc còn chưa rõ (Inference):* Đây là nguy cơ suy giảm nhận thức có thể lan rộng nếu các trường học triển khai AI bừa bãi mà không kèm phương pháp sư phạm gợi mở (Socratic scaffolding); tuy nhiên nghiên cứu tập trung vào môn Toán cấp THPT tại Thổ Nhĩ Kỳ, chưa rõ mức độ tác động cụ thể đối với các môn khoa học xã hội hay cấp học khác.

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Học sinh THPT sử dụng trợ lý AI trong các buổi luyện tập toán học độc lập tại nhà hoặc trên lớp mà không có giáo viên hướng dẫn, đặt câu hỏi yêu cầu AI cung cấp ngay lời giải hoàn chỉnh cho bài tập khó. |
| Stakeholder bị ảnh hưởng | - **Người dùng trực tiếp:** Học sinh THPT (bị suy giảm năng lực tư duy toán học độc lập và mất thói quen tự giải bài).<br>- **Bên liên quan:** Giáo viên bộ môn (bị che mờ mức độ hiểu bài thực tế của học sinh), phụ huynh và nhà trường (chịu ảnh hưởng về chất lượng giáo dục thực chất). |
| Failure mode | **Over-reliance / Cognitive crutch**:<br>Người dùng tin AI quá mức và bỏ kiểm tra (Over-reliance); học sinh sử dụng AI giải bài trực tiếp như một "chiếc nạng nhận thức" để hoàn thành bài tập nhanh, bỏ qua nỗ lực tư duy độc lập (productive struggle). |
| Layer bắt đầu lỗi | **Grounding / Instruction layer (Inferred)**:<br>Thiếu pedagogical guardrails và problem-specific scaffolding trong phiên bản GPT Base (so với phiên bản GPT Tutor được thiết kế gợi ý từng bước); giao diện và cách hướng dẫn trực tiếp làm học sinh dễ dàng lấy ngay đáp án thay vì phải tự suy nghĩ. Nguồn nghiên cứu không công bố chi tiết kiến trúc kỹ thuật nội bộ của hệ thống. |
| Harm xảy ra là gì? | - **Observed harm (Ghi nhận trong nghiên cứu):** Nhóm học sinh trung học sử dụng GPT Base bị **suy giảm 17% điểm số bài kiểm tra độc lập** (không có AI) so với nhóm đối chứng không dùng AI.<br>- **Potential harm / Inference (Nguy cơ suy luận):** Học sinh có nguy cơ bị hổng kiến thức toán căn bản lâu dài và mất năng lực tự giải quyết vấn đề khi đối mặt với kỳ thi độc lập nếu lạm dụng AI giải bài tập mà thiếu định hướng sư phạm. |
| Harm lens | **opportunity loss** *(Mất cơ hội rèn luyện tư duy phản biện độc lập, mất cơ hội phát triển năng lực tư duy toán học tự thân và đạt kết quả thực chất trong các kỳ thi không có công nghệ trợ giúp).* |
| Severity | **Medium** *(Hậu quả gây suy giảm năng lực nhận thức đo lường được là 17% điểm số trong bối cảnh AI tutor môn toán; không gây tổn hại thể chất nguy kịch và có thể can thiệp khắc phục qua điều chỉnh phương pháp sư phạm).* |
| Scale | **Gần 1.000 học sinh THPT** (chính xác 993 học sinh trong mẫu nghiên cứu RCT tại Thổ Nhĩ Kỳ theo Bastani et al., 2024); phạm vi tiềm năng ở mức **High** (hàng triệu học sinh) nếu các trường học triển khai AI tutor thiếu rào chắn sư phạm trên diện rộng. |
| Probability | **High (Đánh giá định tính của tôi):** Học sinh có xu hướng ưu tiên các chiến lược tốn ít nỗ lực nhận thức hơn (lower-effort strategies) khi hệ thống cung cấp câu trả lời sẵn một cách dễ dàng; trong nghiên cứu, phần lớn học sinh nhóm GPT Base đều phụ thuộc vào lời giải trực tiếp của AI. |
| Frequency | **High (Đánh giá định tính của tôi):** Lặp lại thường xuyên theo từng buổi học sinh làm bài tập về nhà môn toán suốt năm học nếu công cụ không bị giới hạn. |
| Vì sao? | - *Lý do chọn Mode & Layer:* Chọn `Over-reliance / Cognitive crutch` vì đây là finding cốt lõi được bài báo chứng minh khi học sinh phụ thuộc vào AI giải bài sẵn; chọn `Grounding / Instruction layer (Inferred)` vì sự khác biệt giữa GPT Base và GPT Tutor nằm ở prompt sư phạm và scaffolding.<br>- *Lý do chọn Harm & Lens:* Chọn `opportunity loss` vì sự ỷ lại làm học sinh mất cơ hội trui rèn năng lực nhận thức tự thân.<br>- *Căn cứ mức độ:* Số liệu giảm 17% điểm thi độc lập và tăng 48% khi có AI là kết quả định lượng đối chứng của ĐH Pennsylvania; Severity chọn `Medium` vì tác hại nhận thức nằm trong phạm vi môn học và có thể khắc phục. |

---

### 3. Case study 2 — Lỗi ảo giác toán học và sai lệch sư phạm của trợ lý học tập Khanmigo (The Wall Street Journal & Khan Academy, 2024)

#### Brief Case

- Tổ chức / sản phẩm AI: Khan Academy / Trợ lý học tập ảo thông minh Khanmigo (xây dựng trên nền tảng OpenAI GPT-4).
- Thời gian, địa điểm / bối cảnh: Tháng 02/2024, trong quá trình triển khai thí điểm tại nhiều học khu công lập tại Hoa Kỳ (như Newark - New Jersey, Hobart - Indiana...).
- AI được dùng để làm gì: Đóng vai trò gia sư AI 1-1 hỗ trợ học sinh học tập theo phương pháp gợi mở Socratic môn Toán và Khoa học.
- Vấn đề hoặc sự kiện đáng chú ý: Cuộc điều tra độc lập của báo *The Wall Street Journal* phát hiện Khanmigo thường xuyên mắc lỗi số học cơ bản (như phép trừ đơn giản 343 - 17, tính căn bậc hai, làm tròn số), tự tin khẳng định lời giải sai và không tự phát hiện lỗi ngay cả khi học sinh yêu cầu kiểm tra lại; thậm chí nhầm lẫn đúng - sai trong bài toán hình học định lý Pythagoras.
- Số liệu có nguồn: Theo xác nhận công khai của Sal Khan (CEO Khan Academy) và báo cáo từ WSJ/Edutopia, tỷ lệ lỗi (error rate) của Khanmigo trong các bài toán nâng cao ban đầu ở mức **6% đến 7%**, trước khi tổ chức này phải tích hợp công cụ máy tính số học (symbolic calculator) để giảm tỷ lệ lỗi xuống còn khoảng **3%** vào năm 2024.
- Nguồn:
  1. Matt Barnum — *"We Tested an AI Tutor for Kids. It Struggled With Basic Math"* — The Wall Street Journal — Ngày công bố: 16/02/2024 — URL: https://www.wsj.com/tech/personal-tech/khan-academy-khanmigo-ai-tutor-math-ee0f0550.
  2. Phát biểu của Sal Khan (CEO Khan Academy) về tỷ lệ lỗi 6–7% giảm xuống ~3% sau khi tích hợp công cụ tính toán (được ghi nhận trên Edutopia / IBL News / LA School Report, 2024).
- Phân biệt bằng chứng và nhận định:
  - *Điều nguồn xác nhận (Evidence):* Khanmigo mắc các lỗi tính toán số học tiểu học và logic cụ thể; tỷ lệ lỗi ban đầu là 6%–7% và Khan Academy đã can thiệp kỹ thuật bổ sung máy tính để giảm lỗi xuống ~3%.
  - *Điều tôi suy luận hoặc còn chưa rõ (Inference):* Học sinh nhỏ tuổi chưa đủ năng lực thẩm định có nguy cơ tiếp thu sai kiến thức căn bản nếu tin tưởng mù quáng vào AI; mức độ ảnh hưởng điểm số thực tế trên diện rộng của từng học khu chưa được công bố định lượng cụ thể.

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Học sinh lứa tuổi tiểu học và THCS đối thoại 1-1 với gia sư AI Khanmigo để học các bài toán số học, làm tròn, căn bậc hai hoặc hình học mà không có giáo viên hoặc phụ huynh bên cạnh giám sát tính đúng đắn. |
| Stakeholder bị ảnh hưởng | - **Người dùng trực tiếp:** Học sinh nhỏ tuổi (tiếp thu sai khái niệm toán học nền tảng).<br>- **Bên liên quan:** Phụ huynh và giáo viên (mất thêm công sức rà soát và đính chính kiến thức sai); tổ chức Khan Academy (tổn hại uy tín thương hiệu giáo dục). |
| Failure mode | **Hallucination / Inaccurate mathematical reasoning**:<br>AI sinh câu trả lời số học sai (như phép trừ căn bản 343 - 17, căn bậc hai, làm tròn) nhưng tự tin trình bày như thể hoàn toàn chính xác (Hallucination / Overconfidence), đồng thời gặp lỗi không tự phát hiện sai sót khi được học sinh yêu cầu kiểm tra lại (failure to self-correct). |
| Layer bắt đầu lỗi | **Model (Inferred limitation) / Grounding (Hypothesis)**:<br>- *Model (Inferred limitation):* Giới hạn suy luận số học đáng tin cậy của mô hình ngôn ngữ lớn (LLM) do bản chất dự đoán token văn bản thay vì tính toán logic số học; nguồn dẫn chứng không thiết lập nguyên nhân kỹ thuật nội bộ cụ thể.<br>- *Grounding (Hypothesis / Inferred):* Giả thuyết kỹ thuật suy luận (chưa phải sự thật được chứng minh) rằng ở giai đoạn đầu hệ thống thiếu cơ chế tích hợp công cụ máy tính (calculator / code execution) để kiểm chứng phép tính trước khi sinh câu trả lời. |
| Harm xảy ra là gì? | - **Observed harm (Ghi nhận thực tế):** Học sinh nhỏ tuổi tiếp nhận lời giải số học sai lệch trong các buổi thử nghiệm thực tế do AI tính toán sai (như phép tính 343 - 17) và không tự sửa lỗi.<br>- **Potential harm / Inference (Nguy cơ suy luận):** Nguy cơ học sinh hình thành lỗ hổng nhận thức toán học căn bản và mất niềm tin vào công cụ học tập nếu không có giáo viên/phụ huynh kiểm tra chéo. |
| Harm lens | **misinformation** *(Thông tin sai lệch về mặt số học, quy tắc toán học và logic suy luận được trình bày như sự thật).* |
| Severity | **Medium** *(Gây sai lệch kiến thức nền tảng ở lứa tuổi đang định hình nhận thức; không gây tổn hại thể chất nguy kịch, đòi hỏi con người can thiệp sư phạm để đính chính).* |
| Scale | **Nhiều học khu công lập tại Hoa Kỳ (Multiple U.S. school districts)**: Triển khai thí điểm tại các học khu đối tác của Khan Academy (như Newark - New Jersey, Hobart - Indiana...); số lượng học sinh thực tế bị ảnh hưởng trực tiếp bởi các câu trả lời sai không được nguồn công bố cụ thể. |
| Probability | **Medium** *(Tỷ lệ lỗi đo được trong các bài toán nâng cao ban đầu là **6% đến 7%** theo phát biểu của CEO Sal Khan; sau đó giảm xuống khoảng **3%** khi tích hợp máy tính).* |
| Frequency | **Medium (Đánh giá định tính của tôi):** Xuất hiện định kỳ mỗi khi học sinh gặp các bài toán liên quan đến tính toán số học nhiều chữ số hoặc hình học trừu tượng. |
| Vì sao? | - *Lý do chọn Mode & Layer:* Chọn `Hallucination` vì mô hình đưa ra kết quả tính toán sai nhưng trình bày tự tin; chọn `Model (Inferred)` vì giới hạn suy luận số học của LLM. Đánh dấu rõ `Hypothesis / Inferred` cho giả thuyết về layer Grounding vì nguồn chưa công bố chi tiết pipeline nội bộ.<br>- *Lý do chọn Harm & Lens:* Chọn `misinformation` vì tác hại cốt lõi là việc cung cấp thông tin số học không đúng sự thật.<br>- *Căn cứ mức độ:* Số liệu tỷ lệ lỗi 6%–7% do đích thân nhà sáng lập Sal Khan xác nhận; bài phóng sự của The Wall Street Journal (02/2024) trực tiếp chứng minh các trường hợp lỗi tính toán thực tế. |

---

### 4. Case study 3 (Bổ sung) — Sự cố thuật toán AI chấm điểm bài luận làm sai lệch kết quả thi của 1.400 học sinh (Massachusetts DESE & Cognia, 2025)

#### Brief Case

- Tổ chức / sản phẩm AI: Sở Giáo dục Tiểu học và Trung học Massachusetts (DESE) & Đơn vị khảo thí Cognia / Hệ thống AI chấm điểm tự động bài thi tiêu chuẩn MCAS (Massachusetts Comprehensive Assessment System).
- Thời gian, địa điểm / bối cảnh: Tháng 10/2025, áp dụng cho kỳ thi chuẩn hóa MCAS của học sinh trên toàn bang Massachusetts, Hoa Kỳ.
- AI được dùng để làm gì: Tự động chấm điểm phần thi viết luận (essay automated scoring) của học sinh nhằm giảm tải thời gian và chi phí khảo thí.
- Vấn đề hoặc sự kiện đáng chú ý: Hệ thống AI chấm bài gặp sự cố kỹ thuật (technical glitch), tự động gán điểm 0 hàng loạt cho các bài viết luận đạt chuẩn của học sinh. Lỗi được phát hiện khi một giáo viên tại học khu Lowell rà soát trước dữ liệu của học sinh và báo cáo bất thường, giúp cơ quan chức năng can thiệp kịp thời trước khi công bố điểm chính thức và tổ chức chấm lại toàn bộ.
- Số liệu có nguồn: Khoảng **1.400 bài luận** của học sinh tại gần **200 học khu** trên toàn bang Massachusetts bị AI chấm sai điểm (trong tổng số khoảng 750.000 bài thi luận MCAS toàn bang), theo thông cáo của DESE và báo cáo của các cơ quan báo chí (Patch / Indiatimes, 10/2025).
- Nguồn: Michael O'Connell — *"AI Glitch Results In 1,400 MCAS Essays Scored Incorrectly: DESE"* — Báo điện tử Patch / Massachusetts DESE — Ngày công bố: 07/10/2025 — URL: https://patch.com/massachusetts/across-ma/ai-glitch-results-1-400-mcas-essays-scored-incorrectly-dese.
- Phân biệt bằng chứng và nhận định:
  - *Điều nguồn xác nhận (Evidence):* Khoảng 1.400 bài luận bị gán điểm sai do lỗi kỹ thuật của hệ thống AI tại gần 200 học khu; cơ chế hậu kiểm của giáo viên con người đã kịp thời phát hiện trước khi công bố điểm chính thức và DESE đã tổ chức chấm lại toàn bộ.
  - *Điều tôi suy luận hoặc còn chưa rõ (Inference):* Đây là rủi ro điển hình của việc thiếu cơ chế kiểm định ngoại lệ (anomaly detection); nếu giáo viên không phát hiện kịp thời, học sinh có nguy cơ bị ghi nhận điểm số sai lệch gây ảnh hưởng đến kết quả đánh giá học bạ.

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Hệ thống AI tự động xử lý và gán điểm số hàng loạt cho các bài thi viết luận chuẩn hóa MCAS của học sinh, trước khi kết quả được chốt gửi về các học khu và ghi nhận vào học bạ. |
| Stakeholder bị ảnh hưởng | - **Người dùng/đối tượng trực tiếp:** Học sinh có bài thi bị chấm điểm sai (khoảng 1.400 bài luận).<br>- **Bên liên quan:** Giáo viên bộ môn tại gần 200 học khu (phải tốn công đối soát dữ liệu bất thường); Sở Giáo dục Massachusetts (DESE) và công ty khảo thí Cognia (chịu trách nhiệm pháp lý và uy tín giải trình). |
| Failure mode | **Automated scoring / QA failure (Possible escalation failure — Inferred)**:<br>Sự cố kỹ thuật trong hệ thống chấm điểm tự động khiến thuật toán gán điểm 0 sai lệch cho hàng loạt bài luận đạt chuẩn; nguồn tin công khai không xác định rõ chốt bảo vệ hay quy trình escalation nội bộ nào bị lỗi. |
| Layer bắt đầu lỗi | **Safety / QA (Inferred)**:<br>Sự cố cho thấy các rào chắn kiểm thử chất lượng và lớp bảo vệ (Safety/QA) không phát hiện kịp thời bất thường phân phối điểm số (anomaly detection filter); nguyên nhân kỹ thuật chi tiết của hệ thống Cognia chưa được công bố công khai (chưa đủ bằng chứng để khẳng định lỗi ở cấp độ Model hay Pipeline). |
| Harm xảy ra là gì? | - **Observed harm (Ghi nhận thực tế):** Khoảng **1.400 bài luận của học sinh tại gần 200 học khu** bị **chấm điểm sai (nhiều bài bị gán điểm 0 bất thường)** trên hệ thống trước khi được công bố chính thức, gây tốn kém nguồn lực rà soát và chấm lại toàn bộ.<br>- **Potential harm / Inference (Nguy cơ suy luận):** Tạo nguy cơ học sinh nhận kết quả đánh giá không chính xác và ảnh hưởng đến kết quả học đường nếu lỗi kỹ thuật không được giáo viên phát hiện và đính chính kịp thời trước ngày công bố điểm chính thức. |
| Harm lens | **opportunity loss / Evaluation harm**:<br>Nguy cơ ảnh hưởng bất lợi đến kết quả đánh giá học tập và cơ hội học đường nếu điểm số sai sót không được phát hiện và sửa đổi. (Bỏ nhãn dignity loss do nguồn tài liệu không có bằng chứng ghi nhận tổn hại phẩm giá). |
| Severity | **Potential Severity: High**:<br>Mức độ nghiêm trọng tiềm năng là High vì kỳ thi chuẩn hóa bang có tính chất quyết định đối với kết quả học tập và điều kiện tốt nghiệp của học sinh nếu sai sót không được phát hiện; trên thực tế thiệt hại học bạ đã được ngăn chặn kịp thời nhờ giáo viên phát hiện và DESE tổ chức chấm lại toàn bộ. |
| Scale | **Khoảng 1.400 bài luận** của học sinh tại gần **200 học khu** trên toàn bang Massachusetts (số liệu chính thức do DESE công bố). |
| Probability | **Probability: Low** — Tỷ lệ ghi nhận trong sự cố cụ thể (incident-specific observed rate) ≈ **0,19%** (khoảng 1.400 / 750.000 bài thi); đây không phải xác suất lỗi chung của toàn bộ hệ thống AI chấm điểm. |
| Frequency | **Frequency: Low / Unknown** — Một sự cố kỹ thuật được ghi nhận trong đợt khảo thí được trích dẫn; tần suất chung của hệ thống không được tài liệu công khai công bố. |
| Vì sao? | - *Lý do chọn Mode & Layer:* Chọn `Automated scoring / QA failure` vì phản ánh chính xác sự cố kỹ thuật mà không võ đoán về cơ chế escalation nội bộ; chọn `Safety / QA (Inferred)` vì sự cố liên quan đến quy trình QA và rào chắn kiểm thử chất lượng.<br>- *Lý do chọn Harm & Lens:* Chọn `opportunity loss / Evaluation harm` vì điểm thi chuẩn hóa ảnh hưởng trực tiếp đến đánh giá học tập của học sinh.<br>- *Căn cứ mức độ:* Mức Potential Severity chọn `High` vì tính chất quan trọng của kỳ thi chuẩn hóa bang nếu xảy ra sai sót không được sửa, dù tỷ lệ trong sự cố cụ thể là `Low` (~0,19%). Số liệu 1.400 bài luận và 200 học khu được chứng thực từ Sở Giáo dục Massachusetts (DESE). |
