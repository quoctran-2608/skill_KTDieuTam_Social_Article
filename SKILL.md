# KẾ TOÁN DIỆU TÂM — SOCIAL CONTENT SKILL

**Phiên bản:** 0.9  
**Ngày:** 08/10/2026  
**Vai trò:** Runtime orchestrator cho content case đa nền tảng  
**Trạng thái:** Đang phát triển — Facebook dạng ảnh đã test thực tế; TikTok Photo Carousel v0.2 đã test qua một case Facebook → TikTok thật; TikTok video production chưa khóa.

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

---

# 5. AUTO-START — QUÉT CHỦ ĐỀ NÓNG

Nếu user không cho chủ đề:

### Bắt buộc đọc
- docs/research/ktdt-research-workflow.md
- docs/research/ktdt-source-verification.md khi cần kiểm nhanh

### Cửa sổ
1. ưu tiên 24–72 giờ gần nhất;
2. thiếu ứng viên tốt → mở rộng tối đa 7 ngày;
3. cũ hơn chỉ giữ khi có diễn biến/deadline/thực thi mới.

Nếu có web/search, phải dùng dữ liệu hiện tại.

### Lọc
Một ứng viên mạnh nên đạt ít nhất 4/5:

1. mới / nóng;
2. đúng tệp Diệu Tâm;
3. tác động thực tế;
4. kiểm chứng được;
5. có điểm căng thật.

### Output
Đề xuất 3–5 chủ đề, mỗi chủ đề rất ngắn:

- chuyện gì mới;
- thời điểm;
- ai bị ảnh hưởng;
- vì sao đáng làm;
- tension;
- độ chắc nguồn;
- Nên làm / Có thể làm / Chưa nên làm.

Chọn:

> **KHUYẾN NGHỊ SỐ 1**

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

### Gate
> **DỮ KIỆN CỐT LÕI ĐÃ CHẮC** → dừng chờ OK.

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

## R4 — Cơ hội + Research Package

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

### Gate
Phải kết thúc:

> **✅ ĐỦ DỮ KIỆN ĐỂ CHỌN CÁCH ĐÁNH**

hoặc:

> **❌ CHƯA ĐỦ DỮ KIỆN**

Nếu ✅ → dừng chờ OK.

---

# 7. CHỌN CÁCH ĐÁNH CHUNG

## S1 — Mục tiêu

Đề xuất một mục tiêu chính, tối đa một mục tiêu phụ.

Dừng chờ OK.

## S2 — Góc chính

Dùng Research Package + mục tiêu đã khóa.

Đề xuất góc mạnh nhất và lý do ngắn.

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
- xác định tension;
- giữ conflict-bearing words;
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

Dừng chờ OK.

---

## F4 — CTA

Đề xuất CTA chính phù hợp mục tiêu.

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
3. 5 hashtag đã research phù hợp.

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
- chữ ảnh khớp caption.

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
- slide cuối giúp hành động.

User OK → khóa toàn bộ chữ carousel và chạy T3.

---

## T3 — Caption hoàn chỉnh

AI tự xử lý nội bộ:

- keyword;
- CTA;
- hashtag research;
- spacing;
- emoji;
- factual check;
- evidence boundary.

Caption phải:

- bắt đầu từ người trong tình huống thật khi có thể;
- trả hook debt sớm;
- tách điều chắc / chưa chắc;
- chặn dangerous misunderstanding;
- có actionable value;
- không copy carousel;
- không copy/cắt Facebook máy móc.

### Output user chỉ nhận

**Block 1 — Tiêu đề TikTok**

**Block 2 — Caption TikTok hoàn chỉnh + hashtag ở cuối**

Không tạo block riêng cho keyword / CTA / hashtag.

User OK → khóa Caption/CTA → AI tự QA text → chạy T4.

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

> **Giữ những từ đang gánh mâu thuẫn.**

> **Đơn giản không phải cắt nhiều. Đơn giản là chỉ giữ những thứ đang làm việc.**

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
| T1–T4 | TikTok playbook + DNA/hook/body khi cần |
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

> **Research một lần cho content case. Facebook làm trước. Khi Facebook hoàn tất và user OK, TikTok kế thừa có chọn lọc các sự thật, insight và wording đã được duyệt; chỉ nghiên cứu phần chênh lệch của TikTok. User chỉ cần duyệt những quyết định thật sự đáng duyệt. Mỗi lần user nói OK, khóa quyết định và chạy ngay bước sau. Không biến checklist nội bộ thành công việc của user.**
