# Lab 21 — Phân tích rủi ro AI qua case study thực tế

- Họ và tên: Hoàng Anh Tài
- MSSV / mã học viên: 2A202602612
- Lớp: H201
- Ngành đã chọn: Giáo dục / AI tutor

---

### 1. Industry Risk Snapshot

| Nội dung | Đánh giá của tôi và lý do |
| --- | --- |
| Những tác hại chính có thể xảy ra | **1. Tiếp nhận tri thức sai lệch (Epistemic Harm):** AI tutor tạo ảo giác (hallucination), giải sai bài toán hoặc cung cấp sai sự thật lịch sử/khoa học khiến học sinh học sai bản chất.<br>**2. Suy giảm năng lực tư duy độc lập (Cognitive Crutch):** Học sinh lạm dụng AI làm thay bài tập, triệt tiêu quá trình tư duy nỗ lực (productive struggle), dẫn đến hổng kiến thức nghiêm trọng khi kiểm tra độc lập.<br>**3. Lệ thuộc tâm lý & nội dung không phù hợp (Psychological Harm):** Học sinh vị thành niên tin tưởng mù quáng vào chatbot (sycophancy / nhân hóa AI), có nguy cơ tiếp xúc với phản hồi lệch chuẩn hoặc thiên kiến.<br>**4. Đánh giá sai lệch và bất công học đường (Evaluation Harm):** Thuật toán AI chấm điểm tự động mắc lỗi kỹ thuật hoặc thiên kiến làm sai lệch kết quả học bạ học sinh.<br>*Đối tượng bị ảnh hưởng trực tiếp:* Học sinh (đặc biệt là lứa tuổi K-12), giáo viên, phụ huynh và các cơ sở giáo dục. |
| Mức độ high-stakes | **Trung bình đến Cao (Medium to High):**<br>*Lý do căn cứ (phục vụ bài tập):* Dù không đe dọa trực tiếp đến tính mạng sinh học tức thì như Y tế hay Xe tự lái, nhưng trong Giáo dục, AI tác động trực tiếp đến sự phát triển nhận thức, nhân sinh quan và tri thức nền tảng của trẻ vị thành niên — nhóm đối tượng chưa hoàn thiện kỹ năng phản biện (AI literacy). Ngoài ra, các quyết định đánh giá/chấm điểm bằng AI ảnh hưởng trực tiếp đến bằng cấp, học bạ và cơ hội học tập tương lai của học sinh. |
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
| High-risk moment | Học sinh THPT sử dụng trợ lý AI trong các buổi luyện tập toán học độc lập tại nhà hoặc trên lớp mà không có giáo viên hướng dẫn, đặt câu hỏi yêu cầu AI cung cấp ngay lời giải hoàn chỉnh cho bài tập khó. |
| Stakeholder bị ảnh hưởng | - **Người dùng trực tiếp:** Học sinh THPT (bị suy giảm năng lực tư duy toán học độc lập và mất thói quen tự giải bài).<br>- **Bên liên quan:** Giáo viên bộ môn (bị che mờ mức độ hiểu bài thực tế của học sinh), phụ huynh và nhà trường (chịu ảnh hưởng về chất lượng giáo dục thực chất). |
| Failure mode | **Over-reliance** *(kèm **Sycophancy**)*:<br>Người dùng tin AI quá mức và bỏ kiểm tra (Over-reliance); AI đồng ý với người dùng dù người dùng sai và dễ dãi cung cấp đáp án hoàn chỉnh theo mong muốn làm bài nhanh của học sinh thay vì kiên nhẫn dẫn dắt gợi mở (Sycophancy). |
| Layer bắt đầu lỗi | **Grounding** *(kèm **UX**)*:<br>- *Grounding:* System message / prompt ban đầu của bản "GPT Base" không được thiết lập giới hạn sư phạm (pedagogical guardrails); AI không được neo vào quy tắc gợi ý tư duy Socratic mà giải luôn bài toán.<br>- *UX:* Cách hiển thị giao diện đưa ra câu trả lời quá mượt mà và tiện lợi khiến học sinh thỏa mãn tức thì (ảo tưởng thông thạo), làm học sinh khó và lười kiểm tra lại. |
| Harm xảy ra là gì? | **Học sinh trung học** bị **suy giảm 17% kết quả bài kiểm tra độc lập và hổng kiến thức toán căn bản** khi **học sinh sử dụng AI giải bài trực tiếp như một "chiếc nạng nhận thức" trong suốt quá trình luyện tập mà không trải qua nỗ lực tư duy (productive struggle)**.<br>*(Ghi rõ: Hậu quả đã xảy ra trong nhóm thử nghiệm RCT của nghiên cứu ĐH Pennsylvania; đồng thời là nguy cơ suy giảm nhận thức diện rộng nếu ứng dụng đại trà).* |
| Harm lens | **opportunity loss** *(Mất cơ hội rèn luyện tư duy phản biện độc lập, mất cơ hội phát triển năng lực tư duy toán học tự thân và đạt kết quả thực chất trong các kỳ thi không có công nghệ trợ giúp).* |
| Severity | **Medium** *(Hậu quả gây suy giảm năng lực nhận thức đo lường được là 17% điểm số; không đe dọa thể chất trực tiếp như y tế, nhưng tác động tiêu cực rõ rệt đến kết quả học đường và năng lực tư duy nếu kéo dài).* |
| Scale | **993 học sinh trung học** tại Thổ Nhĩ Kỳ tham gia nghiên cứu thực nghiệm RCT có đối chứng (phạm vi đo lường chính thức theo Wharton / SSRN 2024); có tiềm năng ở mức **High** (hàng triệu học sinh) nếu các trường học triển khai AI tutor thiếu rào chắn sư phạm. |
| Probability | **High** *(Đánh giá của tôi: Tâm lý học sinh luôn ưu tiên con đường tốn ít nỗ lực nhất khi hệ thống cho phép; trong nghiên cứu hầu hết học sinh nhóm GPT Base đều phụ thuộc vào AI).* |
| Frequency | **High** *(Đánh giá của tôi: Lặp lại thường xuyên hàng ngày trong mỗi buổi học sinh làm bài tập về nhà suốt năm học).* |
| Vì sao? | - *Lý do chọn Mode & Layer:* Chọn `Over-reliance` vì học sinh tin AI quá mức và bỏ qua quá trình tự suy nghĩ; chọn `Grounding` vì system message thiếu rào chắn sư phạm để bắt buộc AI chỉ đưa ra gợi ý từng bước.<br>- *Lý do chọn Harm & Lens:* Chọn `opportunity loss` vì sự ỷ lại làm học sinh mất cơ hội trui rèn năng lực nhận thức.<br>- *Căn cứ mức độ:* Số liệu giảm 17% điểm thi độc lập và tăng 48% khi có AI là kết quả định lượng có đối chứng của ĐH Pennsylvania; Severity chọn `Medium` vì tác hại nhận thức có thể khắc phục nếu điều chỉnh phương pháp sư phạm kịp thời. |

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
| High-risk moment | Học sinh lứa tuổi tiểu học và THCS đối thoại 1-1 với gia sư AI Khanmigo để học các bài toán số học, làm tròn, căn bậc hai hoặc hình học mà không có giáo viên hoặc phụ huynh bên cạnh giám sát tính đúng đắn. |
| Stakeholder bị ảnh hưởng | - **Người dùng trực tiếp:** Học sinh nhỏ tuổi (tiếp thu sai khái niệm toán học nền tảng).<br>- **Bên liên quan:** Phụ huynh và giáo viên (mất thêm công sức rà soát và đính chính kiến thức sai); tổ chức Khan Academy (tổn hại uy tín thương hiệu giáo dục). |
| Failure mode | **Hallucination** *(kèm **Sycophancy**)*:<br>AI bịa kết quả số học sai (như phép trừ căn bản 343 - 17, căn bậc hai, làm tròn) và trình bày lời giải như thể hoàn toàn chính xác (Hallucination); khi học sinh đưa ra bước giải sai trong bài hình học, AI vẫn dễ dãi đồng ý và không tự sửa lỗi dù được người dùng nhắc (Sycophancy). |
| Layer bắt đầu lỗi | **Model** *(kèm **Grounding** — nêu giả thuyết riêng do nguồn chưa công bố toàn bộ pipeline kỹ thuật)*:<br>- *Model:* Năng lực cốt lõi của Large Language Model (GPT-4) là dự đoán chuỗi từ ngữ (next-token prediction) dựa trên xác suất văn bản chứ không phải bộ xử lý toán học ký hiệu logic (symbolic engine), dẫn đến tính sai các phép tính số học.<br>- *Grounding (Giả thuyết riêng do chưa đủ bằng chứng công bố chi tiết):* Hệ thống grounding ở giai đoạn đầu chưa tích hợp cơ chế Tool Calling / Code Execution để điều hướng các biểu thức toán học sang máy tính chuyên dụng trước khi trả lời học sinh. |
| Harm xảy ra là gì? | **Học sinh nhỏ tuổi** bị **tiếp thu kiến thức toán học sai lệch và hình thành lỗ hổng tư duy căn bản** khi **gia sư AI Khanmigo tự tin khẳng định các phép tính số học sai (như phép tính 343 - 17) và không nhận ra lỗi sai của chính mình khi được học sinh yêu cầu kiểm tra lại**.<br>*(Ghi rõ: Hậu quả đã xảy ra được The Wall Street Journal ghi nhận trong các bài test thực tế; nguy cơ là học sinh làm sai bài kiểm tra và mất niềm tin vào công nghệ giáo dục).* |
| Harm lens | **misinformation** *(Thông tin sai lệch về mặt số học, quy tắc toán học và logic suy luận được trình bày như sự thật).* |
| Severity | **Medium** *(Gây sai lệch kiến thức nền tảng ở lứa tuổi đang định hình nhận thức; không gây tổn hại thể chất nguy kịch, nhưng gây nhiễu loạn tư duy và đòi hỏi sự can thiệp sư phạm của con người để sửa sai).* |
| Scale | **Hàng chục nghìn học sinh** tại các học khu công lập đối tác thí điểm của Khan Academy tại Mỹ (như Newark - New Jersey, Hobart - Indiana) trong giai đoạn đầu năm 2024. |
| Probability | **Medium** *(Tỷ lệ đo được: **6% đến 7%** ở các bài toán nâng cao theo thừa nhận chính thức của CEO Sal Khan; sau đó giảm xuống khoảng **3%** khi tích hợp máy tính).* |
| Frequency | **Medium** *(Đánh giá của tôi: Xuất hiện định kỳ mỗi khi học sinh gặp các bài toán liên quan đến tính toán số học nhiều chữ số hoặc hình học trừu tượng).* |
| Vì sao? | - *Lý do chọn Mode & Layer:* Chọn `Hallucination` vì mô hình tự bịa kết quả tính toán sai nhưng trình bày rất tự tin; chọn `Model` vì bản chất LLM dự đoán từ ngữ thay vì tính toán số học. Ghi rõ giả thuyết về layer `Grounding` vì chưa có tài liệu công bố chi tiết toàn bộ pipeline kỹ thuật của Khan Academy thời điểm đó.<br>- *Lý do chọn Harm & Lens:* Chọn `misinformation` vì tác hại cốt lõi là việc truyền bá thông tin số học không đúng sự thật.<br>- *Căn cứ mức độ:* Số liệu tỷ lệ lỗi 6%–7% do đích thân nhà sáng lập Sal Khan xác nhận; bài phóng sự của The Wall Street Journal (02/2024) trực tiếp chứng minh các trường hợp lỗi tính toán thực tế. |

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
| High-risk moment | Hệ thống AI tự động xử lý và gán điểm số hàng loạt cho các bài thi viết luận chuẩn hóa MCAS của học sinh, trước khi kết quả được chốt gửi về các học khu và ghi nhận vào học bạ. |
| Stakeholder bị ảnh hưởng | - **Người dùng/đối tượng trực tiếp:** 1.400 học sinh có bài thi bị chấm điểm sai (nguy cơ bị ghi nhận điểm 0 oan).<br>- **Bên liên quan:** Giáo viên bộ môn tại gần 200 học khu (phải tốn công đối soát dữ liệu bất thường); Sở Giáo dục Massachusetts (DESE) và công ty khảo thí Cognia (chịu trách nhiệm pháp lý và uy tín giải trình). |
| Failure mode | **Escalation failure** *(kèm nguy cơ liên đới **Bias / fairness**)*:<br>AI tiếp tục xử lý dù cần chuyển cho người thật (Escalation failure); hệ thống tự động gán điểm 0 cho hàng loạt bài luận đạt chuẩn mà không hề kích hoạt cảnh báo bất thường để chuyển giao cho giám khảo con người xem xét; gây bất công nghiêm trọng giữa các nhóm học sinh bị lỗi (Bias/fairness). |
| Layer bắt đầu lỗi | **Safety** *(kèm **Model** — nêu giả thuyết riêng do chưa đủ bằng chứng công bố chi tiết mã nguồn)*:<br>- *Safety:* Lớp bảo vệ và quy trình kiểm thử chất lượng (Quality Assurance) thiếu bộ lọc phát hiện ngoại lệ (anomaly detection filter / circuit breaker) — khi tỷ lệ điểm 0 tăng đột biến ở các bài viết đủ độ dài, hệ thống không tự động ngắt để chuyển sang human review.<br>- *Model (Chưa đủ bằng chứng):* Nguồn tin chỉ xác nhận "temporary technical issue" trong mô hình của Cognia; giả thuyết riêng là mô hình gặp lỗi phân tích cú pháp (parsing) hoặc xung đột trong đường ống xử lý định dạng bài nộp. |
| Harm xảy ra là gì? | **1.400 học sinh tại gần 200 học khu** bị **nguy cơ trượt chuẩn tốt nghiệp THPT, bị ghi nhận điểm 0 oan vào học bạ và tổn thất tinh thần nghiêm trọng** khi **hệ thống AI chấm bài tự động gặp sự cố kỹ thuật và gán điểm 0 hàng loạt cho các bài luận đạt chuẩn**.<br>*(Ghi rõ: Hậu quả điểm số bị sai lệch tại 200 học khu đã xảy ra trên hệ thống; nguy cơ học bạ đã được ngăn chặn kịp thời nhờ giáo viên phát hiện trước khi công bố chính thức và DESE đã tổ chức chấm lại toàn bộ).* |
| Harm lens | **opportunity loss** *(kèm **dignity loss**)*:<br>- *opportunity loss:* Nguy cơ mất cơ hội tốt nghiệp THPT, mất cơ hội xét tuyển đại học và học bổng dựa trên kết quả kỳ thi chuẩn hóa bang.<br>- *dignity loss:* Tổn hại phẩm giá khi năng lực học tập thực chất bị gán điểm 0 liệt vô căn cứ. |
| Severity | **High** *(Căn cứ: MCAS là kỳ thi chuẩn hóa bắt buộc cấp bang, điểm số có tính chất quyết định điều kiện tốt nghiệp THPT của học sinh; việc bị chấm điểm 0 có thể dẫn tới hậu quả học vấn đặc biệt nghiêm trọng nếu không sửa sai).* |
| Scale | **Khoảng 1.400 bài luận** của học sinh tại gần **200 học khu** trên toàn bang Massachusetts (số liệu chính thức do DESE công bố). |
| Probability | **Low** *(Tỷ lệ đo được: khoảng **0.19%** — tức 1.400 bài lỗi trên tổng số khoảng 750.000 bài thi luận MCAS toàn bang).* |
| Frequency | **Low** *(Đánh giá của tôi: Sự cố kỹ thuật bột phát xuất hiện một lần trong đợt khảo thí năm học do lỗi cập nhật phần mềm).* |
| Vì sao? | - *Lý do chọn Mode & Layer:* Chọn `Escalation failure` vì hệ thống AI âm thầm chấm sai và gán điểm 0 hàng loạt mà không biết tự dừng lại để chuyển cho người thật; chọn `Safety` vì lỗ hổng nằm ở quy trình QA và thiếu bộ lọc ngắt tự động khi phát hiện bất thường. Ghi rõ "chưa đủ bằng chứng" về kiến trúc `Model` vì nhà thầu Cognia không công bố chi tiết kỹ thuật nội bộ.<br>- *Lý do chọn Harm & Lens:* Chọn `opportunity loss` vì điểm thi MCAS quyết định trực tiếp cơ hội tốt nghiệp của học sinh.<br>- *Căn cứ mức độ:* Severity chọn `High` vì hậu quả trượt tốt nghiệp là rất nặng nề đối với học sinh, dù Probability chọn `Low` (0.19%) vì đây là sự cố kỹ thuật hiếm hoi. Số liệu 1.400 bài luận và 200 học khu được chứng thực từ Sở Giáo dục Massachusetts (DESE). |
