# Lab 21 — Phân tích rủi ro AI qua case study thực tế

- Họ và tên: Hoàng Anh Tài
- MSSV / mã học viên: 2A202602612
- Lớp: H201
- Ngành đã chọn: Giáo dục / AI tutor

---

### 1. Industry Risk Snapshot

| Nội dung | Đánh giá của tôi và lý do |
| --- | --- |
| Những tác hại chính có thể xảy ra | **1. Tiếp nhận tri thức sai lệch (Epistemic Harm):** AI tutor tạo ảo giác (hallucination), giải sai bài toán hoặc cung cấp sai sự thật lịch sử/khoa học khiến học sinh học sai bản chất.<br>**2. Suy giảm năng lực tư duy độc lập (Cognitive Crutch):** Học sinh lạm dụng AI làm thay bài tập, triệt tiêu quá trình tư duy nỗ lực (productive struggle), dẫn đến hổng kiến thức nghiêm trọng khi kiểm tra độc lập.<br>**3. Lệ thuộc tâm lý & nội dung không phù hợp (Psychological Harm):** Học sinh vị thành niên tin tưởng mù quáng vào chatbot (sycophancy / nhân hóa AI), có nguy cơ tiếp xúc với phản hồi lệch chuẩn hoặc thiên kiến.<br>**4. Đánh giá sai lệch và bất công học đường (Evaluation Harm):** Thuật toán AI chấm điểm tự động mắc lỗi kỹ thuật hoặc thiên kiến văn hóa/ngôn ngữ làm sai lệch học bạ học sinh.<br>*Đối tượng bị ảnh hưởng trực tiếp:* Học sinh (đặc biệt là lứa tuổi K-12), giáo viên, phụ huynh và các cơ sở giáo dục. |
| Mức độ high-stakes | **Trung bình đến Cao (Medium to High):**<br>*Lý do căn cứ (phục vụ bài tập):* Dù không đe dọa trực tiếp đến tính mạng sinh học tức thì như Y tế hay Xe tự lái, nhưng trong Giáo dục, AI tác động trực tiếp đến sự phát triển nhận thức, nhân sinh quan và tri thức nền tảng của trẻ vị thành niên — nhóm đối tượng chưa hoàn thiện kỹ năng phản biện (AI literacy). Ngoài ra, các quyết định đánh giá/chấm điểm bằng AI ảnh hưởng trực tiếp đến bằng cấp, học bạ và tương lai học tập của học sinh. |
| Dữ liệu nhạy cảm có thể được sử dụng | **Dữ liệu trẻ vị thành niên và hồ sơ học tập cá nhân (Tuân thủ FERPA / COPPA):**<br>- *Dữ liệu định danh cá nhân học sinh (PII vị thành niên):* Họ tên, ngày sinh, trường lớp, khuôn mặt/webcam, giọng nói.<br>- *Dữ liệu năng lực và tiến độ học tập:* Điểm số, lịch sử bài làm sai, điểm yếu nhận thức, nhật ký giải bài.<br>- *Dữ liệu hội thoại và biểu hiện hành vi:* Lịch sử câu hỏi thắc mắc, tâm tư tình cảm hoặc khó khăn tâm lý mà học sinh vô tình bộc lộ với trợ lý AI trong các phiên đối thoại 1-1. |
| Nhu cầu human review | **Cao (High):**<br>*Ai kiểm tra:* Giáo viên bộ môn, chuyên gia sư phạm và phụ huynh học sinh.<br>*Ở bước nào:*<br>1. *Tiền kiểm (Pre-deployment):* Thẩm định giáo trình, hệ thống prompt/guardrails và độ chính xác của cơ sở tri thức trước khi đưa vào lớp học.<br>2. *Giám sát thời gian thực (Real-time monitoring):* Dashboard cảnh báo tự động khi AI gặp lỗi tính toán hoặc khi học sinh hỏi các chủ đề bất thường/nhạy cảm.<br>3. *Hậu kiểm (Post-assessment):* Giáo viên trực tiếp kiểm tra và phê duyệt cuối cùng đối với mọi kết quả chấm điểm, xếp loại học lực của AI trước khi ghi vào hồ sơ.<br>*Vì sao:* Mô hình AI mang bản chất suy luận xác suất thống kê nên không thể cam đoan 100% tính đúng đắn; chỉ có con người mới có năng lực thấu cảm sư phạm, trách nhiệm giải trình pháp lý và khả năng phát hiện lỗ hổng hiểu biết để can thiệp kịp thời. |

---

### 2. Case study 1 — Nghiên cứu thực nghiệm Wharton (UPenn) về việc AI Tutor làm giảm năng lực học sinh (Bastani et al., 2024)

#### Brief Case

- Tổ chức / sản phẩm AI: Trường Kinh doanh Wharton (Đại học Pennsylvania) / Mô hình trợ lý học tập AI dựa trên GPT-4 (gồm 2 phiên bản thử nghiệm: "GPT Base" - giải bài trực tiếp và "GPT Tutor" - gợi ý sư phạm có rào chắn).
- Thời gian, địa điểm / bối cảnh: Năm học 2023–2024, thử nghiệm kiểm soát ngẫu nhiên (RCT) trên gần 1.000 học sinh trung học (lớp 9, 10, 11) tại Thổ Nhĩ Kỳ trong môn Toán.
- AI được dùng để làm gì: Đóng vai trò gia sư AI (AI Tutor) hỗ trợ học sinh giải các bài toán trung học theo thời gian thực trong các buổi tự luyện tập.
- Vấn đề hoặc sự kiện đáng chú ý: Nghiên cứu phát hiện hiện tượng "chiếc nạng nhận thức" (Cognitive crutch): Khi được dùng AI tutor giải bài trực tiếp, học sinh làm bài tập thực hành rất nhanh và đúng nhiều hơn, nhưng bị mất đi quá trình tư duy nỗ lực (productive struggle). Khi bước vào bài kiểm tra độc lập (không còn AI), năng lực giải quyết vấn đề của học sinh bị suy giảm nghiêm trọng so với nhóm không dùng AI.
- Số liệu có nguồn: Trong bài kiểm tra độc lập không có AI hỗ trợ, nhóm học sinh từng sử dụng GPT Base làm bài **kém hơn 17%** so với nhóm đối chứng (học sinh không bao giờ dùng AI), dù trước đó trong lúc luyện tập có AI, nhóm GPT Base giải đúng nhiều hơn 48% (theo nghiên cứu thực nghiệm của Bastani et al., Đại học Pennsylvania, công bố tháng 07/2024).
- Nguồn: Hamsa Bastani, Osbert Bastani, Alp Sungu, Haosen Ge, Özge Kabakcı, Rei Mariman — *"Generative AI Can Harm Learning"* — Wharton School, University of Pennsylvania / SSRN — Ngày công bố: 16/07/2024 — URL: https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4880692 — Trang 1–18.
- Phân biệt bằng chứng và nhận định:
  - *Điều nguồn xác nhận:* Thử nghiệm thực nghiệm chứng minh học sinh dùng AI tutor thiếu kiểm soát sư phạm (GPT Base) bị sụt giảm 17% điểm thi độc lập; học sinh có xu hướng ỷ lại và mắc lỗi số học nhiều hơn vì tin tưởng tuyệt đối vào kết quả sai của AI.
  - *Điều tôi suy luận hoặc còn chưa rõ:* Đây là nguy cơ suy giảm nhận thức có thể lan rộng nếu các trường học triển khai AI bừa bãi mà không kèm phương pháp sư phạm gợi mở (Socratic); tuy nhiên nghiên cứu tập trung vào môn Toán cấp THPT, chưa rõ mức độ tác động cụ thể đối với các môn khoa học xã hội hoặc cấp tiểu học.

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Học sinh sử dụng AI tutor trong lúc tự làm bài tập về nhà hoặc bài luyện tập trên lớp, chọn cách yêu cầu AI giải ngay đáp án thay vì tự suy nghĩ từng bước. |
| Stakeholder bị ảnh hưởng | Học sinh THPT (bị suy giảm năng lực tư duy toán học độc lập), giáo viên (bị che mờ mức độ hiểu bài thực tế của học sinh), phụ huynh và nhà trường. |
| Failure mode | Pedagogical misalignment & Cognitive Offloading (AI hoạt động như một công cụ giải bài thay thế thay vì công cụ sư phạm, triệt tiêu nỗ lực tư duy độc lập và tạo ảo tưởng thông thạo giả tạo). |
| Layer bắt đầu lỗi | **UX & Grounding / Pedagogical Guardrail layer** (Giao diện và cơ chế điều hướng sư phạm không khóa câu trả lời trực tiếp; không bắt buộc học sinh phải đi qua các bước gợi ý tư duy Socratic). |
| Harm xảy ra là gì? | **Hậu quả đã xảy ra:** Điểm kiểm tra năng lực độc lập của học sinh bị sụt giảm 17% so với nhóm không dùng AI.<br>**Nguy cơ:** Hổng lỗ hổng tri thức toán học nền tảng lâu dài, mất khả năng tư duy giải quyết vấn đề khi đối mặt với kỳ thi chuẩn hóa hoặc thực tế cuộc sống. |
| Harm lens | Epistemic & Educational Harm (Tác hại tri thức & suy giảm năng lực nhận thức giáo dục). |
| Severity | **Medium** (Không gây nguy hiểm tính mạng, nhưng gây suy giảm năng lực nhận thức và kết quả học tập trực tiếp của học sinh). |
| Scale | **Medium to High** (Gần 1.000 học sinh trong thử nghiệm tại Thổ Nhĩ Kỳ; có nguy cơ lan rộng ra hàng triệu học sinh toàn cầu nếu áp dụng AI tutor sai cách). |
| Probability | **High** (Tâm lý học sinh luôn có thiên hướng chọn giải pháp nhanh nhất để hoàn thành bài tập nếu không có sự ràng buộc). |
| Frequency | **High** (Xuất hiện liên tục hàng ngày trong mỗi buổi làm bài tập về nhà của học sinh). |
| Vì sao? | Đánh giá dựa trên số liệu định lượng từ thử nghiệm đối chứng ngẫu nhiên (RCT) của ĐH Pennsylvania; giới hạn bằng chứng là nghiên cứu trong khuôn khổ môn Toán trường trung học. |

---

### 3. Case study 2 — Lỗi ảo giác toán học và sai lệch sư phạm của trợ lý học tập Khanmigo (The Wall Street Journal & Khan Academy, 2024)

#### Brief Case

- Tổ chức / sản phẩm AI: Khan Academy / Trợ lý học tập ảo thông minh Khanmigo (xây dựng trên nền tảng OpenAI GPT-4).
- Thời gian, địa điểm / bối cảnh: Tháng 02/2024, trong quá trình triển khai thí điểm tại nhiều học khu công lập tại Hoa Kỳ (như Newark - New Jersey, Hobart - Indiana).
- AI được dùng để làm gì: Đóng vai trò gia sư AI 1-1 hỗ trợ học sinh học tập theo phương pháp gợi mở Socratic môn Toán và Khoa học.
- Vấn đề hoặc sự kiện đáng chú ý: Cuộc điều tra độc lập của báo *The Wall Street Journal* phát hiện Khanmigo thường xuyên mắc lỗi số học cơ bản (như phép trừ đơn giản 343 - 17, tính căn bậc hai, làm tròn số), tự tin khẳng định lời giải sai và không tự phát hiện lỗi ngay cả khi học sinh yêu cầu kiểm tra lại; thậm chí nhầm lẫn đúng - sai trong bài toán hình học định lý Pythagoras.
- Số liệu có nguồn: Theo xác nhận của Sal Khan (CEO Khan Academy) và báo cáo từ WSJ/Edutopia, tỷ lệ lỗi (error rate) của Khanmigo trong các bài toán nâng cao ban đầu ở mức **6% đến 7%**, trước khi tổ chức này phải tích hợp công cụ máy tính số học (symbolic calculator) để giảm tỷ lệ lỗi xuống còn khoảng **3%** vào năm 2024.
- Nguồn: Matt Barnum — *"We Tested an AI Tutor for Kids. It Struggled With Basic Math"* — The Wall Street Journal — Ngày công bố: 16/02/2024 — URL: https://www.wsj.com/tech/personal-tech/khan-academy-khanmigo-ai-tutor-math-ee0f0550.
- Phân biệt bằng chứng và nhận định:
  - *Điều nguồn xác nhận:* Khanmigo mắc các lỗi tính toán số học tiểu học và logic cụ thể; tỷ lệ lỗi ban đầu là 6%–7% và Khan Academy đã phải can thiệp kỹ thuật bổ sung máy tính để hạn chế ảo giác.
  - *Điều tôi suy luận hoặc còn chưa rõ:* Trẻ em lứa tuổi tiểu học và THCS chưa đủ năng lực thẩm định có nguy cơ tiếp thu sai kiến thức căn bản và mất niềm tin vào công cụ giáo dục; mức độ ảnh hưởng điểm số diện rộng của từng trường học chưa có con số thống kê chính thức.

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Học sinh tiểu học/THCS học toán 1-1 với AI tutor mà không có sự kèm cặp của phụ huynh hoặc giáo viên, đặt câu hỏi về các phép tính số học hoặc bài toán hình học đa bước. |
| Stakeholder bị ảnh hưởng | Học sinh nhỏ tuổi (tiếp thu sai khái niệm toán học), tổ chức Khan Academy (suy giảm uy tín thương hiệu), giáo viên và phụ huynh (mất công sức đính chính kiến thức). |
| Failure mode | Hallucination & Arithmetic Reasoning Failure (Mô hình ngôn ngữ lớn dự đoán token tiếp theo thay vì thực hiện phép tính chính xác, dẫn đến tự tin khẳng định kết quả sai). |
| Layer bắt đầu lỗi | **Model & Grounding layer** (Bản chất LLM thuần túy không phải là công cụ tính toán biểu thức tượng trưng; ở thời điểm đầu chưa được liên kết chặt chẽ với symbolic math engine). |
| Harm xảy ra là gì? | **Hậu quả đã xảy ra:** Trợ lý AI cung cấp các phép tính sai (343 - 17 tính sai, làm tròn sai) và học sinh bị nhầm lẫn trong quá trình học thử nghiệm.<br>**Nguy cơ:** Khiến học sinh hình thành lỗ hổng kiến thức toán học nền tảng ngay từ nhỏ. |
| Harm lens | Misinformation / Educational Accuracy Harm (Tác hại sai lệch thông tin và tri thức chuẩn xác trong giáo dục). |
| Severity | **Medium** (Gây hiểu sai kiến thức căn bản, có thể chỉnh sửa nếu phát hiện kịp thời nhưng gây nhiễu loạn tư duy người học). |
| Scale | **Medium** (Hàng chục nghìn học sinh tại các học khu đối tác của Khan Academy tại Mỹ). |
| Probability | **Medium to High** (Ban đầu tỷ lệ lỗi đo được từ 6%–7% ở các câu hỏi toán học nâng cao). |
| Frequency | **Medium** (Xuất hiện lặp lại ở các câu hỏi yêu cầu tính toán nhiều bước hoặc hình học). |
| Vì sao? | Căn cứ vào bài phóng sự điều tra của The Wall Street Journal và số liệu tỷ lệ lỗi 6%–7% do đích thân nhà sáng lập Sal Khan thừa nhận; giới hạn bằng chứng là chưa có báo cáo đo lường thiệt hại điểm thi cụ thể của học sinh. |

---

### 4. Case study 3 (Bổ sung) — Sự cố thuật toán AI chấm điểm bài luận làm sai lệch kết quả thi của 1.400 học sinh (Massachusetts DESE & Cognia, 2025)

#### Brief Case

- Tổ chức / sản phẩm AI: Sở Giáo dục Tiểu học và Trung học Massachusetts (DESE) & Đơn vị khảo thí Cognia / Hệ thống AI chấm điểm tự động bài thi tiêu chuẩn MCAS (Massachusetts Comprehensive Assessment System).
- Thời gian, địa điểm / bối cảnh: Tháng 10/2025, áp dụng cho kỳ thi chuẩn hóa MCAS của học sinh trên toàn bang Massachusetts, Hoa Kỳ.
- AI được dùng để làm gì: Tự động chấm điểm phần thi viết luận (essay automated scoring) của học sinh nhằm giảm tải thời gian và chi phí khảo thí.
- Vấn đề hoặc sự kiện đáng chú ý: Hệ thống AI chấm bài gặp lỗi kỹ thuật (technical glitch), tự động gán điểm 0 hàng loạt cho các bài viết luận đạt chuẩn của học sinh. Lỗi chỉ được phát hiện khi một giáo viên tại học khu Lowell rà soát trước dữ liệu của học sinh và báo cáo bất thường, buộc Sở Giáo dục phải mở cuộc điều tra và chấm lại toàn bộ.
- Số liệu có nguồn: Khoảng **1.400 bài luận** của học sinh tại gần **200 học khu** trên toàn bang Massachusetts bị AI chấm sai điểm (trong tổng số khoảng 750.000 bài thi luận MCAS toàn bang), theo thông cáo của DESE và báo cáo của các cơ quan báo chí (Patch / Indiatimes, 10/2025).
- Nguồn: Michael O'Connell — *"AI Glitch Results In 1,400 MCAS Essays Scored Incorrectly: DESE"* — Báo điện tử Patch / Massachusetts DESE — Ngày công bố: 07/10/2025 — URL: https://patch.com/massachusetts/across-ma/ai-glitch-results-1-400-mcas-essays-scored-incorrectly-dese.
- Phân biệt bằng chứng và nhận định:
  - *Điều nguồn xác nhận:* Khoảng 1.400 bài luận bị gán điểm sai do lỗi kỹ thuật của hệ thống AI tại gần 200 học khu; cơ chế hậu kiểm của giáo viên con người đã kịp thời phát hiện trước khi công bố điểm chính thức và DESE đã tổ chức chấm lại toàn bộ.
  - *Điều tôi suy luận hoặc còn chưa rõ:* Đây là rủi ro điển hình của việc thiếu cơ chế kiểm định ngoại lệ (anomaly detection); nếu giáo viên không phát hiện kịp thời, 1.400 học sinh này đã phải chịu thiệt hại nghiêm trọng về học bạ và xét tốt nghiệp.

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Hệ thống AI tự động duyệt và gán điểm số hàng loạt cho các bài thi chuẩn hóa mà không có bộ lọc phát hiện điểm số bất thường (anomaly detection filter) trước khi xuất kết quả. |
| Stakeholder bị ảnh hưởng | 1.400 học sinh (nguy cơ bị ghi nhận điểm 0 oan), phụ huynh, giáo viên các học khu, Sở Giáo dục Massachusetts (DESE) và công ty khảo thí Cognia. |
| Failure mode | Automated scoring failure & Algorithmic glitch (Lỗi kỹ thuật trong đường ống chấm điểm tự động khiến thuật toán đánh giá sai lệch toàn bộ chất lượng bài viết). |
| Layer bắt đầu lỗi | **Model & Safety/Quality Assurance Pipeline layer** (Đường ống xử lý dữ liệu và kiểm thử chất lượng trước khi triển khai thiếu cơ chế bắt lỗi ngoại lệ khi điểm số phân phối bất thường). |
| Harm xảy ra là gì? | **Hậu quả đã xảy ra:** 1.400 bài luận bị gán điểm sai, gây hoang mang cho nhà trường và phụ huynh, tốn kém nguồn lực để rà soát và chấm lại toàn bộ.<br>**Nguy cơ:** Ảnh hưởng trực tiếp đến kết quả xét tuyển và tốt nghiệp của học sinh nếu lỗi không được giáo viên phát hiện. |
| Harm lens | Algorithmic Injustice & Assessment Harm (Tác hại đánh giá sai lệch và bất công do thuật toán khảo thí). |
| Severity | **High** (Điểm thi chuẩn hóa MCAS là điều kiện tốt nghiệp và đánh giá xếp hạng trường học cấp bang). |
| Scale | **Medium** (1.400 bài thi của học sinh trên gần 200 học khu bị tác động). |
| Probability | **Low** (Tỷ lệ lỗi trên tổng số bài thi là nhỏ: 1.400 / 750.000 ~ 0.19%). |
| Frequency | **Low** (Sự cố mang tính bột phát do cập nhật kỹ thuật hệ thống). |
| Vì sao? | Căn cứ theo thông cáo chính thức từ Sở Giáo dục DESE và đơn vị khảo thí Cognia tháng 10/2025; giới hạn bằng chứng là lỗi kỹ thuật nội bộ cụ thể chưa được công bố chi tiết mã nguồn. |
