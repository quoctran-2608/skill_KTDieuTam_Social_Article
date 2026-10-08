# TIKTOK PHOTO CAROUSEL PLAYBOOK — KẾ TOÁN DIỆU TÂM

**Phiên bản:** 0.5  
**Ngày cập nhật:** 08/10/2026  
**Trạng thái:** Thử nghiệm — bổ sung Depth & Voice Review sau lesson từ case thực tế  
**Phạm vi:** TikTok Photo Carousel gồm Title, chữ từng slide, Caption, Hashtag, concept ảnh, tạo ảnh và QA. Không bao gồm sản xuất video trừ khi user chủ động yêu cầu.

---

# 1. Định nghĩa mặc định

Trong skill này:

> **“Bài viết TikTok” mặc định = TikTok Photo Carousel, không phải video.**

Output hoàn chỉnh gồm:

1. **Tiêu đề TikTok**
2. **Bộ ảnh carousel**
3. **Caption hoàn chỉnh có hashtag ở cuối**

Không tự sinh:

- shot list;
- voiceover;
- cảnh quay;
- B-roll;
- camera angle;
- timeline dựng;
- hướng dẫn edit;

trừ khi user chủ động yêu cầu video TikTok.

Nếu user chỉ nói “làm bài TikTok”, không hỏi lại “caption hay text post?”. Mặc định đi vào Photo Carousel.

---

# 2. Hai chế độ chạy

## 2.1. ADAPTATION MODE — mặc định sau Facebook

Nếu cùng content case đã có Research Core và bài Facebook đã hoàn tất:

> **TikTok phải kế thừa Research Core và các tài sản Facebook đã được duyệt trước khi viết.**

Được kế thừa có chọn lọc:

- verified facts;
- source package;
- audience;
- reader situation;
- core tension;
- evidence boundary;
- dangerous misunderstanding;
- useful action;
- approved angle;
- approved Facebook hook / wording / explanation nếu vẫn phù hợp.

Không được full research lại từ đầu chỉ vì đổi nền tảng.

Chỉ nghiên cứu phần chênh lệch cần cho TikTok:

- search wording;
- title;
- cover;
- carousel architecture;
- slide density;
- caption treatment;
- CTA wording;
- hashtag;
- visual concept.

Nếu phát hiện nguồn mới, xung đột hoặc dữ kiện có khả năng đã thay đổi, chỉ refresh phần bị ảnh hưởng.

Nguyên tắc:

> **Kế thừa sự thật và insight; tái thiết cách kể theo hành vi TikTok.**

Và:

> **Không sáng tạo lại chỉ để chứng minh TikTok khác Facebook. Nếu một câu, insight hoặc cách giải thích đã đúng và vẫn làm việc trên TikTok, được phép kế thừa.**

## 2.2. STANDALONE MODE — TikTok-only

Nếu không có Research Core trước đó, chạy research workflow chung trước rồi mới dùng playbook này.

User không cần tự chọn mode. AI tự xác định từ context.

## 2.3. Depth Target

Sau khi kế thừa Research Core và chạy TikTok Delta Research, AI phải xác định một câu:

> **Người đã hiểu carousel vẫn cần hiểu sâu thêm điều gì để có thể suy nghĩ hoặc tự kiểm đúng?**

Đây là **Depth Target**.

Depth Target:

- không phải hook;
- không phải CTA;
- không phải thêm thật nhiều kiến thức;
- không phải checkpoint cho user.

Nó là tiêu chuẩn nội bộ để đánh giá Caption.

Depth Target có thể thuộc:

- mechanism;
- condition;
- implication;
- exception;
- decision model;
- how-to-check.

Không ép mọi bài phải có causal WHY.

Với bài deadline/thủ tục/update, Depth Target có thể là:

> **WHAT CHANGES / WHO IT CHANGES FOR / HOW TO CHECK / WHAT TO DO NEXT**

Depth Target phải xuất phát từ Research Core hoặc dữ kiện đã verify.

> **Không được tạo chiều sâu bằng suy đoán mục đích chính sách, nguyên nhân hoặc logic không có bằng chứng.**

---

# 3. Title và Slide 1 là hai tài sản khác nhau

> **Title phục vụ nhận diện và search. Slide 1 phục vụ dừng và kéo vuốt.**

## Title ưu tiên

- định danh rõ chủ đề;
- chứa ngôn ngữ người dùng có thể tìm;
- giúp TikTok và người đọc hiểu bài đang nói gì;
- không mạnh hơn bằng chứng.

## Slide 1 ưu tiên

- làm đúng người dừng lại bằng **lý do quan tâm thật**;
- lý do đó có thể là **câu hỏi thực tế cần giải đáp, thông tin/việc cần làm hữu ích, hoặc mâu thuẫn/rủi ro thật**;
- cho lý do rõ ràng để vuốt tiếp;
- tự đứng được như cover.

Không ép bài hướng dẫn/cập nhật quy định thành cảnh báo hoặc nghịch lý chỉ để tạo attention; nếu có tension tự nhiên mạnh, vẫn khai thác.

Không ép một câu làm cả hai nhiệm vụ nếu điều đó làm Title hoặc Hook yếu đi.

Khi kiểm kỹ thuật trước bàn giao, AI phải tự kiểm Title/Description còn nằm trong giới hạn hiện hành của TikTok. Đây là QA nội bộ, không phải checkpoint bắt user duyệt.

---

# 4. Search-first, nhưng không SEO spam

Trước khi chốt Title/Caption, AI phải trả lời:

> **Nếu người dùng muốn tìm câu trả lời cho bài này, họ có thể gõ gì?**

Chọn:

- 1 cụm từ khóa chính;
- tối đa 1–2 biến thể tự nhiên khi hữu ích.

Ưu tiên đưa keyword hoặc ý nghĩa tương đương vào Title/Caption nếu câu vẫn tự nhiên.

Không:

- lặp keyword máy móc;
- hy sinh hook để nhét keyword;
- viết như bài SEO website.

Nguyên tắc:

> **Search-first không có nghĩa SEO spam.**

Keyword là việc nội bộ của AI. Không bắt user duyệt thành checkpoint riêng.

---

# 5. Carousel = chuỗi nhận thức, không phải caption bị chẻ nhỏ

> **Mỗi slide = một bước nhận thức.**

Không chia một caption dài thành nhiều ảnh một cách máy móc.

Một chuỗi có thể đi theo:

> **Dừng → hiểu điều đã chắc → gỡ hiểu sai → hiểu điều chưa chắc → biết nên làm gì**

Đây là ví dụ logic, không phải template cố định.

## Số slide

Không khóa số slide.

Khoảng **4–7 slide** là vùng thử nghiệm mặc định cho nội dung chuyên môn cần nhiều bước, nhưng số slide thực tế phải do số bước nhận thức quyết định.

Rule cắt:

> **Nếu bỏ một slide mà người đọc vẫn đi từ hook đến kết luận không mất một bước hiểu quan trọng, slide đó có thể là slide thừa.**

## Vai trò theo nhịp

- **Slide 1 — Dừng:** nêu lý do cụ thể để đúng người muốn vuốt tiếp; không bắt buộc phải có tension.
- **Slide giữa — Hiểu:** trả món nợ hook, giải thích, chặn hiểu sai, nêu điều kiện/giới hạn.
- **Slide cuối — Làm:** checklist, việc cần kiểm, quyết định tiếp theo hoặc CTA.

Không bắt mọi slide đều phải “giật”.

> **Slide 1 kéo. Slide giữa giải. Slide cuối giúp hành động.**

---

# 6. Chữ trên slide

> **Slide không phải caption thu nhỏ.**

Trên slide chỉ giữ những thứ đang gánh:

- mâu thuẫn;
- con số;
- điều kiện;
- ý cần nhớ;
- cảnh báo;
- hành động.

Phần giải thích dài, ngoại lệ hoặc ngữ cảnh bổ sung để Caption xử lý.

> **Đơn giản không phải cắt nhiều. Đơn giản là chỉ giữ những thứ đang làm việc.**

Và áp dụng Hook Psychology chung:

> **Giữ chi tiết tạo sức nặng cho câu hỏi, thông tin hoặc việc cần làm. Nếu hook dựa trên mâu thuẫn thật, giữ những từ đang gánh mâu thuẫn đó. Cắt phần chỉ làm đầy đủ mà không giúp người xem hiểu hoặc muốn đọc tiếp.**

Không cắt chi tiết quan trọng chỉ để “ngắn kiểu TikTok”; cũng không thêm lời cảnh báo nếu một câu hỏi/việc thực tế đã đủ lực.

---

# 7. Caption TikTok — viết cho một người thật trong một tình huống thật

Caption không bắt đầu từ “chủ đề”; caption bắt đầu từ **người đang ở trong tình huống đó**.

Tránh mở kiểu:

- “Theo quy định mới…”;
- “Trong bối cảnh hiện nay…”;
- “Như chúng ta đã biết…”;

nếu có thể mở bằng tình huống thật như:

- “Nếu bạn đã nộp thuế từ đầu năm…”;
- “Nếu kỳ khai tiếp theo đang tới…”;
- “Nếu doanh thu của bạn đang gần ngưỡng…”.

Nguyên tắc:

> **Đúng và dễ hiểu chưa đủ. Nội dung Diệu Tâm cần có cảm giác đang nói với một người thật trong một tình huống thật.**

## 7.1. Retention mặc định

> **Hook mở món nợ nào, Caption trả món nợ đó sớm.**

Nếu câu hỏi hoặc việc người đọc cần làm đã rõ, **đi thẳng vào câu trả lời/giá trị chính**; không buộc phải thêm một lớp dẫn tình huống trước. Chỉ giữ phần dẫn giúp hiểu đúng.

Thứ tự tham khảo khi phù hợp:

1. chạm đúng tình huống;
2. trả câu hỏi chính;
3. nói điều đã chắc;
4. gỡ hiểu sai quan trọng;
5. nói điều chưa thể kết luận nếu có;
6. cho người đọc một việc có thể kiểm hoặc làm;
7. CTA.

Không bắt buộc đủ 7 bước nếu bài đơn giản.

## 7.2. Specificity

> **Nếu người đọc có thể hỏi “cụ thể là gì?”, hãy nói cụ thể ngay khi có thể.**

Cảnh giác với các từ mơ hồ như:

- liên quan;
- trường hợp này;
- xử lý;
- vấn đề trên;
- đang ở đâu;

nếu có thể nói chính xác hơn bằng:

- loại thuế;
- khoản tiền;
- kỳ tính thuế;
- deadline;
- hồ sơ;
- điều kiện;
- hành động.

## 7.3. Cảm xúc

Không bơm cảm xúc bằng:

- “cực kỳ quan trọng”;
- “siêu nóng”;
- “sốc”;
- “khẩn cấp”;

nếu chính tình huống thật đã đủ lực.

Cảm xúc nên đến từ:

> **tiền thật + deadline thật + hồ sơ thật + quyền lợi thật + câu hỏi thật.**

## 7.4. Điều đã chắc / chưa chắc

Caption chuyên môn phải chủ động tách:

- **Điều đã chắc**
- **Điều chưa nên nói chắc**

Không khẳng định mạnh rồi mới chôn disclaimer ở cuối.

Câu chữ không được mạnh hơn bằng chứng.

## 7.5. Dangerous misunderstanding

Mỗi bài nên tự hỏi:

> **Người đọc dễ hiểu sai nhất ở đâu, và nếu hiểu sai thì có hậu quả gì?**

Nếu hiểu sai có hậu quả thực tế, phải chặn nó sớm bằng câu cụ thể.

Nếu dangerous misunderstanding là trọng tâm bài, chỉ nói:

> **“đừng hiểu như vậy”**

là chưa đủ.

Khi evidence cho phép, phải giúp người đọc hiểu:

1. vì sao cách hiểu đó có vẻ hợp lý;
2. nó đang bỏ sót biến nào;
3. logic đúng thay thế là gì.

Không invent nguyên nhân ngoài nguồn chỉ để bài nghe sâu.

## 7.6. Actionability

Caption phải cố trả lời:

> **Đọc xong thì tôi làm gì?**

Có thể là:

- kiểm một con số;
- chuẩn bị hồ sơ;
- lưu deadline;
- đối chiếu điều kiện;
- chờ đúng văn bản;
- theo dõi cập nhật.

### Mental model

Giá trị cao hơn checklist là giúp người đọc biết **thứ tự suy nghĩ**.

Ví dụ cấu trúc chung:

> **xác định trường hợp → xác định biến quyết định → xác định kỳ/mẫu/quyền/nghĩa vụ → mới thao tác**

Đây chỉ là dạng mental model, không phải template bắt buộc.

Nếu bài có thể cho người đọc cách tự kiểm mà không làm quá bằng chứng, ưu tiên làm điều đó.

## 7.7. Mỗi đoạn phải có nhiệm vụ

Nếu một đoạn không:

- trả lời;
- giải thích;
- cảnh báo;
- chuyển ý;
- hoặc giúp hành động;

thì cân nhắc bỏ.

Không khóa độ dài Caption. Có bài ngắn, có bài cần dài hơn để giữ evidence boundary. Không cắt chỉ vì “TikTok phải ngắn”.

## 7.8. Opening block phải tự đứng được

Caption được phép dài khi giá trị cần thiết đòi hỏi, nhưng opening block phải ngay lập tức cho đúng người lý do để đọc.

Opening nên làm ít nhất một việc:

- đặt đúng tình huống;
- trả câu hỏi chính;
- mở tension thật nếu có;
- phá assumption có căn cứ.

**Câu hỏi hoặc việc cần làm thực tế đã đủ hấp dẫn thì mở thẳng bằng nó**, không thêm cảnh báo/trấn an chỉ để tạo cảm giác có lực.

Không mở bằng:

- “Theo quy định…”;
- “Hiện nay…”;
- “Trong bài viết này…”;

nếu có cách đi thẳng vào vấn đề tốt hơn.

> **Không cắt Caption chỉ vì định kiến “TikTok phải ngắn”. Độ dài do giá trị bổ sung quyết định.**

---

# 8. CAROUSEL VÀ CAPTION — KNOWLEDGE GAIN DELTA

> **Carousel giúp người xem hiểu bài. Caption phải giúp người quan tâm hiểu sâu hơn.**

Carousel chịu trách nhiệm:

- dẫn người xem qua các bước nhận thức;
- làm rõ takeaway chính;
- giữ nhịp vuốt.

Caption chịu trách nhiệm mở thêm lớp:

- vì sao nếu WHY là lớp cần thiết;
- điều kiện;
- ngoại lệ;
- cơ chế;
- implication;
- cách tự xác định trường hợp;
- ranh giới kết luận;
- hành động tiếp theo.

Trước khi Caption được khóa, phải trả lời:

> **Nếu người xem đã đọc hết carousel, họ học thêm được điều gì khi đọc Caption?**

Nếu câu trả lời chỉ là:

> **“chi tiết hơn một chút”**

→ chưa đạt.

Không bê nguyên Caption Facebook sang TikTok.

Không nối các slide thành đoạn văn rồi gọi đó là Caption.

> **Đừng chỉ cho người đọc kết luận. Hãy cho họ cách hiểu để tự đi đến kết luận đúng.**

## 8.1. Depth không đồng nghĩa với dài

> **Depth = thêm đúng lớp giải thích giúp người đọc hiểu bản chất.**

Không phải:

> **Depth = thêm nhiều kiến thức.**

Không tự thêm:

- lịch sử;
- căn cứ dư thừa;
- ngoại lệ không liên quan;
- lý thuyết ngoài nhu cầu người đọc.

Caption sâu nhưng gọn tốt hơn Caption dài nhưng loãng.

Mỗi đoạn phải thêm ít nhất một giá trị mới:

- mechanism;
- condition;
- implication;
- misunderstanding;
- mental model;
- action.

Đoạn chỉ đổi cách nói → bỏ.

---

# 9. Emoji

Không bắt buộc emoji.

Trong Caption, dùng emoji khi giúp:

- dẫn mắt;
- phân đoạn;
- cảnh báo;
- nhấn CTA.

Không có quota emoji.

Không dùng chuỗi emoji để bài “trông giống TikTok”.

Trên ảnh carousel mặc định **không cần emoji** nếu chữ đã đủ lực.

---

# 10. CTA

Một bài chỉ ưu tiên **một hành động chính**.

CTA phải đi ra từ nội dung, không gắn quảng cáo máy móc ở cuối.

Nếu nội dung còn chờ hướng dẫn chính thức:

> **“Theo dõi để cập nhật” thường tự nhiên hơn “liên hệ dịch vụ ngay”.**

Các CTA có thể dùng khi thật sự hợp:

- theo dõi;
- lưu bài;
- bình luận tình huống;
- gửi cho người liên quan;
- nhắn tin khi có nhu cầu tư vấn thật.

Không nhét nhiều CTA cạnh tranh nhau.

---

# 11. Hashtag

Hashtag là tín hiệu phân loại/khám phá, không phải phép tăng view.

Chỉ nghiên cứu/chốt hashtag **sau khi nội dung đã ổn**.

Mặc định thử nghiệm:

> **3–5 hashtag liên quan trực tiếp.**

Không mặc định:

- #fyp
- #viral
- #xuhuong

nếu không có lý do thật.

Khi bàn giao, hashtag phải nằm **ngay cuối Caption**, không tạo block hashtag riêng.

---

# 12. Output chữ cho user

Chỉ Caption sau **T3B + user OK** mới là Final Caption để copy/paste.

Caption ở T3A là Draft được user duyệt hướng, không phải output cuối.

Output copy cuối chỉ cần:

## Block 1 — Tiêu đề TikTok

Title hoàn chỉnh.

## Block 2 — Caption TikTok hoàn chỉnh + hashtag

Caption đã gồm CTA và hashtag ở cuối.

**Caption Final bắt buộc có chữ ký thương hiệu đúng hai dòng** theo `docs/brand/ktdt-social-writing-dna.md`, đặt sau nội dung/CTA, trước căn cứ/ngày cập nhật (nếu có) và hashtag. Không chèn chữ ký vào Title, cover, slide hay ảnh carousel.

Không bắt user copy riêng:

- keyword;
- CTA;
- hashtag;
- SEO note;
- checklist QA.

Những phần đó là việc nội bộ của AI.

---

# 13. Visual mặc định

TikTok carousel của Diệu Tâm mặc định:

- dọc **9:16**;
- slide 1 mặc định là cover;
- **không logo**;
- **không tên thương hiệu trên ảnh**;
- không hỏi user lại về logo.

Nếu user muốn logo, user chủ động upload logo và yêu cầu sửa sau.

9:16 là default thiết kế của workflow Diệu Tâm, không phải tuyên bố rằng organic Photo Post chỉ chấp nhận 9:16.

## Không khóa template

Không khóa:

- màu đỏ/vàng;
- một font;
- background;
- calculator / coin / giấy thuế;
- một bố cục;
- một phong cách poster.

Mỗi chủ đề được phép có concept mới.

Điều phải giữ:

> **Cùng một carousel phải cùng một hệ thị giác.**

Có thể thống nhất:

- typography;
- bảng màu;
- độ tương phản;
- phong cách hình.

Nhưng:

> **layout từng slide được thay đổi theo nhiệm vụ của slide.**

---

# 14. Safe-zone QA

Khi tạo ảnh, AI tự kiểm:

- headline không sát mép;
- CTA không quá thấp;
- nội dung quan trọng không dựa vào vùng dễ bị UI che;
- slide 1 vẫn đọc tốt khi làm cover;
- đủ khoảng thở;
- không dùng hết canvas chỉ vì còn chỗ.

> **Khoảng trống cũng là một phần của thiết kế.**

---

# 15. Workflow TikTok

## T0 — Inheritance + Delta Research + Depth Target — nội bộ, không xin OK

Nếu có Research Core:

- inherit các decision lock;
- inherit source package;
- kiểm freshness nếu dữ kiện có thể thay đổi;
- chạy TikTok Platform Delta Research;
- không full research lại.

Nếu standalone:

- dùng Research Core vừa hoàn tất;
- chạy Delta Research như bình thường.

Cuối T0 phải có **Depth Target** nội bộ.

## T1 — Title + Carousel Structure — xin OK

Đưa:

- Title khuyến nghị;
- số slide;
- nhiệm vụ từng slide;
- lý do ngắn cho cấu trúc.

Chưa viết Caption.

AI tự kiểm:

- các slide có dẫn đúng tới Depth Target không;
- carousel đã đủ để hiểu vấn đề cơ bản chưa;
- phần nào nên để Caption giải thích sâu hơn thay vì nhồi lên slide.

User nói **OK**:

- khóa Title;
- khóa số slide;
- khóa nhiệm vụ từng slide;
- chạy T2 ngay.

## T2 — Exact Slide Copy — xin OK

Viết chữ hoàn chỉnh Slide 1 → Slide n.

Không cố nhét toàn bộ Depth Target lên slide.

> **Slide ngắn không phải vì TikTok cần ít chữ; slide ngắn vì mỗi slide chỉ nên gánh một bước nhận thức.**

User nói **OK**:

- khóa toàn bộ chữ carousel;
- chạy T3A ngay.

## T3A — Caption Draft — xin OK hướng

Caption Draft là bản đầy đủ đầu tiên.

Không cố tình viết nông chỉ vì còn T3B.

Baseline bắt buộc:

- factual đúng;
- evidence boundary đúng;
- search language tự nhiên;
- CTA đúng hướng;
- hashtag phù hợp;
- không lặp carousel máy móc;
- người không chuyên hiểu được;
- actionable.

User chỉ nhận:

- **Block Tiêu đề**
- **Block Caption Draft + hashtag**

User nói **OK**:

> **HƯỚNG CAPTION ĐƯỢC DUYỆT — CHƯA KHÓA EXACT WORDING**

Sau đó chuyển sang T3B.

## T3B — Depth & Voice Review + Rewrite — xin OK final

Đây là **một turn riêng với T3A**.

AI phải đổi vai:

> **writer → editor/reviewer**

Không bảo vệ Draft.

Review theo bốn lớp:

> **ĐÚNG → RÕ → SÂU → CÓ HƠI NGƯỜI**

Tầng trước đạt không có nghĩa tầng sau tự động đạt.

### 1. NEW VALUE

Caption thêm giá trị gì ngoài carousel?

Nếu người đã xem hết carousel chỉ nhận lại cùng thông tin bằng nhiều chữ hơn → FAIL.

### 2. UNDERSTANDING

Caption có thêm ít nhất một lớp phù hợp:

- mechanism;
- condition;
- implication;
- exception;
- decision model;
- how-to-check?

Không bắt mọi bài phải có causal WHY.

### 3. SELF-APPLICATION

Người đọc có biết:

- phải nhìn vào biến nào;
- kiểm theo thứ tự nào;
- hoặc áp logic vào trường hợp của mình ra sao?

### 4. HUMAN VOICE

Bỏ Title/hashtag đi, bài nghe giống:

- người có chuyên môn đang giải thích cho khách hàng;
- hay tài liệu tổng hợp / công văn / AI summary?

Nếu nghiêng về loại hai → FAIL.

### 5. ECONOMY + EVIDENCE

Mỗi đoạn có nhiệm vụ riêng không?

Mọi insight có được Research Core hỗ trợ không?

**Kiểm giá trị thực tế trước khi làm sâu câu chữ:** Với bài hướng dẫn/tự kiểm, đã đưa cách làm, điều kiện và bước tiếp theo **được xác minh** lên đủ sớm chưa? Nếu carousel đã hướng dẫn thao tác, Caption cần bổ sung cách hiểu/đối chiếu/giới hạn hữu ích thay vì kể lại các bước.

Cắt các câu chỉ **lặp lại lý do phải quan tâm, cảnh báo hoặc trấn an** mà không thêm thông tin, điều kiện, giới hạn hay hành động mới. **Giữ** lưu ý thực sự cần để ngăn hiểu sai hoặc bảo toàn căn cứ pháp lý; không cắt chỉ để làm Caption ngắn.

> **Không invent insight để làm bài có vẻ sâu.**

### Opening Block Test

Opening block phải tự đứng được và làm ít nhất một việc:

- đặt đúng tình huống;
- trả tension;
- phá assumption;
- đưa câu trả lời chính.

### Depth Guardrail

> **Depth = thêm đúng lớp giải thích giúp người đọc hiểu bản chất; không phải thêm nhiều kiến thức.**

Nếu fail một gate quan trọng:

> **rewrite trước khi trình user.**

Chỉ trình khi đạt:

> **CAPTION DEPTH PASS**

### Output user thấy

Một dòng ngắn:

> **Bản sau Depth & Voice Review**

Sau đó:

- **Block Tiêu đề**
- **Block Caption Final + hashtag**

Không dump checklist review.

User nói **OK**:

- khóa exact Caption;
- khóa exact CTA;
- khóa hashtag;
- chạy T4.

## T4 — Visual Concept — xin OK

Trình bày ngắn:

- tỷ lệ;
- số ảnh;
- hướng visual;
- nguyên tắc typography;
- nội dung từng ảnh đã khóa.

Mặc định:

> **9:16 + không logo + không tên thương hiệu.**

User nói **OK**:

> **tạo toàn bộ carousel ngay, không hỏi lại.**

## T5 — Generate + QA + Handoff — không xin phép giữa chừng

AI tự:

- tạo toàn bộ ảnh;
- QA từng ảnh;
- QA cả chuỗi;
- kiểm safe zone;
- sửa lỗi khách quan rõ ràng nếu có;
- bàn giao theo đúng thứ tự đăng.

Không tạo slide 1 rồi xin OK để tạo slide 2.

---

# 16. QA từng slide

Kiểm:

1. chữ đúng với decision lock;
2. số/con số đúng;
3. dấu tiếng Việt đúng;
4. factual claim không mạnh hơn bằng chứng;
5. dễ đọc trên điện thoại;
6. contrast đủ;
7. safe zone ổn;
8. không logo;
9. không tên thương hiệu;
10. không có artifact rõ ràng cạnh tranh với nội dung.

Nếu phát hiện lỗi khách quan rõ như sai chữ, sai dấu, factual mismatch hoặc logo ngoài ý muốn → sửa trước khi bàn giao.

---

# 17. QA cả carousel

Trước khi coi bộ ảnh hoàn chỉnh, hỏi:

1. Slide 1 có tạo lý do để vuốt Slide 2 không?
2. Slide 2 có trả món nợ Slide 1 chưa?
3. Mỗi slide có thêm một bước hiểu mới không?
4. Có slide nào chỉ nhắc lại slide trước không?
5. Nếu bỏ một slide, bài có mất bước nhận thức nào không?
6. Slide cuối có cho người đọc biết nên làm gì không?
7. Cả bộ có cùng một hệ thị giác không?
8. Chữ có đọc tốt trên điện thoại không?
9. Có lỗi dấu tiếng Việt không?
10. Có câu nào mạnh hơn bằng chứng không?

---

# 18. AIGC reminder

Không tạo checkpoint riêng.

Sau khi bàn giao bộ ảnh AI-generated, chỉ thêm một dòng:

> **Lưu ý khi đăng: ảnh được tạo bằng AI, hãy kiểm tra yêu cầu gắn nhãn nội dung AI của TikTok tại thời điểm đăng.**

---

# 19. Nghiên cứu TikTok khi truy cập bị hạn chế

Ưu tiên:

1. TikTok trực tiếp;
2. TikTok Creator Search Insights;
3. TikTok Creative Center / Keyword Insights / hashtag trend;
4. tài liệu chính thức TikTok;
5. dữ liệu Diệu Tâm nếu có.

Nếu không đủ dữ liệu TikTok trực tiếp, có thể dùng:

- YouTube Shorts / Search;
- Facebook;
- nguồn social marketing đáng tin;

để bổ trợ giả thuyết đóng gói.

Nhưng phải ghi:

> **Suy luận chéo nền tảng — không phải bằng chứng hiệu quả trên TikTok.**

Không biến dữ liệu YouTube/Facebook thành dữ liệu TikTok.

Không dừng workflow chỉ vì không đọc được TikTok trực tiếp.

---

# 20. Câu căn chỉnh cho AI

> **Đừng viết TikTok như một caption Facebook ngắn hơn. Carousel giúp người xem đi qua mạch chính; Caption phải tạo Knowledge Gain Delta cho người thật sự quan tâm. Viết Draft trước, rồi ở turn kế tiếp đổi vai thành editor: tìm chỗ đúng nhưng nông, chỗ chỉ lặp carousel, chỗ thiếu mechanism/condition/mental model hoặc còn giống tài liệu tổng hợp. Rewrite trước khi gọi Caption là Final. Sâu không có nghĩa nhiều chữ; sâu là giúp người đọc hiểu đúng bản chất bằng những gì Research Core thực sự hỗ trợ.**

> **Không biến checklist nội bộ của AI thành công việc của user. T3A và T3B được tách thành hai turn vì writer và reviewer có nhiệm vụ khác nhau; user chỉ cần OK hướng Draft rồi OK Final Caption.**
