# KẾ TOÁN DIỆU TÂM — SOCIAL CONTENT SKILL

**Phiên bản:** 0.8  
**Ngày:** 07/10/2026  
**Vai trò:** File điều phối trung tâm / runtime orchestrator  
**Trạng thái:** Đang phát triển — Facebook dạng ảnh đã test thực tế; TikTok writing đang ở playbook thử nghiệm v0.1.

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

## Quy ước duyệt checkpoint

Ở cuối mỗi checkpoint, AI chỉ xin duyệt **một lần**.

- AI trình bày kết quả của checkpoint hiện tại và dừng.
- Khi người dùng trả lời `OK`, `duyệt`, `chốt`, `tiếp tục` hoặc chọn một phương án, điều đó đồng thời có nghĩa:
  1. duyệt checkpoint hiện tại;
  2. khóa các decision lock vừa được chốt;
  3. **ngay ở turn kế tiếp, AI phải thực hiện checkpoint tiếp theo và đưa kết quả của checkpoint đó.**

Không được trả lời kiểu:

> “Đã chốt. Hãy nói OK lần nữa để tôi sang bước tiếp.”

Một checkpoint = tối đa một lần duyệt, trừ khi người dùng yêu cầu sửa.

## Chế độ AUTO-START khi user chỉ đưa URL skill

Prompt tối thiểu hợp lệ:

> **“Tiến hành chạy skill https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/SKILL.md”**

Khi nhận đúng kiểu prompt này mà **không có chủ đề, nền tảng hoặc mục tiêu cụ thể**, AI **không được hỏi lại “muốn viết chủ đề gì?”**.

AI phải tự khởi động như sau:

1. đọc `SKILL.md`;
2. mở `docs/research/ktdt-research-workflow.md`;
3. chạy **CHECKPOINT A — Quét chủ đề nóng**;
4. tìm các chủ đề mới / nóng / sốt / đang được quan tâm trong **24–72 giờ gần nhất**;
5. nếu chưa có đủ ứng viên tốt, mở rộng cửa sổ tối đa **7 ngày**;
6. chỉ giữ chủ đề liên quan rõ đến:
   - thuế;
   - kế toán;
   - hộ kinh doanh;
   - doanh nghiệp;
   - hóa đơn;
   - lao động / BHXH khi có tác động vận hành doanh nghiệp;
   - chính sách tài chính / thủ tục có ảnh hưởng thực tế tới nhóm khách hàng Diệu Tâm;
7. xếp hạng và đề xuất chủ đề tốt nhất;
8. dừng để người dùng duyệt.

Nếu người dùng chỉ trả **OK** mà không chọn số khác, mặc định hiểu là:

> **duyệt chủ đề AI đang khuyến nghị số 1.**

Sau đó AI phải chạy ngay checkpoint nghiên cứu sâu tiếp theo ở turn kế tiếp.

### Mặc định nền tảng khi AUTO-START

Do quy trình hiện tại đã được kiểm chứng sâu nhất cho Facebook dạng ảnh:

> **Nếu user không chỉ định nền tảng, mặc định nền tảng đích = Facebook dạng ảnh.**

Đây là default runtime, không phải quy luật thương hiệu vĩnh viễn. Nếu user chỉ định nền tảng khác thì dùng nền tảng user chọn.

### Không yêu cầu prompt dài

Không yêu cầu người dùng phải ghi thêm:

- chủ đề;
- đối tượng;
- góc;
- mục tiêu;
- định dạng;

nếu họ muốn skill tự tìm từ đầu.

Không yêu cầu người dùng paste lại file con nếu URL trong danh bạ có thể truy cập được.

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

### TikTok writing
- Path: `docs/platform/ktdt-tiktok-writing-playbook.md`
- URL: https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/platform/ktdt-tiktok-writing-playbook.md
- Dùng ở: phần chữ TikTok — caption hoặc text post, search keyword, nhịp chữ, CTA và hashtag. **Không dùng để sản xuất video.**

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

- chỉ hỏi về chủ đề nếu user **đã yêu cầu một phạm vi hẹp nhưng phạm vi đó vẫn mơ hồ**;
- không hỏi chủ đề trong AUTO-START: phải tự quét chủ đề nóng;
- không hỏi nền tảng trong AUTO-START: mặc định Facebook dạng ảnh;
- chưa có logo nhưng người dùng yêu cầu phải dùng đúng logo;
- chưa rõ mục tiêu kinh doanh khi mục tiêu quyết định cách đánh.

---

# 3. RUNTIME FLOW — CHẠY TỪNG BƯỚC

## CHECKPOINT 0 — Xác định chế độ chạy

### Nếu user đã cho chủ đề

Ghi nhận:

- chủ đề;
- nền tảng nếu có;
- mục tiêu nếu có;
- tài sản đầu vào nếu có.

Nếu không có nền tảng → mặc định Facebook dạng ảnh, trừ khi yêu cầu cho thấy nền tảng khác.

Sau đó đi thẳng tới **CHECKPOINT 1.1 — Nghiên cứu sự thật**. Không cần xin một lượt OK chỉ để xác nhận lại brief nếu brief đã rõ.

### Nếu user KHÔNG cho chủ đề

Không hỏi lại.

Chạy ngay **CHECKPOINT A — QUÉT CHỦ ĐỀ NÓNG** bên dưới.

---

## CHECKPOINT A — QUÉT CHỦ ĐỀ NÓNG / HOT TREND

### Bắt buộc đọc

- `docs/research/ktdt-research-workflow.md`
- URL: https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/research/ktdt-research-workflow.md

Khi cần kiểm nhanh độ chắc của ứng viên, dùng thêm:

- `docs/research/ktdt-source-verification.md`
- URL: https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/research/ktdt-source-verification.md

### Cửa sổ thời gian

1. ưu tiên tin / thay đổi / thảo luận đáng chú ý trong **24–72 giờ gần nhất**;
2. nếu chưa có đủ ứng viên chất lượng → mở rộng tối đa **7 ngày**;
3. chủ đề cũ hơn 7 ngày chỉ được giữ nếu **tuần này có diễn biến mới, deadline mới hoặc mức quan tâm mới**.

### Phải dùng dữ liệu hiện tại

Nếu môi trường có web/search, phải research web hiện tại.

Không được dùng kiến thức cũ trong model để tự tuyên bố một chủ đề đang “hot”.

### Lọc chủ đề

Mỗi ứng viên phải có ít nhất 4/5 yếu tố:

1. **Mới / đang nóng** — có diễn biến mới hoặc deadline gần.
2. **Đúng tệp Diệu Tâm** — ảnh hưởng rõ đến doanh nghiệp, hộ kinh doanh, kế toán / vận hành.
3. **Tác động thực tế** — tiền, thuế, hồ sơ, quyền lợi, nghĩa vụ, thời hạn hoặc quyết định.
4. **Kiểm chứng được** — có nguồn đủ mạnh để research sâu.
5. **Có điểm căng nội dung** — tồn tại hiểu lầm, thay đổi, mâu thuẫn, chi phí hoặc câu hỏi thật.

Không coi một chủ đề là hot chỉ vì nhiều báo copy cùng một thông cáo.

### Đầu ra

Đề xuất **3–5 chủ đề**.

Mỗi chủ đề ghi rất ngắn:

- chuyện gì vừa xảy ra;
- thời điểm / độ mới;
- ai bị ảnh hưởng;
- vì sao đáng làm ngay;
- điểm căng tiềm năng;
- độ chắc nguồn ban đầu;
- đánh giá: **Nên làm / Có thể làm / Chưa nên làm**.

Cuối cùng chọn:

> **KHUYẾN NGHỊ SỐ 1**

và giải thích ngắn vì sao.

### Gate

> **Dừng sau shortlist. Nếu user nói OK → mặc định chọn KHUYẾN NGHỊ SỐ 1, khóa chủ đề và ở turn kế tiếp chạy ngay CHECKPOINT 1.1. Nếu user chọn chủ đề khác → khóa chủ đề đó và chạy CHECKPOINT 1.1.**

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
> **Trình bày mục tiêu và dừng. Khi người dùng OK/chọn phương án → khóa mục tiêu và ở turn kế tiếp chạy ngay CHECKPOINT 3.**

---

## CHECKPOINT 3 — Chốt GÓC CHÍNH

### Dùng
- hồ sơ nghiên cứu;
- mục tiêu đã khóa.

### Làm
Đề xuất góc chính mạnh nhất, giải thích ngắn vì sao nó phù hợp với người đọc + khoảng trống + mục tiêu.

Không viết hook ở bước này.

### Gate
> **Trình bày góc và dừng. Khi người dùng OK/chọn phương án → khóa góc và ở turn kế tiếp chạy ngay CHECKPOINT 4.**

---

## CHECKPOINT 4 — Chốt ĐỊNH DẠNG

### Nếu Facebook dạng ảnh, bắt buộc đọc
- `docs/platform/ktdt-facebook-post-playbook.md`
- URL: https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/platform/ktdt-facebook-post-playbook.md

### Nếu TikTok writing, bắt buộc đọc
- `docs/platform/ktdt-tiktok-writing-playbook.md`
- URL: https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/platform/ktdt-tiktok-writing-playbook.md

### Làm với Facebook
Mặc định đưa 2 lựa chọn:

- **1 ảnh**;
- **3 ảnh**.

AI khuyến nghị một phương án dựa trên số bước nhận thức người xem cần đi qua.

### Làm với TikTok writing
Chỉ chọn định dạng chữ:

- **Caption / phần mô tả TikTok**;
- **TikTok Text Post**.

Không mở nhánh sản xuất video nếu user chỉ yêu cầu viết bài TikTok.

### Gate
> **Trình bày lựa chọn format phù hợp và khuyến nghị rồi dừng. Khi người dùng OK/chọn phương án → khóa format và ở turn kế tiếp chạy ngay CHECKPOINT 5.**

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
> **Trình bày các hook và khuyến nghị rồi dừng. Khi người dùng OK/chọn một hook → khóa nguyên văn hook và ở turn kế tiếp chạy ngay CHECKPOINT 6.**

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
> **Trình bày retention path và dừng. Khi người dùng OK → khóa cấu trúc và ở turn kế tiếp chạy ngay CHECKPOINT 7.**

---

## CHECKPOINT 7 — Chốt CTA

### Bắt buộc dùng
- `docs/brand/ktdt-social-writing-dna.md`
- `docs/content/ktdt-body-writing-retention.md`

### Làm
Đề xuất CTA chính phù hợp mục tiêu đã khóa. CTA phải đi ra tự nhiên từ giá trị bài, không mặc định bán dịch vụ.

### Gate
> **Trình bày CTA và dừng. Khi người dùng OK/chọn phương án → khóa CTA và ở turn kế tiếp chạy ngay CHECKPOINT 8.**

---

## CHECKPOINT 8 — Viết BẢN NỘI DUNG HOÀN CHỈNH

### Bắt buộc đọc
- `docs/brand/ktdt-social-writing-dna.md`
- `docs/content/ktdt-body-writing-retention.md`
- nếu Facebook: `docs/platform/ktdt-facebook-post-playbook.md`
- nếu TikTok: `docs/platform/ktdt-tiktok-writing-playbook.md`

URLs:
- https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/brand/ktdt-social-writing-dna.md
- https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/content/ktdt-body-writing-retention.md
- https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/platform/ktdt-facebook-post-playbook.md
- https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/platform/ktdt-tiktok-writing-playbook.md

### Luật
- giữ nguyên các decision lock;
- hook caption không được tự đổi;
- hook mở món nợ nào, thân bài trả món nợ đó sớm;
- nói với một người thật trong một tình huống thật;
- không để người đọc phải đoán `cụ thể là gì?`;
- xưng hô có chức năng;
- CTA đúng bản đã khóa.

### Gate
> **Đưa bản viết và dừng. Khi người dùng OK → nếu Facebook chạy CHECKPOINT 9; nếu TikTok chạy CHECKPOINT 9T.**

---

## NHÁNH NỀN TẢNG SAU CHECKPOINT 8

- Nếu nền tảng đích là **Facebook dạng ảnh** → chạy CHECKPOINT 9 đến CHECKPOINT 13.
- Nếu nền tảng đích là **TikTok writing** → chạy CHECKPOINT 9T đến CHECKPOINT 11T.
- Nếu nền tảng khác và repo chưa có playbook tương ứng → không áp playbook Facebook/TikTok. Nói rõ phần đó chưa khóa và đưa kế hoạch thử nghiệm để user duyệt.
- Không được bê quy tắc Facebook sang TikTok hoặc ngược lại.

---

## CHECKPOINT 9T — ĐÓNG GÓI TIKTOK WRITING

### Bắt buộc đọc
- `docs/platform/ktdt-tiktok-writing-playbook.md`
- URL: https://github.com/quoctran-2608/skill_KTDieuTam_Social_Article/blob/main/docs/platform/ktdt-tiktok-writing-playbook.md

### Làm
Tách rõ:

1. hook / câu đầu;
2. caption hoặc text post;
3. CTA;
4. cụm từ khóa tìm kiếm chính;
5. 3–5 hashtag.

Không tạo shot list, cảnh quay, timeline dựng hay voiceover nếu user chỉ yêu cầu viết bài TikTok.

Keyword và hashtag là dữ liệu động. Nếu có web hoặc công cụ TikTok phù hợp thì research hiện tại trước khi chốt.

### Gate
> **Đưa bản đóng gói TikTok và dừng. Khi user OK → khóa text / CTA / keyword / hashtag và chạy CHECKPOINT 10T.**

---

## CHECKPOINT 10T — QA TIKTOK WRITING

### Bắt buộc đọc
- `docs/brand/ktdt-social-writing-dna.md`
- `docs/content/ktdt-body-writing-retention.md`
- `docs/platform/ktdt-tiktok-writing-playbook.md`

### Kiểm
- factual / bằng chứng;
- hook debt đã được trả sớm;
- từ khóa chính rõ và tự nhiên;
- không keyword stuffing;
- nhịp chữ dễ quét;
- không copy nguyên caption Facebook;
- CTA chỉ một hành động chính;
- hashtag liên quan thật;
- không tự chuyển sang sản xuất video.

### Gate
> **Nếu đạt, báo `TIKTOK TEXT ĐÃ ĐỦ CHUẨN` và dừng. Khi user OK → chạy CHECKPOINT 11T.**

---

## CHECKPOINT 11T — BÀN GIAO TIKTOK

Bàn giao:

1. hook / câu đầu;
2. caption hoặc text post hoàn chỉnh;
3. CTA;
4. từ khóa tìm kiếm chính;
5. 3–5 hashtag;
6. ghi chú factual nếu có phần đang chờ hướng dẫn chính thức.

Không thêm tài liệu sản xuất video.

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
> **Đưa bản đóng gói và dừng. Khi người dùng OK → khóa chữ trên ảnh / caption / hashtag và ở turn kế tiếp chạy ngay CHECKPOINT 10.**

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
> **Nếu đạt, báo `TEXT ĐÃ ĐỦ CHUẨN ĐỂ TẠO ẢNH` và dừng. Khi người dùng OK → ở turn kế tiếp chạy ngay CHECKPOINT 11.**

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
> **Trình bày concept ảnh và hỏi tạo ảnh ngay không. Khi người dùng OK → ở turn kế tiếp tạo ảnh ngay theo CHECKPOINT 12, không hỏi lại các điểm đã khóa.**

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
| 0 Chế độ chạy | `SKILL.md` | 
| A Quét chủ đề nóng | `ktdt-research-workflow.md` + `ktdt-source-verification.md` khi cần |
| 1.1 Sự thật | `ktdt-research-workflow.md` + `ktdt-source-verification.md` |
| 1.2 Người đọc | `ktdt-research-workflow.md` |
| 1.3 Cạnh tranh | `ktdt-research-workflow.md` + `ktdt-platform-competitor-research.md` |
| 1.4 Cơ hội / hồ sơ | `ktdt-research-workflow.md` + `ktdt-research-output.md` |
| 2 Mục tiêu | hồ sơ nghiên cứu + DNA khi cần |
| 3 Góc | hồ sơ nghiên cứu |
| 4 Format Facebook | `ktdt-facebook-post-playbook.md` |
| 4 Format TikTok writing | `ktdt-tiktok-writing-playbook.md` |
| 5 Hook | `ktdt-social-writing-dna.md` + `ktdt-hook-language-psychology.md` |
| 6 Retention | `ktdt-social-writing-dna.md` + `ktdt-body-writing-retention.md` |
| 7 CTA | DNA + body/retention |
| 8 Viết | DNA + body/retention + playbook nền tảng |
| 9 Đóng gói Facebook | Facebook playbook |
| 10 QA text Facebook | DNA + body/retention + Facebook playbook |
| 11–12 Ảnh | Facebook playbook + tài sản brand của user |
| 9T Đóng gói TikTok | TikTok writing playbook |
| 10T QA TikTok | DNA + body/retention + TikTok writing playbook |
| 11T Bàn giao TikTok | TikTok writing playbook |

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

- TikTok **video production** (TikTok writing đã có playbook thử nghiệm);
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

> **Nếu user chỉ nói “Tiến hành chạy skill [URL]”, hãy tự bắt đầu bằng quét chủ đề nóng trong ngày/tuần, không hỏi họ muốn viết gì. Sau đó làm một checkpoint, đưa kết quả, chờ duyệt rồi tự chạy checkpoint kế tiếp. Quyết định đã chốt thì giữ nguyên. Nghiên cứu phải chắc trước khi sáng tạo; khi viết phải nói với một người thật trong một tình huống thật; khi đã chọn bài dạng ảnh thì chỉ hoàn thành sau khi ảnh đã được tạo và QA hoặc người dùng chủ động dừng ở phần text.**