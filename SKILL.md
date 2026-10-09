# KẾ TOÁN DIỆU TÂM — SOCIAL CONTENT SKILL

**Phiên bản:** 0.19  
**Ngày:** 09/10/2026  
**Vai trò:** Runtime orchestrator cho content case đa nền tảng  
**Trạng thái:** Đang phát triển — Facebook dạng ảnh đã test thực tế; TikTok Photo Carousel v0.7 đang thử nghiệm theo hướng Facebook-first, rõ giá trị người xem; TikTok video production chưa khóa.

---

# 0. CÁCH DÙNG SKILL NÀY

Prompt tối thiểu hợp lệ:

> **“Tiến hành chạy skill https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/SKILL.md”**

Khi nhận prompt kiểu này, AI phải:

1. đọc SKILL.md trước;
2. không nhảy thẳng sang viết bài;
3. chỉ mở file con đúng với checkpoint hiện tại;
4. tự chạy checkpoint;
5. trình bày recommendation;
6. dừng tại đúng gate cần user quyết định;
7. khi user nói **OK**, khóa quyết định và chạy ngay checkpoint tiếp theo ở turn kế tiếp.

Không yêu cầu user phải viết prompt dài với:

- chủ đề;
- đối tượng;
- góc;
- mục tiêu;
- định dạng;

nếu họ muốn skill tự tìm từ đầu.

## 0.1. Ý nghĩa của “OK”

Khi user chỉ trả lời:

> **OK**

mặc định có nghĩa:

1. duyệt recommendation hiện tại;
2. khóa các decision lock của checkpoint hiện tại;
3. chạy ngay checkpoint tiếp theo;
4. không hỏi xác nhận lại lần hai.

Không trả lời kiểu:

> “Đã chốt. Anh có muốn tôi tiếp tục không?”

Một checkpoint = tối đa một lần duyệt, trừ khi user yêu cầu sửa.

### Ngoại lệ TikTok T3A

Ở **T3A — Caption Draft**, `OK` **không khóa nguyên văn Caption**.

`OK` tại T3A có nghĩa:

1. user chấp nhận hướng nội dung;
2. core message đúng hướng;
3. factual direction và evidence boundary được giữ;
4. CTA intent được giữ;
5. AI phải chuyển vai từ **writer → editor/reviewer** và chạy ngay **T3B — Final Editorial Review** ở turn kế tiếp.

Sau T3A, AI vẫn được phép sửa:

- opening;
- câu chữ;
- thứ tự đoạn;
- độ dài;
- mức giải thích;
- ví dụ/tình huống;
- cách giải thích hoặc ví dụ (nếu hữu ích);
- wording CTA;
- hashtag nếu việc sửa Caption làm hashtag khác phù hợp hơn.

Chỉ sau khi user `OK` bản **T3B Final Caption** mới khóa nguyên văn Caption/CTA/hashtag để sang T4.

## 0.2. Nguyên tắc tự động hóa

> **Không biến checklist nội bộ của AI thành công việc của user. AI tự kiểm những gì có thể tự kiểm; chỉ dừng xin OK ở những quyết định sáng tạo hoặc chiến lược thật sự cần người duyệt.**

Các việc như:

- factual QA;
- keyword;
- hashtag research;
- spacing;
- emoji;
- safe zone;
- kiểm giới hạn nền tảng;
- AIGC reminder;

mặc định là việc nội bộ, không tạo checkpoint riêng trừ khi chúng làm thay đổi quyết định đã khóa.

---

# 1. KIẾN TRÚC TỔNG

Workflow mặc định của một content case:

> **SHARED RESEARCH CORE → FACEBOOK PRODUCTION → TIKTOK ADAPTATION → TIKTOK PRODUCTION**

Nguyên tắc:

> **Research once, adapt many times.**

Và:

> **Kế thừa sự thật và insight; không kế thừa máy móc packaging.**

Nếu user chỉ yêu cầu một nền tảng cụ thể:

- Facebook-only → kết thúc sau Facebook;
- TikTok-only → chạy Shared Research Core rồi vào TikTok ở Standalone Mode;
- nền tảng khác chưa có playbook → nói rõ phạm vi đang thử nghiệm.

Nếu user chỉ đưa URL skill và không chỉ định platform:

> **mặc định full workflow = Facebook trước, sau khi Facebook hoàn tất thì tiếp tục TikTok Photo Carousel.**

Không hỏi lại “có muốn làm TikTok không?” trong full workflow.

---

# 2. CONTENT CASE / SHARED RESEARCH CORE

Sau pha research, AI phải giữ một package nội bộ dùng xuyên suốt case:

- Topic / event
- Verified facts
- Sources
- Evidence strength
- What is certain
- What is not yet certain
- Audience
- Reader situation
- Main question / pain
- Dangerous misunderstanding
- Useful action
- Core tension
- Strong wording / conflict-bearing words
- Content opportunity
- Approved angle
- Time-sensitive items requiring refresh
- Recommended Route / Content Worthiness

Các factual/audience decision đã được duyệt trở thành **decision lock cấp content case**.

Không tự mở lại ở platform sau trừ khi:

- có nguồn mới;
- nguồn mâu thuẫn;
- dữ kiện thời gian có thể đã thay đổi;
- user yêu cầu kiểm lại;
- hoặc phát hiện lỗi factual.

Khi cần refresh:

> **refresh phần bị ảnh hưởng, không reset toàn bộ content case.**

---

# 3. REPO VÀ FILE CHÍNH THỨC

**Repo:** quoctran-2608/skill_KTDieuTam_Social_Article  
**Branch:** main  
**Repo URL:** https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article

## Research

- docs/research/ktdt-research-workflow.md  
  https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/research/ktdt-research-workflow.md

- docs/research/ktdt-source-verification.md  
  https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/research/ktdt-source-verification.md

- docs/research/ktdt-platform-competitor-research.md  
  https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/research/ktdt-platform-competitor-research.md

- docs/research/ktdt-research-output.md  
  https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/research/ktdt-research-output.md

## Writing

- docs/brand/ktdt-social-writing-dna.md  
  https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/brand/ktdt-social-writing-dna.md

- docs/content/ktdt-hook-language-psychology.md  
  https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/content/ktdt-hook-language-psychology.md

- docs/content/ktdt-body-writing-retention.md  
  https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/content/ktdt-body-writing-retention.md

## Platform

- docs/platform/ktdt-facebook-post-playbook.md  
  https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/platform/ktdt-facebook-post-playbook.md

- docs/platform/ktdt-tiktok-writing-playbook.md  
  https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/platform/ktdt-tiktok-writing-playbook.md

> **Luật tải file:** Không đọc toàn bộ repo ở mỗi turn. Chỉ mở file cần cho checkpoint hiện tại. Khi checkpoint yêu cầu nhiều file, đọc đủ trước khi tạo output.

---

# 4. DECISION LOCK

Khi user đã duyệt, AI không tự đổi:

- topic;
- factual conclusion;
- audience;
- objective;
- angle;
- hook;
- retention path;
- CTA;
- format;
- title;
- số slide;
- nhiệm vụ từng slide;
- exact slide copy;
- caption;
- chữ trên ảnh;
- số ảnh;
- visual concept đã khóa;
- logo/vị trí logo nếu platform đó có dùng.

Chỉ reopen khi:

- lỗi factual / bằng chứng;
- lỗi hiển thị khách quan bắt buộc sửa;
- user chủ động mở lại.

> **Không sáng tạo lại chỉ vì AI nghĩ có thể “hay hơn”.**

## TikTok Caption — Soft Lock và Hard Lock

**Sau T3A + OK — Soft Lock**

Khóa:

- factual direction;
- core message;
- evidence boundary;
- audience;
- lý do quan tâm chính (tension thật nếu có);
- CTA intent.

Chưa khóa:

- exact wording;
- opening;
- paragraph order;
- explanation depth;
- mental model;
- CTA wording;
- caption length;
- hashtag package.

**Sau T3B + OK — Hard Lock**

Khóa:

- exact final Caption;
- exact CTA wording;
- hashtag package.

Sau Hard Lock mới được sang visual.

---

# 5. AUTO-START — QUÉT CHỦ ĐỀ NÓNG

Nếu user không cho chủ đề:

### Bắt buộc đọc
- docs/research/ktdt-research-workflow.md
- docs/research/ktdt-source-verification.md khi cần kiểm nhanh

### Cửa sổ research — ưu tiên yêu cầu của user

**Nếu user chỉ định khoảng thời gian ngay trong prompt chạy skill** (ví dụ: "1 tháng vừa qua", "30 ngày gần đây", "tháng 9/2026", "từ 01/09 đến 30/09/2026"), thì **dùng chính khoảng thời gian đó cho AUTO-START/shortlist**, thay thế hoàn toàn mặc định 24–72 giờ / tối đa 7 ngày ở đây **và trong các file research con**.

- Với mốc tương đối, tính theo **ngày chạy skill** và múi giờ phù hợp. "1 tháng vừa qua" = một tháng tính lùi từ ngày chạy; không tự đổi thành "tháng trước". "30 ngày gần đây" = 30 ngày tính lùi.
- Ghi ngắn **khoảng ngày thực tế đã hiểu** khi trình shortlist, để user kiểm tra; không tạo checkpoint xác nhận thời gian riêng nếu yêu cầu đã rõ.
- Chỉ chọn các topic có **diễn biến, thay đổi hoặc catalyst đáng nói trong khoảng user yêu cầu**. Có thể tra nguồn ngoài khoảng đó để kiểm chứng bối cảnh, nhưng không được lấy tin cũ không có diễn biến trong kỳ làm ứng viên rồi gọi là tin trong kỳ.
- Không âm thầm thu hẹp về hôm nay/tuần này hoặc mở rộng ngoài khoảng đã được yêu cầu. Nếu không đủ 3–5 topic mạnh, nói rõ và đưa số ứng viên thực sự đạt thay vì tự đổi phạm vi.

**Chỉ khi user không chỉ định thời gian**, áp dụng mặc định:

1. ưu tiên 24–72 giờ gần nhất;
2. thiếu ứng viên tốt → mở rộng tối đa 7 ngày;
3. cũ hơn chỉ giữ khi có diễn biến/deadline/thực thi mới.

Nếu có web/search, phải dùng dữ liệu phù hợp với cửa sổ đã chọn và kiểm chứng tình trạng hiện tại khi cần.

### Lọc topic — ưu tiên strength trước khi nghĩ hook

Một ứng viên mạnh phải được nhìn qua 5 câu hỏi:

**1. ACTUAL NOVELTY / WHY NOW**

Không chỉ hỏi:

> “Có tin hoặc văn bản mới không?”

Phải hỏi:

> **Điều gì thực sự mới hoặc vừa thay đổi đối với người đọc, và tại sao họ nên quan tâm ngay lúc này?**

Một văn bản mới, bài giải thích mới hoặc xác nhận lại cách làm cũ **không tự động tạo actual novelty**.

Nếu chưa đủ dữ kiện để biết có thay đổi thật hay không:

> **CHƯA XÁC ĐỊNH — R1 PHẢI KIỂM LẠI PREMISE**

**2. ĐÚNG TỆP**

Topic có liên quan rõ tới người đọc Diệu Tâm hay không?

**3. STAKES / TÁC ĐỘNG THỰC**

Nếu người đọc bỏ qua, họ có thể:

- mất tiền;
- bỏ lỡ quyền lợi;
- gặp rủi ro;
- trễ deadline;
- sai nghĩa vụ;
- sai hồ sơ;
- ra quyết định sai;
- tốn đáng kể thời gian/công sức;
- hoặc bị ảnh hưởng vận hành?

Không phải “có tác động” là đủ. Phải nhìn **mức độ tác động**.

**4. KIỂM CHỨNG ĐƯỢC**

Có nguồn đủ mạnh để research sâu không?

**5. NATURAL TENSION**

Sự thật bản thân nó có lý do khiến đúng người quan tâm không?

> **Hook không được cứu một topic yếu.**

Nếu phải dùng copywriting quá mạnh mới khiến một việc nhỏ trông đáng sợ hoặc cấp bách, topic đó không được coi là strong candidate.

Topic ưu tiên số 1 thường nên mạnh ở phần lớn các tiêu chí trên.

Tuy nhiên:

> **stakes thấp không tự động đồng nghĩa topic vô giá trị.**

Một topic có thể vẫn hữu ích cho education, trust, search hoặc chăm audience và được phân loại thành Utility / Strategic Organic.

### TOPIC STRENGTH PREVIEW — qualitative, không chấm điểm giả chính xác

Với mỗi ứng viên shortlist, AI tự đánh giá ngắn:

- **Actual novelty:** Mạnh / Vừa / Yếu / Chưa xác định
- **Why now:** Rõ / Có nhưng yếu / Không rõ
- **Stakes:** Cao / Vừa / Thấp
- **Natural tension:** Cao / Vừa / Thấp
- **Cold-attention potential:** Cao / Vừa / Thấp
- **Strategic / utility value:** Cao / Vừa / Thấp
- **Likely route:** A / B / C

Không dùng kiểu:

> 7.2/10 = PASS  
> 6.8/10 = FAIL

vì các con số đó dễ tạo cảm giác chính xác giả.

Đây là preview ban đầu, chưa phải kết luận cuối. R1–R4 được phép nâng hoặc hạ route khi bằng chứng mới xuất hiện.

### Output shortlist

Đề xuất **3–5 chủ đề**.

Mỗi chủ đề chỉ cần:

- chuyện gì đang xảy ra;
- **Why now / actual change ban đầu**;
- ai bị ảnh hưởng;
- stakes chính;
- natural tension;
- độ chắc nguồn;
- likely route;
- đánh giá: **Nên làm / Có thể làm / Chưa nên làm**.

### Kiểm framing trước khi khuyến nghị — nội bộ

Trước khi đưa ra **KHUYẾN NGHỊ SỐ 1**, AI tự kiểm: framing dự kiến có dễ làm người đọc hiểu rằng Diệu Tâm đang hướng dẫn né/lách quy định, cổ súy sai phạm hoặc khai thác sự cố để câu chú ý không?

Nếu **topic tốt nhưng framing chưa tốt**, tự đề xuất cách đặt vấn đề chính xác, hữu ích và phù hợp vai trò tư vấn tuân thủ của Diệu Tâm **trước khi trình user**. Không loại topic chỉ vì liên quan nợ thuế, cưỡng chế, vi phạm hay rủi ro; không làm mất tension thật chỉ để câu chữ nghe an toàn hơn. Nếu điều kiện pháp lý còn chưa chắc, để R1 xác minh, không tự diễn giải thành quyền được làm.

Đây là kiểm tra nội bộ trong shortlist, **không thêm checkpoint hay thang điểm**.

Cuối cùng chọn:

> **KHUYẾN NGHỊ SỐ 1**

Khi AUTO-START không có mục tiêu khác từ user, ưu tiên khuyến nghị topic có khả năng trở thành:

> **Route A — Priority / Traffic Candidate**

hơn một topic chỉ hữu ích nhỏ.

Route B vẫn được giữ nếu có strategic/utility value rõ, nhưng không được giả vờ rằng nó là strong cold-traffic candidate.

Nếu user nói OK mà không chọn số khác → khóa #1 và chạy Research Core.

---

# 6. SHARED RESEARCH CORE — CHẠY MỘT LẦN

## R1 — Sự thật

### Đọc
- ktdt-research-workflow.md
- ktdt-source-verification.md

### Làm
- xác minh nguồn;
- tách chính thức / dự thảo / chưa chốt;
- kiểm ngày, phạm vi, con số, điều kiện;
- lập sổ nguồn;
- xác định điều không được phép khẳng định.

### Output
- sự thật trung tâm;
- điều đã chắc;
- điều chưa chắc;
- giới hạn dữ liệu.

### PREMISE RECHECK — chỉ kích hoạt khi factual research làm thay đổi lý do topic được chọn

Sau khi xác minh sự thật, AI phải so kết quả R1 với premise lúc shortlist.

Tự hỏi:

> **Research vừa rồi có làm suy yếu đáng kể Actual Novelty, Why Now, Stakes hoặc Natural Tension khiến topic được chọn không?**

Ví dụ:

- tưởng có chức năng mới → thực ra chức năng đã tồn tại;
- tưởng nghĩa vụ mới → thực ra chỉ là nhắc lại;
- tưởng thay đổi áp dụng rộng → thực ra phạm vi rất hẹp;
- tưởng có deadline mới → thực ra deadline không đổi.

Nếu **không**:

> tiếp tục flow R1 bình thường.

Nếu **có**:

chạy **TOPIC STRENGTH RECHECK** ngay.

Output rất ngắn:

- Actual novelty sau verify
- Why now sau verify
- Stakes
- Natural tension
- Likely route mới
- Recommendation

Nếu topic vẫn Route A:

> tiếp tục **R1 Gate bình thường**, không tạo checkpoint riêng cho Premise Recheck.

Nếu topic rơi rõ xuống Route B hoặc C và không còn phù hợp mục tiêu content ưu tiên:

> **không tiếp tục R2 → R4 theo quán tính.**

Trình user recommendation sớm.

Với bare `OK`, thực hiện recommendation đang được AI đề xuất.

### Gate
> **DỮ KIỆN CỐT LÕI ĐÃ CHẮC** → dừng chờ OK, trừ khi PREMISE RECHECK đã kích hoạt route change cần user quyết định.

---

## R2 — Người đọc

### Đọc
- ktdt-research-workflow.md

### Khóa
- người đọc chính;
- tình huống thật;
- họ đang nghĩ gì;
- họ lo / hỏi / quyết định gì;
- khoảng cách nhận thức;
- dangerous misunderstanding;
- useful action.

### Gate
Phải trả lời được:

> **Bài này đang nói với ai, họ đang nghĩ gì và tại sao họ phải quan tâm?**

Dừng chờ OK.

---

## R3 — Nội dung cạnh tranh cho platform đầu tiên

### Đọc
- ktdt-research-workflow.md
- ktdt-platform-competitor-research.md

Trong full workflow, platform đầu tiên = Facebook.

### Làm
- nghiên cứu platform đích;
- tách organic / paid nếu cần;
- không dùng đối thủ để xác nhận luật;
- không gọi hiệu quả / viral nếu thiếu dữ liệu;
- tìm content gap.

### Gate
Khóa:

- phần đã bão hòa;
- pattern quan sát được;
- giới hạn dữ liệu;
- ít nhất một khoảng trống đáng thử.

Dừng chờ OK.

---

## R4 — Cơ hội + Research Package + Content Worthiness

### Đọc
- ktdt-research-workflow.md
- ktdt-research-output.md

### Làm
Đóng gói:

- source package;
- truth;
- evidence boundary;
- audience;
- situation;
- reader question;
- tension;
- misunderstanding;
- useful action;
- observed gap;
- opportunity;
- content promise;
- time-sensitive fields.

Sau khi đóng gói Research Package, AI phải trả lời **hai câu hỏi khác nhau**.

### GATE 1 — RESEARCH SUFFICIENCY

> **Dữ kiện đã đủ chắc để ra quyết định chưa?**

Chỉ có:

- **PASS**
- **FAIL**

Nếu FAIL:

> **❌ CHƯA ĐỦ DỮ KIỆN**

và nói rõ còn thiếu gì.

### GATE 2 — CONTENT WORTHINESS

Chỉ chạy nếu Research Sufficiency = PASS.

Hỏi:

> **Với những gì research vừa chứng minh, topic này đáng đầu tư content ở mức nào?**

Đánh giá qualitative:

- Actual novelty
- Why now
- Stakes
- Natural tension
- Cold-attention potential
- Strategic / utility value
- Paid-traffic suitability

**Paid-traffic suitability không phải dự đoán ads sẽ thắng.**

Nó chỉ trả lời:

> topic này có đủ lý do để đáng ưu tiên đem đi test với cold audience hay không.

Không được nói “quảng cáo sẽ hiệu quả” nếu chưa có dữ liệu thực.

**Kiểm lại framing trước khi chốt Route — nội bộ:**

Nếu topic mạnh nhưng framing ban đầu có nguy cơ gây hiểu sai về quy định hoặc hình ảnh Diệu Tâm, **ưu tiên sửa framing, không tự động hạ Route A**. Giữ Route A khi sức nặng thực của topic vẫn đủ sau khi sửa.

Ghi ngắn trong Content Case **cách đặt vấn đề nên dùng và ý diễn đạt cần tránh**, để S2/Hook Facebook/Title và cover TikTok không quay lại framing đã loại chỉ nhằm tăng attention. Giữ đủ chủ thể, điều kiện, giới hạn pháp lý đã xác minh; framing không được dùng để che một claim sai.

Nếu sau khi sửa framing, topic không còn đủ sức hút như đánh giá ban đầu, **đánh giá lại Route A/B/C**. Không tạo gate duyệt riêng cho user.

### RECOMMENDED ROUTE

**ROUTE A — PRIORITY / TRAFFIC CANDIDATE**

Topic đủ mạnh để tiếp tục full production:

> Research → Facebook → TikTok

và có thể cân nhắc làm creative để test cold traffic.

Một topic đặc biệt mạnh có thể gọi là **Hero Topic**, nhưng Hero chỉ là nhãn nhấn mạnh bên trong Route A, không tạo workflow riêng.

---

**ROUTE B — UTILITY / STRATEGIC ORGANIC**

Topic:

- đúng;
- hữu ích;
- có giá trị giáo dục/search/trust/chăm audience;

nhưng attention/stakes/Why Now chưa đủ mạnh để ưu tiên paid traffic hoặc production lớn.

Route B **không phải bài dở**.

Nếu mục tiêu là organic utility hoặc strategic education:

> có thể tiếp tục.

Nếu mục tiêu hiện tại là tìm topic chủ lực/cold traffic:

> khuyến nghị lưu topic này vào utility backlog và quay lại shortlist chọn topic mạnh hơn.

---

**ROUTE C — DEPRIORITIZE**

Topic có thể đúng nhưng:

- actual novelty thấp;
- Why Now yếu;
- stakes thấp;
- tension thấp;
- strategic value không đủ;

nên không đáng tiếp tục tốn production lúc này.

> **Dừng topic và quay lại shortlist.**

---

Guardrail:

> **Stakes thấp một mình không đủ để đưa topic vào Route C.**

Topic giáo dục hoặc trust-building có strategic value rõ phải được giữ ở Route B thay vì bị loại chỉ vì nó không gây đau.

### Sau R4

**Research FAIL**

→ dừng / research thêm.

**Research PASS + Route A**

→ dừng chờ OK; OK chạy S1.

**Research PASS + Route B**

→ AI đưa recommendation:

- tiếp tục nếu mục tiêu là utility/education/strategic organic;
- quay lại shortlist nếu đang tìm priority/traffic topic.

Bare `OK` = làm theo recommendation.

**Research PASS + Route C**

→ không chạy S1;

→ quay lại shortlist và recommend candidate tiếp theo.

> **Một topic bị NO-GO production sau research vẫn là một kết quả research thành công.**

---

# 7. CHỌN CÁCH ĐÁNH CHUNG

## S1 — Mục tiêu

Đề xuất một mục tiêu chính, tối đa một mục tiêu phụ.

Dừng chờ OK.

## S2 — Góc chính

Dùng Research Package + mục tiêu đã khóa.

Đề xuất góc mạnh nhất và lý do ngắn.

Trước khi khóa góc, xác định **giá trị chính người đọc cần nhận**: hiểu một kết luận, tự đối chiếu trường hợp hay thực hiện một việc. Nếu bài hứa hướng dẫn/tự kiểm, ưu tiên góc giúp người đọc **biết cách làm**, không chỉ biết vì sao nên làm.

Chưa viết hook.

Dừng chờ OK.

Sau S2:

- full workflow / Facebook-only → Facebook Production;
- TikTok-only → TikTok T0.

---

# 8. FACEBOOK PRODUCTION

## F1 — Format

### Đọc
- ktdt-facebook-post-playbook.md

Mặc định đề xuất:

- 1 ảnh;
- 3 ảnh.

AI khuyến nghị theo số bước nhận thức, không theo lượng thông tin.

Dừng chờ OK.

---

## F2 — Hook

### Đọc đồng thời
- ktdt-social-writing-dna.md
- ktdt-hook-language-psychology.md

### Làm
- xác định **lý do đúng người đọc cần quan tâm**: câu hỏi cần giải đáp, thông tin/việc cần làm hữu ích, hoặc mâu thuẫn thật;
- giữ chi tiết gánh lực; **nếu có tension thật** thì giữ conflict-bearing words, không ép bài hướng dẫn/cập nhật thành cảnh báo;
- tạo 3–5 hook;
- trước khi chọn #1, thử chuyển xuống câu sau mọi context không trực tiếp tạo lực cho Hook và kiểm tra câu có giống điều người đọc tự nghĩ/nói hay không;
- đề xuất #1.

Dừng chờ OK.

---

## F3 — Retention path

### Đọc
- ktdt-social-writing-dna.md
- ktdt-body-writing-retention.md

Chỉ dựng xương sống:

- hook mở món nợ gì;
- trả sớm thế nào;
- thứ tự tò mò;
- điều chắc / hiểu sai / việc cần làm.

Với bài hướng dẫn/tự kiểm: đưa cách thực hiện, điều kiện và bước tiếp theo **đã xác minh** lên sớm; không kéo dài bằng nhiều đoạn lặp lại lý do cần cảnh giác.

Dừng chờ OK.

---

## F4 — CTA

- Chọn **một hành động chính** phù hợp mục tiêu: lưu / gửi / theo dõi / bình luận / nhắn / không CTA.
- CTA phải cho người đọc một **lý do cụ thể** để làm hành động đó.
- **Không dùng CTA để tóm tắt hoặc giải thích lại bài**; nếu cần câu chốt nội dung/factual note, tách riêng.
- Với bài thuần thông tin, có thể không thêm CTA nếu bài đã có kết thúc tự nhiên; không mặc định bán dịch vụ.

Dừng chờ OK.

---

## F5 — Viết caption hoàn chỉnh

### Đọc
- DNA
- body/retention
- Facebook playbook

### Luật
- giữ decision lock;
- hook không tự đổi;
- hook debt phải được trả sớm;
- nói với một người thật trong tình huống thật;
- cụ thể khi có thể;
- CTA đúng bản đã khóa.

Đưa bản viết và dừng chờ OK.

---

## F6 — Đóng gói Facebook

### Đọc
- Facebook playbook

Output:

1. chữ trên ảnh;
2. caption;
3. 3–5 hashtag đã research phù hợp.

Emoji chủ yếu ở caption; không mặc định emoji trên ảnh.

Dừng chờ OK.

---

## F7 — QA text

AI tự kiểm:

- factual;
- evidence boundary;
- hook debt;
- câu mơ hồ;
- giọng có hơi người;
- spacing / emoji / CTA / hashtag;
- chữ ảnh khớp caption;
- **giá trị chính đến đủ sớm**; nếu bài hứa hướng dẫn/tự kiểm, người đọc có biết cách làm bằng các bước đã xác minh không; có đoạn nào chỉ nhắc lại cùng một cảnh báo không.

Nếu đạt:

> **TEXT ĐÃ ĐỦ CHUẨN ĐỂ TẠO ẢNH**

Dừng chờ OK.

---

## F8 — Concept ảnh

### Đọc
- Facebook playbook

Tóm tắt:

- số ảnh;
- tỷ lệ;
- exact text;
- phong cách;
- màu nếu đã có;
- logo có dùng không;
- vị trí logo nếu dùng;
- tài sản tham chiếu.

Dừng chờ OK.

---

## F9 — Generate + QA ảnh

Khi user OK concept:

> **tạo ảnh ngay, không hỏi lại các điểm đã khóa.**

Nếu có tool ảnh, phải tạo ảnh thật.

QA:

- tỷ lệ;
- mobile readability;
- exact text;
- dấu tiếng Việt;
- logo đúng nếu có;
- không chi tiết thừa;
- vùng thở;
- visual hợp mục tiêu.

Lỗi khách quan rõ → tự sửa trước khi bàn giao nếu không cần mở decision lock.

---

## F10 — Facebook Handoff

Bàn giao:

1. ảnh hoàn chỉnh;
2. chữ trên ảnh;
3. caption;
4. hashtag;
5. factual note nếu còn điểm đang chờ.

Bài Facebook chỉ Complete khi:

- ảnh đã tạo + QA;
- hoặc user chủ động yêu cầu dừng ở text.

Khi user duyệt bản Facebook cuối:

> **FACEBOOK COMPLETE**

### Nếu Facebook-only
Content case có thể kết thúc.

### Nếu full workflow
User nói OK ở bản Facebook cuối đồng nghĩa:

1. khóa Facebook;
2. tạo TikTok inheritance handoff;
3. chạy TikTok T0 nội bộ;
4. đưa T1 ở turn kế tiếp.

Không hỏi:

> “Có muốn tiếp tục TikTok không?”

---

# 9. FACEBOOK → TIKTOK INHERITANCE

**Mặc định Facebook hoàn thành trước TikTok.** Nếu đã có Research Core và bài Facebook được duyệt, dùng chúng làm **bản gốc nội dung**, không mở một quy trình nghiên cứu và viết mới.

- **Kế thừa:** facts, nguồn, đối tượng, kết luận, điều kiện/ngoại lệ, giới hạn bằng chứng, cách hướng dẫn, hook/câu chữ/CTA đã tốt.
- **Điều chỉnh khi cần:** Title, Slide 1, phân chia slide, nhịp caption, hashtag, visual. Giữ nguyên câu chữ tốt nếu vẫn phù hợp.
- **Chỉ nghiên cứu bổ sung phần thiếu hoặc có khả năng thay đổi.** Không tự nghiên cứu lại đối thủ, nền tảng hay toàn bộ chủ đề chỉ để chuyển thể.
- **Nếu TikTok-only:** dùng Research Core chung vừa hoàn tất, không cần Facebook assets.

> **Giữ chất lượng đã được duyệt; đổi cách trình bày khi người xem TikTok thực sự được lợi.**

Quy tắc viết và QA ở docs/platform/ktdt-tiktok-writing-playbook.md.

---

# 10. TIKTOK PHOTO CAROUSEL

### Đọc trước khi production
- docs/platform/ktdt-tiktok-writing-playbook.md
- Research Core và bài Facebook đã duyệt, nếu có.
- docs/research/ktdt-platform-competitor-research.md **chỉ khi phát sinh nhu cầu nghiên cứu nền tảng/đối thủ**, không phải mặc định.

## T0 — Inherit + kiểm phần chênh lệch — INTERNAL

**Không xin OK.**

- Xác định Research Core và bài Facebook hoàn chỉnh đã được duyệt để tái sử dụng.
- Kế thừa nội dung đã chốt. Nếu nguồn hoặc thông tin theo thời điểm có dấu hiệu thay đổi, chỉ xác minh lại phần bị ảnh hưởng.
- Xác định **điều cốt lõi người xem phải biết, hiểu hoặc làm được** từ Content Case/S2 và bài Facebook. Không đặt Depth Target riêng.
- Chỉ nghiên cứu chênh lệch TikTok khi cần cho search/title, format hoặc giới hạn kỹ thuật. **Không làm lại research/SEO/competitor** chỉ vì đổi nền tảng.

Nếu TikTok-only, dùng Research Core chung vừa hoàn tất rồi tiếp tục.

## T1 — Title + Carousel Structure — xin OK

### Output user thấy
- Title TikTok khuyến nghị;
- số slide và nhiệm vụ/nội dung chính của từng slide;
- lý do ngắn vì sao cách chia dễ xem và **không làm mất giá trị gốc**.

**Title và Slide 1 khác nhiệm vụ nhưng cùng lời hứa.** Được phép giống/gần giống câu chữ khi hiệu quả. Không ép số slide, không bịa hook khác để tỏ ra mới.

AI tự kiểm: nếu chỉ vuốt slide, người xem sẽ nhận đủ ý/bước thiết yếu của bài Facebook chưa? Điều kiện, mốc, hướng dẫn quan trọng có chỗ chưa? Không viết Caption ở T1.

User OK → khóa Title, số slide và nhiệm vụ từng slide; chạy T2 ngay.

## T2 — Exact Slide Copy — xin OK

### Đọc
- TikTok playbook;
- Brand DNA/hook/body khi cần cho câu chữ.

Viết exact text Slide 1 → Slide n, đọc tốt trên điện thoại.

- Giữ **tên mục, thao tác, con số, điều kiện, ngoại lệ, kết luận thiết yếu**; không thay bằng khẩu hiệu chung chỉ để ít chữ.
- Mỗi slide trọn một ý/bước hữu ích, không phải caption bị cắt ngẫu nhiên.
- Không ép mâu thuẫn; nếu tension thật có sức nặng thì giữ chi tiết quan trọng.
- Không tự thêm claim hay làm mạnh hơn bằng chứng.
- So với Facebook đã duyệt, **không làm rơi thông tin quan trọng** khi chuyển thành carousel.

User OK → khóa exact slide copy và chạy T3A ngay.

## T3A — CAPTION DRAFT — xin OK hướng

**Mặc định bắt đầu từ caption Facebook đã duyệt**, nếu có. Có thể kế thừa gần nguyên văn khi đã rõ, đúng và phù hợp TikTok. Chỉ biên tập chỗ thật sự giúp đọc tốt hơn.

Caption Draft phải:
- trả lời điều Title/Slide 1 hứa; đưa giá trị chính lên sớm;
- **đủ rõ khi đọc riêng**, kể cả bước/điều kiện cốt lõi đã xuất hiện trên slide;
- giữ căn cứ, giới hạn pháp lý và cách diễn đạt đã xác minh;
- tránh ý lặp, cảnh báo giả, hoặc viết khác Facebook chỉ để tạo mới;
- có CTA/hashtag phù hợp, không ép độ dài hay chiều sâu bổ sung.

Draft phải đáng dùng ngay, không cố viết nông để chờ T3B.

### Output user thấy
**Block 1 — Tiêu đề TikTok**

**Block 2 — Caption Draft + hashtag**

User OK → **SOFT LOCK:** duyệt hướng caption, không khóa nguyên văn; chạy T3B ngay ở lượt tiếp.

---

## T3B — FINAL EDITORIAL REVIEW — xin OK final

Đây vẫn là **một lượt riêng với T3A** để AI đóng vai biên tập, **không phải lượt bắt buộc viết lại để khác**.

Đọc đối chiếu Research Core, bài Facebook đã duyệt (nếu có), Title, exact carousel, Caption Draft.

**Chạy bốn câu hỏi biên tập của TikTok playbook**:
1. Đúng nhu cầu và lời hứa Title/Slide 1?
2. Đủ thông tin thiết yếu khi chỉ xem slide hoặc chỉ đọc caption?
3. Rõ, tự nhiên, không lặp hoặc cắt mất chi tiết thực tế?
4. Đúng nguồn và giới hạn bằng chứng, không tạo claim mới thiếu căn cứ?

Nếu có lỗi → **sửa đúng chỗ sai**; nếu Draft đã tốt → giữ nguyên hoặc chỉnh rất ít. Không tạo Depth Target, Knowledge Gain Delta hoặc mental model chỉ để đạt PASS. Không tự tuyên bố đạt nếu thiếu giá trị thiết yếu.

Nếu exact slide copy đã khóa có lỗi factual hoặc thiếu dữ liệu thiết yếu đến mức gây hiểu sai/hụt lời hứa, **không âm thầm sửa slide đã khóa**: báo đúng chỗ cần mở lại theo Decision Lock.

Chỉ trình khi đạt tiêu chuẩn QA nội dung, với nhãn nội bộ:

> **CAPTION EDITORIAL PASS**

### Output user thấy
Một dòng ngắn: **Bản caption sau biên tập cuối**

**Block 1 — Tiêu đề TikTok**

**Block 2 — Caption Final + hashtag**

Không dump checklist QA. User OK → HARD LOCK exact Caption/CTA/hashtag; sang T4.

---

## T4 — Visual Concept — xin OK

Đề xuất gọn tỷ lệ, concept, typography, bố cục, độ dễ đọc và cách thể hiện exact slide copy đã khóa.

Mặc định **9:16, không logo, không tên thương hiệu trên ảnh**. Không khóa template/màu/font cho mọi bài; cùng bộ ảnh có hệ thị giác nhất quán nhưng bố cục từng slide có thể khác.

User OK → tạo toàn bộ carousel ở T5; không hỏi lại từng slide.

---

## T5 — Generate + QA + TikTok Handoff

AI tự:
1. tạo toàn bộ carousel theo thứ tự đã duyệt;
2. QA exact text, dấu tiếng Việt, số, căn cứ, khả năng đọc trên điện thoại, contrast, safe zone;
3. QA mạch nội dung, không thiếu bước hoặc slide chỉ lặp vô ích;
4. sửa lỗi khách quan rõ trước khi bàn giao;
5. bàn giao **bộ ảnh + Block Title + Block Caption Final (chữ ký/nguồn/hashtag)**.

Không tự thêm logo/tên thương hiệu lên ảnh. Với ảnh AI, nhắc user kiểm tra yêu cầu gắn nhãn nội dung AI của TikTok khi đăng.

Sau handoff: **CONTENT CASE COMPLETE**, trừ khi user yêu cầu nền tảng khác.

---

# 11. LUẬT VIẾT CỨNG

Áp dụng xuyên suốt:

> **Câu chữ không được mạnh hơn bằng chứng.**

> **Đúng và dễ hiểu chưa đủ. Nội dung Diệu Tâm cần có cảm giác đang nói với một người thật trong một tình huống thật.**

> **Nếu người đọc có thể hỏi “cụ thể là gì?”, hãy nói cụ thể ngay khi có thể.**

> **Hook mở món nợ nào, thân bài/caption trả món nợ đó sớm.**

> **Nếu chọn hook dựa trên tension thật, giữ những từ đang gánh mâu thuẫn; không bịa tension khi một câu hỏi/việc thực tế đã đủ hấp dẫn.**

> **Đơn giản không phải cắt nhiều. Đơn giản là chỉ giữ những thứ đang làm việc.**

> **Carousel và Caption đều phải truyền tải đủ giá trị cốt lõi khi xem/đọc riêng. Được lặp thông tin thiết yếu giữa hai phần; không sao chép máy móc, không ép tạo lớp kiến thức mới để khác nhau.**

> **Đừng chỉ cho người đọc kết luận. Hãy cho họ cách hiểu để tự đi đến kết luận đúng.**

> **Chiều sâu phải đến từ logic đã được nghiên cứu, không đến từ việc AI tự suy thêm.**

**Chữ ký thương hiệu — bắt buộc cho mọi bài đăng hoàn chỉnh:** Khi bàn giao nội dung xuất bản Facebook, Final Caption TikTok và sau này là phần mô tả/bài đăng YouTube, Zalo OA, AI phải chèn **đúng nguyên văn chữ ký hai dòng đã khóa trong `docs/brand/ktdt-social-writing-dna.md`**. Đặt sau nội dung/CTA, trước căn cứ/ngày cập nhật/hashtag nếu có. **Không tự chèn vào ảnh, slide, cover, thumbnail, Title hoặc lời thoại.** Áp dụng khi tạo bản nội dung hoàn chỉnh để user duyệt và ở final handoff; không ép vào research hoặc outline.

Không dùng cảm xúc giả bằng “sốc”, “siêu nóng”, “cực kỳ quan trọng” nếu tình huống thật đã đủ lực.

Ưu tiên tension từ:

> **tiền thật + deadline thật + hồ sơ thật + quyền lợi thật + câu hỏi thật.**

---

# 12. LUẬT NGHIÊN CỨU CỨNG

Không dùng đối thủ, social hoặc comment để xác nhận luật.

Ưu tiên:

> **văn bản pháp lý gốc / cơ quan có thẩm quyền → nguồn chuyên môn đáng tin → báo chí → đối thủ / mạng xã hội**

Trong nguồn chính thức:

> **văn bản gốc có trọng số cao hơn bài giải thích về văn bản.**

Không:

- trộn dự thảo với quy định hiện hành;
- biến khả năng thành chắc chắn;
- suy thủ tục chưa ban hành;
- bịa dữ liệu;
- gọi nội dung hiệu quả chỉ vì thấy nó tồn tại.

---

# 13. SƠ ĐỒ FILE → FLOW

| Flow | File bắt buộc |
|---|---|
| AUTO-START | research workflow + source verification khi cần |
| R1 Sự thật | research workflow + source verification |
| R2 Người đọc | research workflow |
| R3 Cạnh tranh | research workflow + platform competitor research |
| R4 Research Package | research workflow + research output |
| S1–S2 | Research Package + DNA khi cần |
| F1 | Facebook playbook |
| F2 | DNA + hook psychology |
| F3–F5 | DNA + body/retention |
| F6–F10 | Facebook playbook + DNA/body khi cần |
| T0 | TikTok playbook + Research Core/bài Facebook; competitor research khi thực sự cần |
| T1–T2 | TikTok playbook + DNA/hook/body khi cần |
| T3A | TikTok playbook + DNA + body/retention |
| T3B | TikTok playbook + Research Core + exact carousel + Caption Draft |
| T4 | TikTok playbook |
| T5 | TikTok playbook + image tool nếu có |

---

# 14. PHẠM VI HIỆN TẠI

Đã test thực tế:

- hot-topic research;
- factual / reader / competition / opportunity research;
- DNA / hook / retention;
- Facebook image post;
- Facebook visual generation + QA;
- Facebook → TikTok selective inheritance;
- TikTok Photo Carousel writing + visual workflow qua một case thật.

Chưa khóa hoàn chỉnh:

- TikTok video production;
- Zalo;
- YouTube;
- hệ visual identity toàn diện;
- campaign/ad set/placement;
- vòng học từ dữ liệu chính chủ;
- multi-platform QA ngoài Facebook → TikTok.

Không nâng một lesson chưa được kiểm chứng thành luật cứng chỉ vì nó xuất hiện một lần.

---

# 15. CÂU CĂN CHỈNH CHO AI

> **Research một lần cho Content Case. Khi có Facebook được duyệt, TikTok kế thừa nội dung và câu chữ đang hiệu quả, không nghiên cứu hoặc viết lại từ đầu. Chỉ chuyển cách đóng gói: Title/Slide 1 đúng lời hứa, carousel dễ vuốt mà đủ bước và caption đủ rõ khi đọc riêng. Thông tin quan trọng được phép xuất hiện ở cả carousel lẫn caption; không bắt buộc tạo Knowledge Gain Delta/Depth Target. T3A duyệt hướng, T3B biên tập độc lập để sửa lỗi thực sự chứ không viết lại cho khác. Chỉ sau khi user OK Final Caption mới làm hình. Giữ đúng bằng chứng và chữ ký thương hiệu.**