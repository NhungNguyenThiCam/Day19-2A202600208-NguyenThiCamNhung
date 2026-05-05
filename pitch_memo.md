# PITCH MEMO — VinEdu RAG

**Student:** Nguyễn Thị Cẩm Nhung | **Date:** 24/04/2026 | **Audience:** Seed VC

---

## 1. THE PROBLEM

1.4 triệu sinh viên ĐH Việt Nam mất 3-5h/tuần tua video bài giảng thủ công — 60% không biết ôn từ đâu trước kỳ thi, dẫn đến GPA thấp và trượt môn dù đã xem đủ bài giảng. Giảng viên lớp đông (500+ SV) bị quá tải >10h/tuần trả lời 70% câu hỏi lặp lại — không có feedback loop nào map được "sinh viên không hiểu chỗ nào".

---

## 2. THE INSIGHT

Các trường đại học Việt Nam không thiếu nội dung bài giảng — họ thiếu **feedback loop giữa "sinh viên không hiểu chỗ nào" và "giảng viên cần dạy lại chỗ đó"**. Video bài giảng là dataset lớn nhất chứa gap này, nhưng không ai khai thác được.

**Founder-market fit:** Là sinh viên CNTT từng thấy 70% câu hỏi trên group lớp là lặp lại, và giảng viên mất 10h/tuần trả lời — tôi nhận ra đây không phải vấn đề "search", mà là vấn đề "knowledge gap mapping" chưa được tự động hóa.

---

## 3. THE SOLUTION

**VinEdu** — Công cụ duy nhất tại Việt Nam giúp sinh viên tìm đúng đoạn thầy giải bài trong video 2 giờ — trong 5 giây — cứu họ khỏi trượt môn đêm nay. Sinh viên không trả tiền cho "tốt nghiệp loại Giỏi năm sau" — họ trả cho "pass môn này tuần tới".

**Differentiator:** Không chỉ là "Ctrl+F cho video". VinEdu biến 90 phút bài giảng bỏ lỡ thành 5 phút targeted review, capture 70% 'exam-critical info' ẩn trong whiteboard notes. Đồng thời cung cấp **Knowledge Gap Heatmap** cho giảng viên — map được chính xác chỗ nào cả lớp yếu.

**Tech:** Multimodal RAG với Gemini 2.5 Flash (1M-2M tokens context), MMR thay Cross-Encoder (tối ưu chi phí), Dashboard cho GV theo dõi confusion signals và điều chỉnh giảng dạy hàng tuần.

---

## 4. WHY NOW

**3 yếu tố đồng thời:**
1. **Chi phí AI giảm 90%:** Gemini 2.5 Flash (Q4/2024) giá 1/10 GPT-4V, làm index hàng trăm giờ video khả thi về kinh tế — lần đầu tiên startup có thể build multimodal RAG mà không cần $10M seed.
2. **Behavior shift:** 81% SV Gen Z VN (Decision Lab 2023) học qua video, attention span 8s — không còn đọc textbook. Video là primary learning medium, nhưng không có tool search.
3. **Áp lực thi cử:** Thất nghiệp thanh niên 11.24% (Q3/2024), Fresher jobs -37% (Joboko 2025) — SV trả tiền cho thứ cứu họ khỏi trượt môn đêm nay, không phải tốt nghiệp loại Giỏi năm sau.

---

## 5. TRACTION / PROOF

**⚠️ CAVEAT QUAN TRỌNG:** Pilot 50 SV (4 tuần) — sample size nhỏ, likely "friendly user bias", đang mở rộng lên 200 users trong 8 tuần để validate.

**Early Signals (NOT proven traction):**
- **Time-to-Answer:** 15-20p → <5s (đo được bằng analytics — real improvement)
- **70% click Timestamp ngay lần đầu** (chưa đo bounce rate — họ có stay hay quay lại video?)
- **D7 Retention: 68%** (quá sớm để claim habit formation — cần D30. Có thể là "novelty effect")
- **Sean Ellis: 42%** (21/50 "Very disappointed" — strongest signal, nhưng 1 người đổi ý → drop below 40%)

**Unit Economics (PROJECTED, not proven):**
- **LTV/CAC = 4.8x** — LTV: 199k×6 tháng = 1,194k (projected, chưa có churn data); CAC: 250k (Facebook Ads pilot, có thể optimistic cho EdTech VN)
- **Payback: 4.2 tháng** (dựa trên projected LTV)

**Teacher Impact (Real):** GV giảm 80% thời gian QA (10h→2h/tuần), phát hiện 3 chủ đề "nóng" cả lớp yếu qua Knowledge Gap Heatmap.

---

## 6. THE ASK

**500M VND seed** để scale 50→500 WAU trong 6 tháng:

**Use of Funds:**
- 40% (200M): Hire 2 engineers build Teacher Dashboard v2.0
- 30% (150M): Ký 3 trường ĐH (Bách Khoa HN, UEH, FTU), tích hợp LMS API
- 25% (125M): Paid ads (FB/TikTok), CAC target 250k
- 5% (25M): Ops, server, legal

**Milestone 6 tháng:** 500 WAU, MRR 100M, 3 university partnerships

**Milestone 12 tháng:** 5,000 paying users, MRR 1B, 5 trường ĐH

---

## MOAT (If OpenAI does this?)

**Thật lòng:** Hiện tại moat yếu. Nếu OpenAI ship "Media Search API" tuần sau, tech stack của tôi (MMR, Gemini Flash) bay màu.

**Moat thực sự (đang build):**

1. **Data Flywheel:** Từ pilot 50 users, đã thu được 2,400+ câu hỏi tiếng Việt về CNTT/Kinh tế — map được "confusion signals" tại timestamp cụ thể (ví dụ: 73% SV hỏi về "con trỏ trong C" tại phút 34-38 của bài giảng). Mỗi câu hỏi → retrain retrieval ranking → system càng chính xác cho context VN. OpenAI không có dataset này — họ train trên English lectures.

2. **Teacher Workflow Lock-in:** 3 GV pilot đã depend vào Knowledge Gap Heatmap để prep bài tuần sau — không còn đoán "lớp yếu chỗ nào". Khi GV điều chỉnh giảng dạy dựa trên tool hàng tuần → switching cost cao. Không phải optional tool, mà là "system of record" cho teaching effectiveness.

3. **LMS Integration Depth:** Đang tích hợp Moodle API của BK HN (attendance + assignment data) → biết chính xác SV nào miss bài, SV nào nộp bài trễ → personalized review. OpenAI không có sales team VN để build mối quan hệ từng trường.

**Nếu OpenAI thực sự launch:** Pivot hoàn toàn sang B2B — bán cho trường như "Teaching Analytics Platform", không phải "Student Search App". Compete trên workflow integration, không phải AI quality.

---

