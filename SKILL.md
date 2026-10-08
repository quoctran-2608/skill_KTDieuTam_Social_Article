# KẾ TOÁN DIỆU TÂM — SOCIAL CONTENT SKILL

**Phiên bản:** 0.16  
**Ngày:** 08/10/2026  
**Vai trò:** Runtime orchestrator cho content case đa nền tảng  
**Trạng thái:** Đang phát triển — Facebook dạng ảnh đã test thực tế; TikTok Photo Carousel v0.5 đang thử nghiệm sau lesson Depth & Voice từ case thật; TikTok video production chưa khóa.

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
5. AI phải chuyển vai từ **writer → editor/reviewer** và chạy ngay **T3B — Depth & Voice Review** ở turn kế tiếp.

Sau T3A, AI vẫn được phép sửa:

- opening;
- câu chữ;
- thứ tự đoạn;
- độ dài;
- mức giải thích;
- ví dụ/tình huống;
- mental model;
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
- main tension;
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

Đề xuất CTA chính phù hợp mục tiêu; với bài thuần thông tin, có thể đề xuất **không thêm CTA kêu gọi tương tác** nếu bài đã có kết thúc tự nhiên.

Không mặc định bán dịch vụ.

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

Sau FACEBOOK COMPLETE, AI tự lập nội bộ:

## INHERIT FROM CONTENT CASE
- Facts: locked
- Sources: reusable
- Audience: locked
- Situation: locked
- Core tension: locked
- Evidence boundary: locked
- Dangerous misunderstanding: locked
- Useful action: reusable
- Approved angle: reusable

## ELIGIBLE FACEBOOK ASSETS
- approved hook;
- approved wording;
- explanation user đã duyệt;
- misunderstanding xử lý tốt;
- CTA insight;
- những từ đang gánh mâu thuẫn.

## REOPEN FOR TIKTOK
- search wording;
- Title;
- cover hook;
- carousel architecture;
- exact slide copy;
- Caption treatment;
- CTA wording;
- hashtag;
- visual concept.

Nguyên tắc:

> **Không sáng tạo lại chỉ để chứng minh TikTok khác Facebook. Cái gì vẫn làm việc thì được reuse.**

Nhưng:

> **Research inheritance ≠ packaging inheritance.**

Không mặc định bê:

- caption Facebook nguyên văn;
- số ảnh;
- tỷ lệ;
- logo;
- visual;
- emoji;
- CTA wording;
- cách chia đoạn.

---

# 10. TIKTOK PHOTO CAROUSEL

### Bắt buộc đọc trước TikTok production
- docs/platform/ktdt-tiktok-writing-playbook.md
- docs/research/ktdt-platform-competitor-research.md

## T0 — Inheritance + Platform Delta Research — INTERNAL

Không xin OK.

Nếu adaptation mode:

- dùng Research Core;
- dùng approved Facebook assets có chọn lọc;
- kiểm freshness của time-sensitive fields;
- không full research lại.

Nếu standalone:

- dùng Research Core vừa hoàn tất;
- không có Facebook assets thì bỏ qua phần đó.

Delta Research chỉ tìm:

- search intent;
- keyword;
- Title treatment;
- cover behavior;
- carousel architecture;
- slide-count hypothesis;
- TikTok-specific gap;
- hashtag candidates;
- platform-specific CTA/visual clue.

### DEPTH TARGET — internal

Trong T0, AI phải xác định một câu:

> **Sau khi người đọc đã xem hết carousel, điều gì họ vẫn cần hiểu sâu hơn để có thể suy nghĩ hoặc tự kiểm đúng?**

Depth Target có thể tập trung vào:

- mechanism — cơ chế;
- condition — điều kiện làm kết luận thay đổi;
- implication — kết luận đó có nghĩa gì trong thực tế;
- exception — trường hợp nào khác đi;
- decision model — phải nhìn các biến theo thứ tự nào;
- how-to-check — tự xác định trường hợp của mình ra sao.

Không bắt buộc mọi bài phải có causal `WHY`.

Với bài deadline/thủ tục/update, Depth Target có thể là:

> **WHAT CHANGES / WHO IT CHANGES FOR / HOW TO CHECK / WHAT TO DO NEXT**

Depth Target phải xuất phát từ Research Core hoặc dữ kiện đã verify.

> **Không được tạo “chiều sâu” bằng suy đoán mục đích chính sách, nguyên nhân hoặc logic không có bằng chứng.**

Nếu TikTok trực tiếp khó truy cập, dùng fallback trong competitor research và ghi:

> **Suy luận chéo nền tảng — không phải bằng chứng hiệu quả trên TikTok.**

Không dừng workflow chỉ vì không đọc được TikTok trực tiếp.

---

## T1 — Title + Carousel Structure

### Output user thấy
- Title khuyến nghị;
- số slide;
- nhiệm vụ từng slide;
- lý do ngắn vì sao cấu trúc đó hợp.

Chưa viết Caption.

Rule:

> **Title ≠ Slide 1 Hook.**

Title ưu tiên search/nhận diện.  
Slide 1 ưu tiên dừng/kéo vuốt.

AI phải tự kiểm thêm:

- các slide có dẫn đúng tới Depth Target không;
- carousel đã đủ để hiểu vấn đề cơ bản chưa;
- phần nào nên để Caption giải thích sâu hơn thay vì nhồi lên slide.

Depth Target **không tạo checkpoint riêng cho user**.

User OK → khóa:

- Title;
- số slide;
- nhiệm vụ slide;

và chạy T2 ngay.

---

## T2 — Exact Slide Copy

### Đọc
- TikTok playbook
- DNA
- hook language
- body/retention khi cần

Viết exact text Slide 1 → Slide n.

Nguyên tắc:

- mỗi slide = một bước nhận thức;
- slide không phải caption thu nhỏ;
- giữ conflict-bearing words;
- không cắt chỉ để ngắn;
- Slide 1 kéo;
- slide giữa giải;
- slide cuối giúp hành động;
- không cố nhét toàn bộ Depth Target lên slide.

> **Slide ngắn không phải vì TikTok cần ít chữ; slide ngắn vì mỗi slide chỉ nên gánh một bước nhận thức.**

User OK → khóa toàn bộ chữ carousel và chạy T3A.

---

## T3A — CAPTION DRAFT

AI viết Caption TikTok bản đầu dựa trên:

- Research Core;
- TikTok Delta Research;
- Depth Target;
- Title đã khóa;
- exact carousel đã khóa.

AI tự xử lý nội bộ:

- keyword;
- CTA;
- hashtag research;
- spacing;
- emoji;
- factual correctness;
- evidence boundary.

Caption Draft vẫn phải là một bản **đáng dùng**, không được cố tình viết sơ sài chỉ vì còn T3B phía sau.

Caption phải:

- nói với đúng người;
- trả hook debt sớm;
- không copy carousel nguyên văn;
- không copy/cắt Facebook máy móc;
- có actionable value;
- không mạnh hơn bằng chứng.

### Output user thấy

**Block 1 — Tiêu đề TikTok**

**Block 2 — Caption Draft + hashtag**

### Gate

User `OK` ở T3A:

> **không khóa nguyên văn Caption.**

Nó chỉ xác nhận:

> **HƯỚNG CAPTION ĐÚNG — CHUYỂN SANG DEEP REVIEW**

Sau đó AI phải chạy T3B ở turn kế tiếp.

---

## T3B — DEPTH & VOICE REVIEW + REWRITE

Ở checkpoint này AI phải đổi vai:

> **Writer → Editor / Reviewer**

Không cố bảo vệ Caption Draft.

Hãy coi Draft là bài của một người khác và hỏi:

> **“Tại sao người đọc có thể thấy bài này đúng nhưng vẫn chưa đáng đọc?”**

AI phải review lại:

- Research Core;
- Depth Target;
- toàn bộ carousel đã khóa;
- Caption Draft.

Sau đó kiểm 5 gate:

### G1 — NEW VALUE

> **Nếu người đọc đã xem hết carousel, họ còn học thêm được gì khi đọc Caption?**

Nếu câu trả lời chỉ là:

> “cùng thông tin nhưng chi tiết hơn”

→ FAIL.

Caption phải tạo một **Knowledge Gain Delta** thật.

### G2 — UNDERSTANDING

Caption có giúp người đọc hiểu thêm ít nhất một lớp phù hợp không:

- mechanism;
- condition;
- implication;
- exception;
- decision logic;
- how-to-check.

Không bắt mọi bài phải trả causal `WHY`.

Nếu có hiểu lầm cốt lõi, không chỉ phủ định. Khi evidence cho phép, phải chỉ ra:

- cách hiểu đó thiếu ở đâu;
- đang bỏ sót biến nào;
- logic đúng thay thế là gì.

### G3 — SELF-APPLICATION

Sau khi đọc, người đọc có biết:

> **“Tôi phải nhìn vào đâu để biết trường hợp của mình?”**

hoặc:

> **“Tôi nên kiểm các biến theo thứ tự nào?”**

Mục tiêu là cho người đọc một **mental model**, không chỉ một kết luận để nhớ.

### G4 — HUMAN VOICE

Bỏ Title và hashtag đi.

Caption nghe giống:

- **A. một người có chuyên môn đang giải thích trực tiếp cho khách hàng**;
- hay **B. tài liệu tổng hợp / công văn / AI summary**?

Nếu nghiêng về B → FAIL.

Khi tình huống là nguồn tension chính, ưu tiên:

> **Situation → explanation**

Nếu search intent cần câu trả lời trực tiếp, có thể:

> **Answer → situation → explanation**

### G5 — ECONOMY + EVIDENCE

> **Mỗi đoạn phải kiếm được quyền tồn tại.**

Một đoạn dài phải thêm ít nhất một việc:

- mechanism / WHY;
- condition;
- implication;
- misunderstanding;
- mental model;
- action.

Nếu chỉ đổi cách nói → cắt.

**Trước khi thêm lời dẫn hoặc đào sâu:** với bài hướng dẫn/tự kiểm, thông tin giúp người đọc thực hiện hay tự đối chiếu **đã xác minh** có đến đủ sớm chưa? Nếu carousel đã chứa thao tác, Caption có tạo lớp hiểu mới thay vì lặp lại không?

**Cắt** câu chỉ nhắc lại lý do cần quan tâm, cảnh báo hoặc trấn an mà không thêm thông tin, điều kiện, giới hạn hay hành động mới. **Không cắt** lưu ý thực sự cần để tránh hiểu sai và giữ đúng bằng chứng.

Mọi phần “sâu” phải được Research Core hỗ trợ.

> **Không invent insight để làm bài có vẻ sâu.**

### OPENING BLOCK TEST

Opening block phải tự đứng được.

Nó phải làm ít nhất một việc:

- đặt đúng người vào tình huống;
- trả tension;
- phá assumption;
- hoặc đưa câu trả lời chính.

Không mở bằng:

- “Theo quy định…”;
- “Hiện nay…”;
- “Trong bài viết này…”;

nếu có cách đi thẳng vào vấn đề tốt hơn.

### DEPTH GUARDRAIL

> **Depth = thêm đúng lớp giải thích giúp người đọc hiểu bản chất.**

Không phải:

> **Depth = thêm nhiều kiến thức.**

Không chữa bài nông bằng cách:

- thêm lịch sử;
- thêm toàn bộ căn cứ pháp lý;
- thêm hàng loạt ngoại lệ không liên quan;
- viết thành giáo trình;
- biến Caption TikTok thành bài website.

Rule cắt:

> Nếu cắt một phần mà mất mechanism / condition / evidence boundary / mental model → không cắt.

> Nếu cắt một phần mà người đọc không mất gì → phần đó đang thừa.

### Gate

Chỉ được trình bản T3B khi đạt:

> **CAPTION DEPTH PASS**

Nếu fail một gate quan trọng:

> **AI phải rewrite trước khi trình user.**

Không trình report QA rồi bắt user tự quyết định sửa gì.

### Output user thấy

Một câu rất ngắn:

> **Bản sau Depth & Voice Review**

Sau đó chỉ đưa:

**Block 1 — Tiêu đề TikTok**

**Block 2 — Caption Final + hashtag**

Có thể thêm tối đa 1–2 dòng nói ngắn điểm đã nâng nếu cần, không dump checklist review.

User `OK` tại đây:

- khóa exact Caption;
- khóa exact CTA;
- khóa hashtag;
- chạy T4.

---

## T4 — Visual Concept

Trình bày ngắn:

- tỷ lệ;
- số ảnh;
- hướng visual;
- typography;
- exact text đã khóa.

Default:

> **9:16 + không logo + không tên thương hiệu trên ảnh.**

Không khóa template/màu/font cố định cho mọi bài.

Cùng một carousel phải cùng visual system, nhưng layout từng slide thay đổi theo nhiệm vụ slide.

User OK →

> **tạo toàn bộ carousel ngay.**

Không xin OK từng slide.

---

## T5 — Generate + QA + TikTok Handoff

AI tự:

1. tạo toàn bộ carousel;
2. QA từng slide;
3. QA cả chuỗi;
4. kiểm safe zone;
5. kiểm exact text / dấu / con số;
6. sửa lỗi khách quan rõ ràng;
7. bàn giao theo đúng thứ tự đăng.

### QA từng slide
- đúng decision lock;
- factual;
- mobile-readable;
- contrast;
- safe zone;
- không logo;
- không tên thương hiệu;
- không artifact rõ.

### QA cả chuỗi
1. Slide 1 có kéo Slide 2 không?
2. Slide 2 có trả món nợ Slide 1 chưa?
3. Mỗi slide có thêm một bước hiểu mới không?
4. Có slide lặp không?
5. Bỏ một slide có mất bước hiểu quan trọng không?
6. Slide cuối có hành động rõ không?
7. Visual system có nhất quán không?
8. Có câu nào mạnh hơn bằng chứng không?

### Handoff
- bộ ảnh carousel theo thứ tự;
- Block Title;
- Block Caption + hashtag.

Nếu ảnh được tạo bằng AI, thêm đúng một dòng:

> **Lưu ý khi đăng: ảnh được tạo bằng AI, hãy kiểm tra yêu cầu gắn nhãn nội dung AI của TikTok tại thời điểm đăng.**

Sau handoff:

> **CONTENT CASE COMPLETE**

trừ khi user yêu cầu platform khác.

---

# 11. LUẬT VIẾT CỨNG

Áp dụng xuyên suốt:

> **Câu chữ không được mạnh hơn bằng chứng.**

> **Đúng và dễ hiểu chưa đủ. Nội dung Diệu Tâm cần có cảm giác đang nói với một người thật trong một tình huống thật.**

> **Nếu người đọc có thể hỏi “cụ thể là gì?”, hãy nói cụ thể ngay khi có thể.**

> **Hook mở món nợ nào, thân bài/caption trả món nợ đó sớm.**

> **Nếu chọn hook dựa trên tension thật, giữ những từ đang gánh mâu thuẫn; không bịa tension khi một câu hỏi/việc thực tế đã đủ hấp dẫn.**

> **Đơn giản không phải cắt nhiều. Đơn giản là chỉ giữ những thứ đang làm việc.**

> **Carousel giúp người xem hiểu bài. Caption phải giúp người quan tâm hiểu sâu hơn. Nếu Caption chỉ là carousel được viết thành đoạn văn, Caption chưa hoàn thành nhiệm vụ.**

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
| T0 | TikTok playbook + platform competitor research |
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

> **Research một lần cho content case. Facebook làm trước. TikTok kế thừa có chọn lọc. Khi viết TikTok, carousel giúp người xem hiểu mạch chính; Caption phải tạo thêm một lớp hiểu có giá trị. Caption Draft chưa phải bản khóa: sau khi user OK hướng Draft, AI phải đổi vai sang editor, review chiều sâu và giọng người thật ở checkpoint kế tiếp, rewrite nếu cần, rồi mới trình Final Caption. Chỉ Final Caption được user OK mới đi sang visual. Không biến checklist nội bộ thành công việc của user, nhưng cũng không gộp writer và reviewer vào cùng một lượt khi việc tách vai có thể nâng chất lượng.**
