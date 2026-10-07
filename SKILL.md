# KẾ TOÁN DIỆU TÂM — SOCIAL CONTENT SKILL

**Phiên bản:** 0.5  
**Ngày:** 07/10/2026  
**Vai trò:** File điều phối trung tâm / runtime orchestrator  
**Trạng thái:** Đang phát triển — đã kiểm chứng thực tế đến Facebook dạng ảnh: nghiên cứu → chọn cách đánh → hook → thân bài → đóng gói → tạo ảnh → QA cơ bản.

---

# 0. CÁCH DÙNG SKILL NÀY

Khi người dùng đưa URL của `SKILL.md` cùng một yêu cầu làm nội dung, AI phải:

1. **Đọc `SKILL.md` trước.**
2. Không nhảy thẳng sang viết bài hoàn chỉnh.
3. Xác định bước hiện tại và chỉ mở những file con được chỉ định cho bước đó.
4. Thực hiện **một checkpoint tại một thời điểm**.
5. Trình bày kết quả / khuyến nghị của checkpoint hiện tại.
6. **Dừng và chờ người dùng duyệt** bằng các tín hiệu như `OK`, `duyệt`, `chốt`, `tiếp tục` trước khi sang checkpoint kế tiếp.
7. Khi một quyết định đã được duyệt, ghi nhận nó là **decision lock** và không tự đổi ở bước sau.

> **Mặc định là chế độ tương tác từng bước. Chỉ chạy liền nhiều bước nếu người dùng chủ động yêu cầu không cần duyệt từng bước.**

Nếu một file bắt buộc không mở được, phải nói rõ file nào không truy cập được và **dừng bước đó**. Không được tự bịa nội dung của file.

---

# 1. REPO VÀ DANH BẠ FILE CHÍNH THỨC

**Repo:** `quoctran-2608/skill_KTDieuTam_Social_Article`  
**Branch chuẩn:** `main`  
**Repo URL:** https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article

## 1.1. File điều phối

- Path: `SKILL.md`
- URL: https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/SKILL.md
- Vai trò: xác định thứ tự chạy, checkpoint, decision lock và file con phải đọc.

## 1.2. Nghiên cứu

### Quy trình nghiên cứu
- Path: `docs/research/ktdt-research-workflow.md`
- URL: https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/research/ktdt-research-workflow.md
- Dùng ở: toàn bộ pha nghiên cứu.

### Kiểm chứng nguồn
- Path: `docs/research/ktdt-source-verification.md`
- URL: https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/research/ktdt-source-verification.md
- Dùng ở: nghiên cứu sự thật, đặc biệt luật / thuế / kế toán / chính sách / số liệu.

### Nghiên cứu đối thủ và nội dung cạnh tranh theo nền tảng
- Path: `docs/research/ktdt-platform-competitor-research.md`
- URL: https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/research/ktdt-platform-competitor-research.md
- Dùng ở: nghiên cứu nội dung cạnh tranh trên nền tảng đích.

### Chuẩn đầu ra nghiên cứu
- Path: `docs/research/ktdt-research-output.md`
- URL: https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/research/ktdt-research-output.md
- Dùng ở: đóng gói hồ sơ nghiên cứu và quyết định có đủ dữ kiện để sáng tạo hay chưa.

## 1.3. Viết nội dung

### DNA thương hiệu
- Path: `docs/brand/ktdt-social-writing-dna.md`
- URL: https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/brand/ktdt-social-writing-dna.md
- Dùng ở: mọi bước viết / đánh giá nội dung Diệu Tâm.

### Hook
- Path: `docs/content/ktdt-hook-language-psychology.md`
- URL: https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/content/ktdt-hook-language-psychology.md
- Dùng ở: tạo và đánh giá câu mở đầu. **Phải dùng cùng DNA.**

### Thân bài & retention
- Path: `docs/content/ktdt-body-writing-retention.md`
- URL: https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/content/ktdt-body-writing-retention.md
- Dùng ở: thiết kế đường giữ người đọc, viết thân bài, xưng hô, độ rõ, CTA.

## 1.4. Nền tảng

### Facebook dạng ảnh
- Path: `docs/platform/ktdt-facebook-post-playbook.md`
- URL: https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/platform/ktdt-facebook-post-playbook.md
- Dùng ở: chọn 1 ảnh / 3 ảnh, đóng gói caption, spacing, emoji, hashtag, tạo ảnh và QA ảnh.

> **Luật tải file:** Không cần đọc toàn bộ repo ở mỗi lần chạy. Chỉ mở file đúng với checkpoint hiện tại theo bảng điều phối bên dưới. Khi một checkpoint yêu cầu nhiều file, phải đọc đủ các file đó trước khi tạo đầu ra.

---

# 2. NGUYÊN TẮC ĐIỀU PHỐI

## 2.1. Decision lock

Khi người dùng đã duyệt một quyết định như:

- nền tảng;
- đối tượng;
- mục tiêu;
- góc chính;
- định dạng;
- hook;
- CTA;
- chữ trên ảnh;
- số ảnh;
- logo / vị trí logo nếu đã chốt;

thì quyết định đó trở thành **điểm khóa**.

AI không được tự tối ưu lại ở bước sau, trừ khi:

- phát hiện lỗi factual / bằng chứng / an toàn;
- phát hiện lỗi hiển thị bắt buộc phải sửa;
- hoặc người dùng chủ động mở lại quyết định.

## 2.2. Không đi trước checkpoint

Không tạo hook khi góc chưa được duyệt.  
Không viết caption hoàn chỉnh khi hook / retention / CTA chưa được duyệt.  
Không tạo ảnh khi chữ trên ảnh và format chưa được duyệt.

## 2.3. Chỉ hỏi điều thật sự thiếu

Nếu prompt đã cung cấp đủ thông tin cho checkpoint hiện tại, làm luôn checkpoint đó.

Chỉ hỏi lại khi thiếu dữ kiện làm thay đổi đáng kể kết quả, ví dụ:

- chưa biết chủ đề và không thể suy ra;
- chưa biết nền tảng đích trước bước nghiên cứu cạnh tranh;
- chưa có logo nhưng người dùng yêu cầu phải dùng đúng logo;
- chưa rõ mục tiêu kinh doanh khi mục tiêu quyết định cách đánh.

---

# 3. RUNTIME FLOW — CHẠY TỪNG BƯỚC

## CHECKPOINT 0 — Nhận brief

### Mục tiêu
Xác định tối thiểu:

- chủ đề hoặc yêu cầu tìm chủ đề;
- nền tảng đích;
- mục tiêu nội dung / kinh doanh nếu người dùng đã nêu;
- tài sản đầu vào có sẵn như link, file, logo.

Nếu người dùng chưa có chủ đề, dùng **tiền bước chọn chủ đề** trong:

- `docs/research/ktdt-research-workflow.md`
- URL: https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/research/ktdt-research-workflow.md

### Đầu ra
Tóm tắt brief đang hiểu trong vài dòng. Nếu đủ để nghiên cứu, đề nghị bắt đầu CHECKPOINT 1.1.

### Gate
> **Chờ người dùng OK.**

---

## CHECKPOINT 1.1 — Nghiên cứu SỰ THẬT

### Bắt buộc đọc
- `docs/research/ktdt-research-workflow.md`
- `docs/research/ktdt-source-verification.md`

URLs:
- https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/research/ktdt-research-workflow.md
- https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/research/ktdt-source-verification.md

### Làm
- xác minh nguồn;
- tách chính thức / dự thảo / chưa chốt;
- kiểm ngày, phạm vi, con số, điều kiện;
- lập sổ nguồn;
- xác định điều không được phép khẳng định.

Với thông tin hiện hành / luật / thuế / chính sách / dữ liệu mới, phải dùng nguồn web hiện tại nếu có khả năng truy cập web.

### Đầu ra checkpoint
- sự thật trung tâm;
- điều đã chắc;
- điều chưa chắc / không được nói;
- giới hạn dữ liệu.

### Gate
> **Chỉ đi tiếp khi đạt: DỮ KIỆN CỐT LÕI ĐÃ CHẮC. Sau đó dừng và chờ OK.**

---

## CHECKPOINT 1.2 — Nghiên cứu NGƯỜI ĐỌC

### Bắt buộc đọc
- `docs/research/ktdt-research-workflow.md`
- URL: https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/research/ktdt-research-workflow.md

### Làm
Xác định:

- người đọc chính;
- tình huống thật;
- họ đang nghĩ gì;
- họ lo / hỏi / quyết định gì;
- khoảng cách nhận thức;
- điều họ cần biết.

### Gate
> **Bài này đang nói với ai, họ đang nghĩ gì và tại sao họ phải quan tâm phải được làm rõ. Dừng và chờ OK.**

---

## CHECKPOINT 1.3 — Nghiên cứu NỘI DUNG CẠNH TRANH

### Bắt buộc đọc
- `docs/research/ktdt-research-workflow.md`
- `docs/research/ktdt-platform-competitor-research.md`

URLs:
- https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/research/ktdt-research-workflow.md
- https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/research/ktdt-platform-competitor-research.md

### Làm
- nghiên cứu trên **nền tảng đích**;
- tách organic / paid nếu có;
- không dùng đối thủ để xác nhận luật;
- không gọi hiệu quả / viral nếu không đủ dữ liệu;
- không có dữ liệu thì nói `chưa đủ dữ liệu`.

### Gate
> **Chốt được điều đã bão hòa, pattern quan sát được và giới hạn dữ liệu. Dừng và chờ OK.**

---

## CHECKPOINT 1.4 — CƠ HỘI NỘI DUNG & HỒ SƠ NGHIÊN CỨU

### Bắt buộc đọc
- `docs/research/ktdt-research-workflow.md`
- `docs/research/ktdt-research-output.md`

URLs:
- https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/research/ktdt-research-workflow.md
- https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/research/ktdt-research-output.md

### Làm
- xác định khoảng trống quan sát được;
- cơ hội của Diệu Tâm;
- lời hứa nội dung khả thi;
- đóng gói hồ sơ theo chuẩn output.

### Gate
> **Phải kết thúc bằng ✅ ĐỦ DỮ KIỆN ĐỂ CHỌN CÁCH ĐÁNH hoặc ❌ CHƯA ĐỦ DỮ KIỆN. Nếu ✅, dừng và chờ OK.**

---

## CHECKPOINT 2 — Chốt MỤC TIÊU NỘI DUNG

### Dùng
- hồ sơ nghiên cứu đã duyệt;
- `docs/brand/ktdt-social-writing-dna.md` khi cần kiểm ranh giới thương hiệu.

### Làm
Đề xuất **một mục tiêu chính** và tối đa một mục tiêu phụ. Nói rõ hành vi mong muốn của người xem.

### Gate
> **Người dùng duyệt mục tiêu → khóa mục tiêu → dừng chờ OK cho góc.**

---

## CHECKPOINT 3 — Chốt GÓC CHÍNH

### Dùng
- hồ sơ nghiên cứu;
- mục tiêu đã khóa.

### Làm
Đề xuất góc chính mạnh nhất, giải thích ngắn vì sao nó phù hợp với người đọc + khoảng trống + mục tiêu.

Không viết hook ở bước này.

### Gate
> **Người dùng duyệt góc → khóa góc → dừng chờ OK.**

---

## CHECKPOINT 4 — Chốt ĐỊNH DẠNG

### Nếu Facebook dạng ảnh, bắt buộc đọc
- `docs/platform/ktdt-facebook-post-playbook.md`
- URL: https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/platform/ktdt-facebook-post-playbook.md

### Làm với Facebook
Mặc định đưa 2 lựa chọn:

- **1 ảnh**;
- **3 ảnh**.

AI khuyến nghị một phương án dựa trên số bước nhận thức người xem cần đi qua. Người dùng chốt.

### Gate
> **Khóa format / số ảnh → dừng chờ OK.**

---

## CHECKPOINT 5 — Tạo và chốt HOOK

### Bắt buộc đọc ĐỒNG THỜI
- `docs/brand/ktdt-social-writing-dna.md`
- `docs/content/ktdt-hook-language-psychology.md`

URLs:
- https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/brand/ktdt-social-writing-dna.md
- https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/content/ktdt-hook-language-psychology.md

### Làm
- xác định người đọc đang nghĩ gì;
- sự thật nào làm họ nhìn lại;
- chi tiết nào gánh mâu thuẫn;
- tạo 3–5 phương án đáng dùng;
- cắt chữ thừa nhưng giữ từ gánh lực;
- đề xuất một phương án tốt nhất.

Không chèn ví dụ từ tài liệu như đáp án mẫu.

### Gate
> **Người dùng chọn / duyệt hook → khóa nguyên văn hook → dừng chờ OK.**

---

## CHECKPOINT 6 — Chốt ĐƯỜNG GIỮ NGƯỜI ĐỌC

### Bắt buộc đọc
- `docs/brand/ktdt-social-writing-dna.md`
- `docs/content/ktdt-body-writing-retention.md`

URLs:
- https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/brand/ktdt-social-writing-dna.md
- https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/content/ktdt-body-writing-retention.md

### Làm
Chỉ dựng **xương sống**, chưa viết caption hoàn chỉnh:

- hook mở món nợ gì;
- đoạn đầu trả món nợ đó thế nào;
- các ý tiếp theo theo thứ tự tò mò của người đọc;
- đâu là điều đã chắc / điều cần giải thích / việc cần làm.

### Gate
> **Người dùng duyệt retention path → khóa cấu trúc → dừng chờ OK.**

---

## CHECKPOINT 7 — Chốt CTA

### Bắt buộc dùng
- `docs/brand/ktdt-social-writing-dna.md`
- `docs/content/ktdt-body-writing-retention.md`

### Làm
Đề xuất CTA chính phù hợp mục tiêu đã khóa. CTA phải đi ra tự nhiên từ giá trị bài, không mặc định bán dịch vụ.

### Gate
> **Người dùng duyệt CTA → khóa CTA → dừng chờ OK.**

---

## CHECKPOINT 8 — Viết BẢN NỘI DUNG HOÀN CHỈNH

### Bắt buộc đọc
- `docs/brand/ktdt-social-writing-dna.md`
- `docs/content/ktdt-body-writing-retention.md`
- nếu Facebook: `docs/platform/ktdt-facebook-post-playbook.md`

URLs:
- https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/brand/ktdt-social-writing-dna.md
- https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/content/ktdt-body-writing-retention.md
- https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/platform/ktdt-facebook-post-playbook.md

### Luật
- giữ nguyên các decision lock;
- hook caption không được tự đổi;
- hook mở món nợ nào, thân bài trả món nợ đó sớm;
- nói với một người thật trong một tình huống thật;
- không để người đọc phải đoán `cụ thể là gì?`;
- xưng hô có chức năng;
- CTA đúng bản đã khóa.

### Gate
> **Đưa bản viết để người dùng duyệt. Dừng chờ OK.**

---

## CHECKPOINT 9 — ĐÓNG GÓI FACEBOOK

### Bắt buộc đọc
- `docs/platform/ktdt-facebook-post-playbook.md`
- URL: https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/platform/ktdt-facebook-post-playbook.md

### Làm
Tách rõ:

1. chữ trên ảnh;
2. caption;
3. hashtag.

Với Facebook:

- chỉnh khoảng trắng để tránh tường chữ;
- emoji chủ yếu ở caption;
- hook caption mặc định có ít nhất 1 emoji phù hợp nếu chủ đề cho phép;
- không mặc định emoji trên ảnh;
- nghiên cứu **5 hashtag** phù hợp sau khi nội dung đã ổn;
- hashtag là dữ liệu động: nếu có web, research hiện tại; không tự bịa độ phổ biến.

### Gate
> **Người dùng duyệt text đóng gói → khóa chữ trên ảnh / caption / hashtag → dừng chờ OK.**

---

## CHECKPOINT 10 — QA NỘI DUNG TRƯỚC ẢNH

### Dùng
- `docs/brand/ktdt-social-writing-dna.md`
- `docs/content/ktdt-body-writing-retention.md`
- `docs/platform/ktdt-facebook-post-playbook.md` nếu Facebook.

### Kiểm
- factual / số liệu / phạm vi / trạng thái chính thức;
- lời hứa hook có được trả;
- câu mơ hồ;
- giọng có hơi người;
- spacing / emoji / CTA / hashtag;
- chữ trên ảnh khớp caption.

Với chủ đề thời sự / luật / chính sách đang thay đổi, re-check dữ kiện hiện tại nếu cần.

### Gate
> **Nếu đạt, báo `TEXT ĐÃ ĐỦ CHUẨN ĐỂ TẠO ẢNH` và dừng chờ OK.**

---

## CHECKPOINT 11 — ĐỀ NGHỊ & CHỐT CONCEPT ẢNH

### Bắt buộc đọc
- `docs/platform/ktdt-facebook-post-playbook.md` nếu Facebook.

### Làm
Tóm tắt ngắn:

- số ảnh;
- tỷ lệ / kích thước mục tiêu;
- chữ chính xác trên ảnh;
- phong cách;
- màu chủ đạo nếu đã có;
- logo có dùng không;
- vị trí logo;
- tài sản tham chiếu cần dùng.

Nếu thiếu logo đúng mà bắt buộc phải dùng logo, chỉ lúc này mới yêu cầu người dùng upload / cung cấp logo.

### Gate
> **Hỏi người dùng có tạo ảnh ngay không. Nếu OK → sang CHECKPOINT 12.**

---

## CHECKPOINT 12 — TẠO ẢNH & QA ẢNH

### Làm
Nếu môi trường có công cụ tạo / chỉnh ảnh, phải **dùng công cụ để tạo ảnh thật**, không chỉ mô tả prompt.

Giữ nguyên:

- chữ trên ảnh đã khóa;
- số ảnh;
- logo / vị trí logo đã khóa;
- định hướng visual đã duyệt.

### QA sau tạo
Kiểm ít nhất:

- đúng tỷ lệ phù hợp nền tảng;
- chữ dễ đọc trên điện thoại;
- hook đúng nguyên văn;
- không lỗi dấu tiếng Việt rõ ràng;
- logo sạch, đúng vị trí, không nền rác / viền lạ;
- không chi tiết thừa cạnh tranh với hook;
- bố cục có vùng thở;
- phù hợp mục tiêu organic / quảng cáo.

Nếu có lỗi khách quan rõ ràng, sửa trước khi coi là hoàn chỉnh.

Nếu môi trường không có công cụ tạo ảnh, nói rõ giới hạn và bàn giao **visual brief hoàn chỉnh**; không tuyên bố đã tạo ảnh.

### Gate
> **Người dùng duyệt ảnh → khóa visual.**

---

## CHECKPOINT 13 — BÀN GIAO CUỐI

Với Facebook dạng ảnh, bàn giao:

1. ảnh hoàn chỉnh;
2. chữ trên ảnh;
3. caption;
4. 5 hashtag;
5. ghi chú ngắn nếu còn dữ kiện pháp lý / hướng dẫn đang chờ cập nhật.

Chỉ được coi bài dạng ảnh là hoàn thành khi:

- ảnh đã được tạo và QA;
- hoặc người dùng chủ động yêu cầu dừng ở phần text.

---

# 4. SƠ ĐỒ FILE → CHECKPOINT

| Checkpoint | File bắt buộc |
|---|---|
| 0 Brief / chọn chủ đề | `ktdt-research-workflow.md` nếu cần |
| 1.1 Sự thật | `ktdt-research-workflow.md` + `ktdt-source-verification.md` |
| 1.2 Người đọc | `ktdt-research-workflow.md` |
| 1.3 Cạnh tranh | `ktdt-research-workflow.md` + `ktdt-platform-competitor-research.md` |
| 1.4 Cơ hội / hồ sơ | `ktdt-research-workflow.md` + `ktdt-research-output.md` |
| 2 Mục tiêu | hồ sơ nghiên cứu + DNA khi cần |
| 3 Góc | hồ sơ nghiên cứu |
| 4 Format Facebook | `ktdt-facebook-post-playbook.md` |
| 5 Hook | `ktdt-social-writing-dna.md` + `ktdt-hook-language-psychology.md` |
| 6 Retention | `ktdt-social-writing-dna.md` + `ktdt-body-writing-retention.md` |
| 7 CTA | DNA + body/retention |
| 8 Viết | DNA + body/retention + playbook nền tảng |
| 9 Đóng gói | Facebook playbook |
| 10 QA text | DNA + body/retention + playbook nền tảng |
| 11–12 Ảnh | Facebook playbook + tài sản brand của user |

---

# 5. LUẬT NGHIÊN CỨU CỨNG

Không dùng đối thủ, social hoặc comment để xác nhận luật.

Ưu tiên:

> **văn bản pháp lý gốc / cơ quan có thẩm quyền → nguồn chuyên môn đáng tin → báo chí → đối thủ / mạng xã hội**

Trong nguồn chính thức:

> **văn bản gốc có trọng số cao hơn bài giải thích về văn bản.**

Không:

- trộn dự thảo với quy định hiện hành;
- biến khả năng thành chắc chắn;
- suy thủ tục chưa ban hành;
- bịa dữ liệu cho đủ bảng;
- gọi một nội dung là hiệu quả chỉ vì thấy nó tồn tại.

Luật cốt lõi:

> **Câu chữ không được mạnh hơn bằng chứng.**

---

# 6. PHẠM VI HIỆN TẠI

Đã có quy chuẩn thử nghiệm và đã test thực tế cho:

- nghiên cứu sự thật / người đọc / cạnh tranh / cơ hội;
- DNA;
- hook;
- thân bài / retention;
- Facebook dạng ảnh;
- đóng gói Facebook;
- tạo ảnh và QA visual cơ bản.

Chưa khóa hoàn chỉnh:

- TikTok;
- Zalo;
- YouTube;
- video;
- hệ thống visual identity toàn diện;
- campaign / ad set / placement;
- đo hiệu quả creative sau chạy;
- vòng học từ dữ liệu chính chủ;
- QA đa nền tảng toàn diện.

Nếu người dùng yêu cầu phần chưa khóa, phải nói rõ đây là phần đang thử nghiệm và không tự nâng nó thành quy tắc lâu dài.

---

# 7. CÂU CĂN CHỈNH CHO AI

> **Đọc file điều phối trước. Chỉ mở file con đúng với checkpoint hiện tại. Làm một bước, đưa kết quả, chờ người dùng duyệt rồi mới đi tiếp. Quyết định đã chốt thì giữ nguyên. Nghiên cứu phải chắc trước khi sáng tạo; khi viết phải nói với một người thật trong một tình huống thật; khi đã chọn bài dạng ảnh thì chỉ hoàn thành sau khi ảnh đã được tạo và QA hoặc người dùng chủ động dừng ở phần text.**