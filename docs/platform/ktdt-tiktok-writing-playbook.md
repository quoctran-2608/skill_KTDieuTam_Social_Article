# TIKTOK PHOTO CAROUSEL PLAYBOOK — KẾ TOÁN DIỆU TÂM

**Phiên bản:** 0.2  
**Ngày cập nhật:** 08/10/2026  
**Trạng thái:** Thử nghiệm — đã được test qua một case Facebook → TikTok thật  
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

---

# 3. Title và Slide 1 là hai tài sản khác nhau

> **Title phục vụ nhận diện và search. Slide 1 phục vụ dừng và kéo vuốt.**

## Title ưu tiên

- định danh rõ chủ đề;
- chứa ngôn ngữ người dùng có thể tìm;
- giúp TikTok và người đọc hiểu bài đang nói gì;
- không mạnh hơn bằng chứng.

## Slide 1 ưu tiên

- làm đúng người dừng lại;
- mở mâu thuẫn thật;
- cho lý do để vuốt tiếp;
- tự đứng được như cover.

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

- **Slide 1 — Dừng:** mở tension, khiến muốn vuốt.
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

Và giữ nguyên lesson chung:

> **Giữ những từ đang gánh mâu thuẫn. Thêm chi tiết nếu nó làm câu rõ hơn mà không làm nặng câu. Cắt phần chỉ làm câu đầy đủ hơn nhưng không làm người đọc hiểu hoặc quan tâm hơn.**

Không cắt một từ chỉ vì muốn “ngắn kiểu TikTok” nếu từ đó đang tạo lực cho mâu thuẫn.

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

Thứ tự mặc định khi phù hợp:

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

## 7.7. Mỗi đoạn phải có nhiệm vụ

Nếu một đoạn không:

- trả lời;
- giải thích;
- cảnh báo;
- chuyển ý;
- hoặc giúp hành động;

thì cân nhắc bỏ.

Không khóa độ dài Caption. Có bài ngắn, có bài cần dài hơn để giữ evidence boundary. Không cắt chỉ vì “TikTok phải ngắn”.

---

# 8. Carousel và Caption phải bổ sung nhau

> **Carousel kể theo bước. Caption giải thích thêm.**

Caption có thể lặp conflict chính ở đầu để giữ mạch, nhưng không đọc lại toàn bộ carousel.

Caption nên bổ sung những gì slide không đủ chỗ nói:

- điều kiện;
- ngoại lệ;
- ranh giới bằng chứng;
- giải thích;
- việc nên làm.

Không bê nguyên caption Facebook sang TikTok. Cũng không cắt caption Facebook một cách cơ học rồi gọi đó là TikTok.

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

Khi Caption đã được duyệt, output copy cuối chỉ cần:

## Block 1 — Tiêu đề TikTok

Title hoàn chỉnh.

## Block 2 — Caption TikTok hoàn chỉnh + hashtag

Caption đã gồm CTA và hashtag ở cuối.

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

## T0 — Inheritance + Platform Delta Research — nội bộ, không xin OK

Nếu có Research Core:

- inherit các decision lock;
- inherit source package;
- kiểm freshness nếu dữ kiện có thể thay đổi;
- chạy TikTok Platform Delta Research;
- không full research lại.

Nếu standalone:

- dùng Research Core vừa hoàn tất;
- chạy Delta Research như bình thường.

## T1 — Title + Carousel Structure — xin OK

Đưa:

- Title khuyến nghị;
- số slide;
- nhiệm vụ từng slide;
- lý do ngắn cho cấu trúc.

Chưa viết Caption.

User nói **OK**:

- khóa Title;
- khóa số slide;
- khóa nhiệm vụ từng slide;
- chạy T2 ngay.

## T2 — Exact Slide Copy — xin OK

Viết chữ hoàn chỉnh Slide 1 → Slide n.

User nói **OK**:

- khóa toàn bộ chữ carousel;
- chạy T3 ngay.

## T3 — Caption hoàn chỉnh — xin OK

AI tự xử lý nội bộ:

- keyword;
- CTA;
- hashtag research;
- spacing;
- emoji;
- factual check;
- evidence boundary.

User chỉ nhận:

- **Block Tiêu đề**
- **Block Caption + hashtag**

User nói **OK**:

- khóa Caption/CTA;
- tự QA text;
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

> **Đừng viết TikTok như một caption Facebook ngắn hơn. Hãy xây một chuỗi vuốt có lý do: Title giúp người ta tìm thấy, Slide 1 khiến họ dừng, mỗi slide sau giúp họ hiểu thêm một bước, Caption bổ sung giá trị còn thiếu và Slide cuối giúp họ biết nên làm gì.**

> **Không biến checklist nội bộ của AI thành công việc của user. AI tự kiểm những gì có thể tự kiểm; chỉ dừng xin OK ở những quyết định sáng tạo hoặc chiến lược thật sự cần người duyệt.**
