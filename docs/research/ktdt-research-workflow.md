# QUY TRÌNH NGHIÊN CỨU NỘI DUNG MẠNG XÃ HỘI — KẾ TOÁN DIỆU TÂM

**Phiên bản:** 0.3  
**Ngày:** 07/10/2026  
**Trạng thái:** Đang thử nghiệm  
**Vai trò:** Quy trình bắt buộc để biến một chủ đề kế toán – thuế – doanh nghiệp thành một cơ hội nội dung đủ chắc trước khi chọn cách đánh và viết bài.

---

# 1. Mục tiêu

Nghiên cứu không kết thúc khi AI biết:

> “Tin này nói gì?”

Nghiên cứu chỉ kết thúc khi AI biết:

- sự thật nào đã chắc;
- ai thực sự quan tâm;
- họ đang hiểu sai hoặc chưa rõ điều gì;
- nội dung cạnh tranh đang nói gì;
- phần nào đã bão hòa;
- khoảng trống nào Diệu Tâm có thể chiếm;
- điều gì chưa được phép khẳng định.

Quy trình chuẩn:

> **Sự thật → Người đọc → Nội dung cạnh tranh → Cơ hội nội dung**

Chỉ khi đủ cả 4 lớp mới được chuyển sang bước **chọn cách đánh**.

---

# 2. Tiền bước — Quét chủ đề nóng khi chưa có chủ đề

Nếu người dùng chưa chọn chủ đề, AI **phải chủ động quét tin mới**, không hỏi người dùng “muốn viết gì?” trước.

## 2.1. Cửa sổ thời gian

Ưu tiên theo thứ tự:

1. **24–72 giờ gần nhất**;
2. nếu chưa có đủ ứng viên tốt → mở rộng tối đa **7 ngày**;
3. nội dung cũ hơn chỉ giữ nếu tuần hiện tại có:
   - diễn biến mới;
   - văn bản mới;
   - deadline mới;
   - thay đổi thực thi;
   - hoặc mức quan tâm mới có bằng chứng.

Nếu có khả năng truy cập web/search, bắt buộc dùng dữ liệu hiện tại.

Không được tự gọi một chủ đề là “hot” dựa trên kiến thức model cũ.

## 2.2. Phạm vi ưu tiên

Ưu tiên chủ đề liên quan trực tiếp tới:

- thuế;
- kế toán;
- tài chính / vận hành doanh nghiệp;
- hộ kinh doanh;
- hóa đơn / chứng từ;
- lao động / BHXH khi có tác động doanh nghiệp;
- thủ tục, chính sách hoặc deadline có ảnh hưởng thực tế đến khách hàng Diệu Tâm.

## 2.3. Năm tiêu chí sàng lọc

Một ứng viên mạnh nên đạt ít nhất **4/5**:

1. **Mới / nóng** — có diễn biến mới hoặc thời điểm cần chú ý.
2. **Liên quan đúng tệp** — ảnh hưởng rõ tới người đọc Diệu Tâm.
3. **Tác động thực tế** — có tiền, thời hạn, quyền lợi, nghĩa vụ, hồ sơ, rủi ro hoặc quyết định.
4. **Kiểm chứng được** — có nguồn đủ mạnh để nghiên cứu sâu.
5. **Có điểm căng thật** — có hiểu lầm, mâu thuẫn, thay đổi, chi phí ẩn hoặc câu hỏi chưa rõ.

## 2.4. Không đánh đồng “được đăng nhiều” với “hot”

Không chọn chủ đề chỉ vì:

- tiêu đề báo nghe lớn;
- nhiều trang đăng lại cùng một thông cáo;
- có từ “nóng”, “sốc”, “mới nhất”;
- một bài có lượt xem cao nhưng không biết bối cảnh;
- có khả năng kéo view nhưng ít giá trị cho người đọc Diệu Tâm.

## 2.5. Đầu ra shortlist

Đề xuất **3–5 chủ đề**.

Mỗi chủ đề phải nói ngắn gọn:

- chuyện gì mới;
- thời điểm / độ mới;
- ai bị ảnh hưởng;
- vì sao đáng viết ngay;
- điểm căng tiềm năng;
- mức độ chắc ban đầu của nguồn;
- đánh giá: **Nên làm / Có thể làm / Chưa nên làm**.

Cuối shortlist phải có:

> **KHUYẾN NGHỊ SỐ 1**

Nếu người dùng chỉ trả **OK**, mặc định chọn khuyến nghị số 1 để nghiên cứu sâu.

Đây chỉ là bước sàng lọc. Chưa được xem là nghiên cứu sâu và chưa được viết hook.

---

# 3. BƯỚC 1 — NGHIÊN CỨU SỰ THẬT

## Mục tiêu

Tách rõ:

> **điều đã chính thức → điều đang dự thảo → điều chưa chốt → điều chưa được phép nói chắc.**

Bước này phải tuân theo:

> `docs/research/ktdt-source-verification.md`

## Câu hỏi bắt buộc

AI phải trả lời được:

1. Sự thật trung tâm của chủ đề là gì?
2. Văn bản hoặc nguồn có thẩm quyền nào xác nhận?
3. Ngày ban hành và ngày hiệu lực là khi nào?
4. Áp dụng cho kỳ nào?
5. Ai thuộc phạm vi?
6. Điều kiện là gì?
7. Ngoại lệ là gì?
8. Có điều khoản chuyển tiếp không?
9. Con số nào là số thật, con số nào chỉ là ví dụ?
10. Phần nào hiện mới là dự thảo?
11. Phần nào vẫn chưa có hướng dẫn cuối cùng?
12. Điều gì tuyệt đối chưa được khẳng định?

## Cách làm

Ưu tiên đọc nguồn gốc trước.

Nguồn thứ cấp được dùng để:

- phát hiện vấn đề;
- giải thích;
- tìm câu hỏi;
- tìm tình huống;

nhưng không được thay thế nguồn gốc khi xác nhận luật.

Nếu có nguồn mâu thuẫn, phải giải quyết trước khi sang bước 2.

## Đầu ra bắt buộc

Phải tạo được một **hồ sơ sự thật** gồm:

- sự thật trung tâm;
- nguồn chính;
- trạng thái từng dữ kiện;
- ngày / kỳ áp dụng;
- đối tượng;
- điều kiện;
- ngoại lệ;
- điều chưa chốt;
- điều chưa được phép khẳng định.

## Điều kiện được đi tiếp

Chỉ sang bước 2 khi:

> **DỮ KIỆN CỐT LÕI ĐÃ CHẮC**

Nếu phần chưa chắc ảnh hưởng trực tiếp tới kết luận chính, phải dừng hoặc đổi góc nội dung.

---

# 4. BƯỚC 2 — NGHIÊN CỨU NGƯỜI ĐỌC

## Mục tiêu

Không hỏi chung chung:

> “Ai quan tâm chủ đề này?”

Phải xác định:

> **ai chịu tác động rõ nhất và họ cần quyết định điều gì.**

## Câu hỏi bắt buộc

1. Nhóm nào bị tác động trực tiếp nhất?
2. Nhóm nào chỉ quan tâm gián tiếp?
3. Họ đang có tiền, hồ sơ, thời hạn, nghĩa vụ hay quyết định nào liên quan?
4. Họ có thể đang hiểu sai điều gì?
5. Họ đang yên tâm nhầm ở đâu?
6. Điều gì khiến họ lo hoặc do dự?
7. Họ muốn biết câu trả lời nào nhất?
8. Họ cần làm gì sau khi hiểu nội dung?
9. Câu hỏi nào có khả năng xuất hiện trong tìm kiếm, bình luận hoặc tin nhắn?
10. Nhóm nào không nên là đối tượng chính dù tiêu đề có vẻ áp dụng rộng?

## Nguồn có thể dùng

- câu hỏi tìm kiếm;
- bình luận công khai;
- diễn đàn;
- mạng xã hội;
- nội dung hỏi đáp;
- phản ánh từ báo chí;
- dữ liệu khách hàng của Diệu Tâm nếu sau này có quyền dùng.

Những nguồn này dùng để hiểu người đọc, **không dùng để xác nhận luật**.

## Bắt buộc tìm “khoảng cách nhận thức”

Hoàn thành hai câu:

> **Người đọc có thể đang nghĩ:** ______

> **Điều họ thực sự cần biết thêm là:** ______

Nếu hai câu gần như giống nhau, chủ đề chưa có khoảng nhận thức đủ rõ.

## Đầu ra bắt buộc

Phải khóa được:

- người đọc chính;
- người đọc phụ;
- hiểu lầm / điểm mù;
- nỗi lo thực tế;
- quyết định họ cần đưa ra;
- câu hỏi thật;
- khoảng cách nhận thức;
- điểm căng tiềm năng.

## Điều kiện được đi tiếp

Chỉ sang bước 3 khi AI có thể nói rõ:

> **“Bài này đang nói với ai, họ đang nghĩ gì và tại sao họ phải quan tâm.”**

---

# 5. BƯỚC 3 — NGHIÊN CỨU NỘI DUNG CẠNH TRANH

## Mục tiêu

Không chỉ tìm “đối thủ đã viết gì”.

Phải biết:

- người khác đang chiếm góc nào;
- cách họ mở;
- định dạng họ dùng;
- phản ứng người xem;
- phần nào đã bị nói quá nhiều;
- phần nào chưa ai làm tốt.

Bước này phải tuân theo:

> `docs/research/ktdt-platform-competitor-research.md`

## Nguyên tắc nền tảng

> **Nghiên cứu thông tin ở nơi thông tin đáng tin nhất.  
> Nghiên cứu cách thu hút người xem ở chính nơi nội dung sẽ được đăng.**

Facebook → nghiên cứu Facebook.  
TikTok → nghiên cứu TikTok.  
YouTube → nghiên cứu YouTube.  
Zalo → nghiên cứu Zalo.

**Không mặc định phải nghiên cứu đủ cả bốn nền tảng.** Chỉ nghiên cứu nền tảng dự kiến đăng hoặc những nền tảng thật sự cần để so sánh. Nếu một nội dung sẽ triển khai đa nền tảng, phải tách dữ liệu và kết luận theo từng nền tảng, không trộn chung.

Không lấy:

> bài website đứng đầu tìm kiếm

để kết luận:

> cách đó sẽ thắng trên Facebook hoặc TikTok.

## Ba nhóm cần quan sát

- đối thủ kinh doanh trực tiếp;
- đối thủ nội dung;
- đối thủ tranh sự chú ý.

## Những gì cần ghi

Khi dữ liệu cho phép, ghi:

- chủ đề;
- đối tượng;
- lời hứa;
- góc;
- hook;
- dạng nội dung;
- hình/khung đầu;
- cấu trúc;
- phản ứng người xem;
- câu hỏi trong bình luận;
- phần còn thiếu.

## Luật về dữ liệu thiếu

Nếu nền tảng không cho đủ dữ liệu:

> **ghi rõ “chưa đủ dữ liệu”.**

Không được:

- suy lượt xem;
- suy mức độ lan truyền;
- dùng Google để giả làm dữ liệu TikTok;
- kết luận quảng cáo hiệu quả chỉ vì thấy nó trong thư viện quảng cáo;
- điền nhận định cho đủ bảng.

## Đầu ra bắt buộc

Phải phân biệt:

- nội dung đã bão hòa;
- nội dung đang có cạnh tranh;
- góc chưa được khai thác tốt;
- câu hỏi người xem còn bỏ ngỏ;
- dữ liệu nền tảng nào đủ / chưa đủ.

## Điều kiện được đi tiếp

Chỉ sang bước 4 khi có đủ căn cứ để nói:

> **“Nếu Diệu Tâm làm giống phần lớn nội dung hiện có, bài sẽ không có lý do đủ mạnh để tồn tại.”**

và chỉ ra được ít nhất một hướng khác biệt hợp lý.

Nếu mẫu quan sát còn nhỏ, phải gọi đó là **khoảng trống quan sát được / giả thuyết khoảng trống**, không được gọi chắc chắn là “khoảng trống của toàn thị trường”.

---

# 6. BƯỚC 4 — NGHIÊN CỨU CƠ HỘI NỘI DUNG

## Mục tiêu

Ghép ba lớp trước thành một quyết định:

> **Diệu Tâm nên chiếm góc nào và vì sao góc đó đáng viết ngay.**

Đây không phải bước nghĩ hook cuối cùng.

Đây là bước chọn **cơ hội nội dung**.

## Câu hỏi bắt buộc

1. Điều gì đáng nói nhất?
2. Điều gì đã quá bão hòa?
3. Điều gì người đọc đang cần nhưng nội dung hiện có chưa trả lời tốt?
4. Khoảng cách nhận thức mạnh nhất là gì?
5. Điểm căng nào là thật và phù hợp với Diệu Tâm?
6. Góc nào có thể tạo giá trị mà không cần phóng đại?
7. Góc nào giúp Diệu Tâm thể hiện chuyên môn tốt hơn đối thủ?
8. Nội dung có thể hứa điều gì mà chắc chắn trả được?
9. Điều gì phải loại khỏi bài để không loãng trọng tâm?
10. Có thể phát triển thành chuỗi hay không?

## Cấu trúc cơ hội nội dung

Phải khóa được:

- **Đối tượng chính**
- **Vấn đề họ quan tâm**
- **Khoảng cách nhận thức**
- **Điểm căng chính**
- **Nội dung đã bão hòa**
- **Khoảng trống**
- **Góc Diệu Tâm nên chiếm**
- **Lời hứa nội dung**
- **Giá trị thực tế người đọc nhận được**
- **Điều tuyệt đối không được nói quá**
- **Cơ hội tương tác**
- **Khả năng phát triển thành chuỗi**

## Lời hứa nội dung

Lời hứa phải:

- có ích;
- cụ thể;
- đúng bằng chứng;
- có thể trả được trong bài.

Không hứa:

> “giải quyết hoàn toàn”

nếu nội dung chỉ có thể giúp người đọc hiểu hoặc tự kiểm tra.

---

# 7. Chuẩn bàn giao

Kết quả cuối cùng phải được đóng gói theo:

> `docs/research/ktdt-research-output.md`

Không tự tạo một cấu trúc bàn giao khác nếu không có lý do rõ ràng.

---

# 8. Điều kiện kết thúc nghiên cứu

Nghiên cứu chỉ được kết thúc khi có đủ:

1. **Sự thật trung tâm**
2. **Điều đã chắc**
3. **Điều chưa được phép khẳng định**
4. **Người đọc chính**
5. **Họ đang nghĩ gì**
6. **Họ cần biết gì**
7. **Khoảng cách nhận thức**
8. **Điểm căng**
9. **Câu hỏi thật**
10. **Nội dung đã bão hòa**
11. **Nội dung đang cạnh tranh**
12. **Khoảng trống**
13. **Cơ hội của Diệu Tâm**
14. **Lời hứa nội dung khả thi**

Khi đủ:

> **ĐỦ DỮ KIỆN ĐỂ CHỌN CÁCH ĐÁNH**

Khi thiếu phần có thể làm sai hướng:

> **CHƯA ĐỦ DỮ KIỆN — chưa được viết bài.**

---

# 9. Những lỗi nghiên cứu phải tránh

Không được:

- gom nhiều nguồn nhưng không kết luận;
- dùng đối thủ để xác nhận luật;
- trộn dự thảo với quy định chính thức;
- coi nhiều bài đăng lại là bằng chứng chủ đề hấp dẫn;
- coi lượt xem cao là bằng chứng nội dung đúng;
- cố hoàn thành đủ nền tảng khi dữ liệu không có;
- chọn góc chỉ vì dễ viết hook;
- nghiên cứu người đọc quá rộng kiểu “mọi doanh nghiệp”;
- nhồi mọi phát hiện vào một bài;
- chuyển sang viết khi chưa biết bài này khác gì nội dung đã có.

---

# 10. Nguyên tắc bàn giao sang bước chọn cách đánh

Khối nghiên cứu không quyết định:

- câu hook cuối cùng;
- cấu trúc bài cuối;
- số slide;
- lời kêu gọi cuối;
- hình ảnh;
- bố cục thiết kế.

Nó chỉ bàn giao:

> **sự thật + người đọc + cạnh tranh + cơ hội**

Bước **chọn cách đánh** mới quyết định:

- mục tiêu nội dung;
- góc chính;
- định dạng;
- cơ chế câu mở đầu;
- đường giữ người xem;
- lời kêu gọi hành động.

---

# 11. Câu căn chỉnh cho AI

> **Đừng vội hỏi “viết gì cho hay”. Hãy làm rõ trước: điều gì là sự thật, ai thật sự quan tâm, họ đang hiểu thiếu ở đâu, người khác đã nói gì và Diệu Tâm còn điều gì đáng nói hơn.**
