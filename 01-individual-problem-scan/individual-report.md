# 01 — Individual Problem Scan

| # | Lăng kính | Problem quan sát được | Ai chịu ảnh hưởng? | Dấu hiệu thật |
|---|---        |---                    |---                 |---            |
1 | Lặp lại | Setup venv, PATH và install lại thư viện mỗi khi clone repo/bắt đầu lab mới | Dev, Sinh viên IT | Mất khoảng 30 phút/lần
2 | Lặp lại | Soạn tin nhắn update tiến độ công việc hàng ngày vào nhóm chat cùng format | Cả team, Leader | Mất khoảng 10 phút/ngày
3 | Tốn thời gian | Đọc và tóm tắt tài liệu kỹ thuật/slide tiếng Anh 30-50 trang trước buổi học | Sinh viên, Dev | Mất khoảng 90 phút/bài
4 | Tốn thời gian | Tự debug lỗi terminal/syntax đỏ bằng cách google từng dòng log lỗi | Dev, Tester | Mất khoảng 45 phút/lỗi
5 | AI có thể tốt hơn | Notion/Trello không tự gợi ý ưu tiên task theo Impact/Effort | Leader, PM | Task nhiều nhưng priority mơ hồ
6 | AI có thể tốt hơn | Tìm lại đoạn code snippet hoặc giải pháp đã từng dùng trong project cũ rất khó | Dev | Mất khoảng 15 phút/lần tìm
7 | Pain từ người khác | Dev/Mem phải hỏi lại vì requirement/kịch bản từ Leader mập mờ, thiếu thông số | Dev, Designer | Hỏi lại 2-3 lần/spec
8 | Pain từ người khác | Thành viên nhóm phản hồi ý kiến gắt gao hoặc giao tiếp bất đồng gây nghẽn tiến độ | Cả team, Leader | Mất 1-2 ngày tranh luận
9 | Tốn thời gian | Thử và sai (trial & error) nhiều lần để chỉnh prompt ra đúng định dạng mong muốn | Content Creator, Dev | Mất khoảng 60 phút/prompt
10 | Lặp lại | Convert dữ liệu thô từ file log/text sang bảng Markdown hoặc định dạng JSON | Dev, Data analyst | Lặp lại mỗi lần báo cáo

## Top 3
| Rank | Problem | Vì sao chọn | Điều còn chưa chắc |
|---|---|---|---|
1| Tóm tắt & Lọc tài liệu kỹ thuật tiếng Anh (Slide/PRD/Paper) | Workflow rõ ràng, diễn ra hàng tuần, metric đo lường thời gian giảm tiết kiệm rất tốt | Đánh giá độ "hiểu sâu" của bản tóm tắt thế nào để người dùng không bỏ sót ý quan trọng 
2| Tự động Debug & Phân tích lỗi Terminal/Code | TPain point rất thật và tức thì khi dev/học bài, AI xử lý ngữ cảnh log lỗi rất giỏi | Cách giới hạn ngữ cảnh (context window) khi codebase/log lỗi quá dài
3| Phân chia task nhóm & Gợi ý ưu tiên theo Impact/Effort | Giải quyết xung đột/đùn đẩy việc trong nhóm, impact rộng đến cả team | Khó bắt AI hiểu hết ngữ cảnh ẩn (subtext) và năng lực thực tế của từng thành viên

## Problem Card #1 — Tóm tắt & Lọc tài liệu kỹ thuật/slide tiếng Anh

**Problem 1 câu:**  
Sinh viên và Dev tốn quá nhiều thời gian đọc thủ công tài liệu kỹ thuật/slide tiếng Anh dài 30-50 trang để lọc kiến thức cốt lõi trước mỗi buổi học/sprint.

**Actor:**  
Sinh viên IT, Lập trình viên

**Thời điểm / bối cảnh:**  
trước mỗi buổi học/sprint.

**Current workflow:**

```text
1. Tải file PDF/Slide
2. Mở tài liệu đọc lần lượt
3. Vừa đọc vừa dịch từng đoạn
4. Ghi chép note thủ công
5. Tổng hợp thành dàn ý ôn tập
```

**Bottleneck:**  
Khâu đọc-dịch-ghi chép thủ công tốn 60–90 phút nhưng vẫn bỏ sót hoặc không đọng lại cấu trúc kiến thức.

**Impact:**  
Tốn năng lượng não bộ trước khi bắt tay vào làm bài thực hành, trễ deadline chuẩn bị bài.

**Success metric:**  
Giảm thời gian chuẩn bị tài liệu từ 60 phút xuống < 10 phút; người dùng trả lời đúng 80%+ câu hỏi kiểm tra nhanh từ bản tóm tắt.

**Non-AI alternative:**  
Đọc lướt (skimming) phần kết luận/mục lục hoặc mượn vở/note của bạn khác.
**AI hypothesis:**  
Nếu dùng RAG/LLM phân rã tài liệu theo khung First Principles và tự tạo flashcard Q&A, người dùng sẽ nắm 80% cốt lõi trong 5 phút.

**Quick gut:**  
Agent

### Draft current workflow
```text

CURRENT STATE - 60-90 phút:
[Tải PDF] 
-> [Đọc & Dịch từng trang]
-> [Note thủ công] <-- BOTTLENECK
-> [Tổng hợp dàn ý] 
-> [Xong]
```

### Draft future workflow

```text

FUTURE STATE - < 10 phút:
[Upload PDF] 
-> [AI Extract Core & Build Q&A]
-> [Human Review & Học nhanh] <-- HUMAN BOUNDARY 
-> [Ghi nhớ/Áp dụng]

Fallback: AI tóm tắt sai → Prompt AI lại với định dạng ngắn hơn / Đổi AI khác
```
## Problem Card #2 — Tự động Debug & Phân tích lỗi Terminal/Code

**Problem 1 câu:**  
Dev và sinh viên IT mất nhiều giờ "thử và sai" khi tự mò lỗi Terminal/syntax bằng cách Google từng dòng log lỗi rời rạc.

**Actor:**  
Sinh viên IT, Lập trình viên, Tester

**Thời điểm / bối cảnh:**  
Đang làm lab/code project

**Current workflow:**

```text
1. Chạy lệnh bị lỗi
2. Copy dòng log báo đỏ
3. Google/Search StackOverflow
4. Thử áp dụng sửa
5. Vẫn lỗi, lặp lại tìm kiếm
```

**Bottleneck:**  
Mất thời gian đọc hàng chục thread Forum không đúng nguyên nhân góc (root cause) của môi trường cá nhân.

**Impact:**  
Bị nghẽn tiến độ công việc, gây ức chế và tốn nhiều giờ vô ích cho lỗi nhỏ.

**Success metric:**  
Giảm thời gian sửa các lỗi syntax/môi trường thông thường từ 45 phút xuống < 3 phút.

**Non-AI alternative:**  
Hỏi bạn bè/Mentor hoặc xóa đi cài lại toàn bộ môi trường từ đầu.

**AI hypothesis:**  
Nếu truyền log lỗi + thông tin môi trường (HĐH, phiên bản Python/Tools) cho AI, AI có thể chỉ ra Root Cause và câu lệnh sửa chính xác ngay lần đầu.

**Quick gut:**  
Rule / Workflow (Dùng Prompt cấu trúc sẵn bắt buộc quăng thêm Context môi trường).

### Draft current workflow
```text
CURRENT STATE — Tốn 45 phút/lỗi
[Chạy lệnh lỗi] 
─► [Copy log báo đỏ] 
─► [Google / StackOverflow] ──◄ Bottleneck: Mất thời gian thử sai 
─► [Thử áp dụng lệnh sửa] 
─► [Sửa xong]

```

### Draft future workflow

```text
FUTURE STATE — Ngắn hơn (< 3 phút)
[Log lỗi + Context] 
─► [AI Scan Log & Root Cause] 
─► [AI Gợi ý lệnh Fix] ──◄ Human Boundary: Kiểm tra & Chạy lệnh 
─► [Chạy lệnh Fix]
                               
FALLBACK: Chạy lệnh AI gợi ý vẫn lỗi -> Cung cấp thêm OS/Version/Env log cho AI OR Search StackOverflow

```

## Problem Card #3 — Weekly Report

**Problem 1 câu:**  
Lập kế hoạch đồ án nhóm thường bị phân công cảm tính, không phân biệt được task quan trọng và task tốn sức dẫn đến đùn đẩy việc và trễ deadline.

**Actor:**  
Leader nhóm, Thành viên đồ án.

**Thời điểm / bối cảnh:**  
Buổi họp Kick-off nhóm / Đầu Sprint mới

**Current workflow:**

```text
1. Liệt kê danh sách việc
2. Họp nhóm bàn giao
3. Thành viên tự nhận task cảm tính
4. Làm bị trễ/quá sức
5. Cãi nhau/Đùn đẩy
```

**Bottleneck:**  
Không đo lường được nỗ lực (Effort) thực tế của task và không minh bạch về tác động (Impact).

**Impact:**  
Mất đoàn kết nhóm, đồ án không có điểm thưởng cho các tính năng quan trọng (Quick Wins).

**Success metric:**  
100% task được phân loại rõ ràng trong Ma trận Impact/Effort; tỷ lệ trễ deadline nhóm giảm 50%.

**Non-AI alternative:**  
Leader tự dùng kinh nghiệm để ép chỉ tiêu và áp đặt phân công.

**AI hypothesis:**  
Nếu AI đóng vai trò phản biện độc lập giúp xếp hạng task vào Ma trận Impact/Effort, nhóm sẽ đạt thỏa thuận phân công nhanh hơn 3 lần.

**Quick gut:**  
Rule (Sử dụng Framework Impact/Effort ép vào Prompt).

### Draft current workflow

```text

CURRENT STATE — Tốn 90 phút/buổi họp
[Liệt kê Task] 
─► [Họp tranh luận cảm tính] ─◄ Bottleneck: Đùn đẩy, đoán sai Effort 
─► [Phân công gượng ép] 
─► [Trễ deadline / Cãi nhau]

```

### Draft future workflow

```text

FUTURE STATE — Ngắn hơn (< 15 phút)
[Input Task List] 
─► [AI Map Impact/Effort] 
─► [AI Đề xuất Task-Member] ──◄ Human Boundary: Thảo luận & Chốt 
─► [Chốt phân công]
                               
FALLBACK: Nhóm không đồng ý phân chia của AI ─► Leader điều chỉnh Ma trận thủ công & Biểu quyết nhóm

```