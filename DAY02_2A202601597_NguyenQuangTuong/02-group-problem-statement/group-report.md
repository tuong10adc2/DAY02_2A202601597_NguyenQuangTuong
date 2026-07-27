# Group Report — Day 02

## Thành viên nhóm


| STT | Họ và tên          | Mã học viên | Vai trò trong nhóm                  |
| --- | --------------------- | -------------- | ------------------------------------- |
| 1   | Phạm Đình Minh     | 2A202601979    | Nhóm trưởng / Điều phối         |
| 2   | Phạm Đức Trung     | 2A202601253    | Phân tích Problem và Workflow     |
| 3   | Đồng Đại Huy      | 2A202601901    | Validation và Thu thập Evidence    |
| 4   | Nguyễn Đình Bình  | 2A202601091    | Research và Đánh giá giải pháp |
| 5   | Nguyễn Quang Tường | 2A202601597    | Tổng hợp và Documentation         |

## Group Convergence

Nhóm gồm 5 thành viên. Mỗi thành viên đã thực hiện Individual Problem Scan và chọn Top 3 problems. Sau khi chia sẻ các Top 3, nhóm gom các problem có bottleneck/pattern tương đồng thành các cluster sau.

### Bảng 1 — Gom nhóm các problem


| Cluster                         | Candidate examples                                                                                                                        | Pattern chung                                                                                                                                                                                                                       |
| ------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Knowledge Discovery & Retrieval | Dataset discovery, Video/slide search, Tìm lại decision cũ, Technical document summarization, Tra cứu câu hỏi/thông tin trường | Người dùng cần tìm đúng thông tin từ các nguồn lớn, dài hoặc phân tán, sau đó đánh giá relevance, context và freshness trước khi có thể sử dụng thông tin đó.                                        |
| Technical Problem Solving       | Baseline reproduction, Debugging, Git conflict, API Spec extraction                                                                      | Developer/researcher phải hiểu technical context, xác định nguyên nhân hoặc thông tin cần thiết, thực hiện hành động kỹ thuật và kiểm tra kết quả; trong một số trường hợp phải lặp lại nhiều vòng. |
| Team Coordination               | Action-item extraction, Task prioritization                                                                                               | Thông tin từ trao đổi hoặc các task ban đầu chưa có cấu trúc rõ ràng và cần được chuyển thành action item, priority, owner hoặc deadline để team có thể hành động nhất quán.                         |
| Rules, Procedures & Compliance  | Rubric checking, Course registration, Administrative procedures                                                                           | Người dùng phải đối chiếu nhiều rule, constraint hoặc procedure để xác định một lựa chọn, output hoặc hành động có hợp lệ, đầy đủ và phù hợp hay không.                                             |
| Expensive Repetitive Execution  | Multi-model/method experiments                                                                                                            | Công việc bắt buộc phải thực thi lặp lại nhiều lần, trong khi mỗi lần chạy có runtime và chi phí lớn; bottleneck chủ yếu nằm ở execution/compute resources hơn là reasoning.                                 |

### Bảng 2 — Shortlist và Score

Sau khi cluster, nhóm shortlist đúng 3 candidate problems sau:

1. **Tra cứu Video + Slide**
2. **Dataset Discovery**
3. **Baseline Reproduction**


| Candidate              | Actor rõ | Workflow rõ | Pain có evidence | Impact đo được | Làm trong lab | So sánh R/W/A được | Nhóm hiểu domain |     Tổng |
| ---------------------- | --------: | -----------: | ----------------: | -----------------: | -------------: | ---------------------: | -----------------: | --------: |
| Tra cứu Video + Slide |         5 |            5 |                 5 |                  5 |              5 |                      4 |                  5 | **34/35** |
| Dataset Discovery      |         5 |            5 |                 4 |                  4 |              5 |                      5 |                  5 | **33/35** |
| Baseline Reproduction  |         5 |            5 |                 3 |                  4 |              3 |                      5 |                  4 | **29/35** |

**Candidate được chọn:** Tra cứu Video + Slide

**Lý do:** Candidate này có actor và workflow rõ, pain có evidence thực tế, impact có thể đo được, scope phù hợp để triển khai trong lab và nhóm có đủ hiểu biết về domain. So với hai candidate còn lại, bài toán này cân bằng tốt nhất giữa giá trị thực tế, khả năng đo lường và tính khả thi khi xây dựng MVP.

## Quick validation

Problem ban đầu:

> Sinh viên CNTT mất khoảng 35–45 phút để tua video bài giảng dài khoảng 2 tiếng và lướt hàng chục trang slide chỉ để tìm lại một đoạn hướng dẫn, code mẫu hoặc cách fix lỗi cụ thể.

Mục tiêu của validation là kiểm tra xem pain này có thực sự xuất hiện ở nhiều sinh viên hay chỉ là trải nghiệm cá nhân, đồng thời xác định bottleneck chính nằm ở bước nào: tìm video, tua video, nghe thử nhiều đoạn, tìm slide hay đối chiếu giữa video và slide.

Nhóm thực hiện quick interview với một số sinh viên CNTT thường xuyên sử dụng video ghi lại bài giảng và slide để làm bài tập hoặc đồ án.

Các câu hỏi validation:

1. Lần gần nhất bạn phải tìm lại một nội dung cụ thể trong video bài giảng là khi nào?
2. Bạn thường mất bao lâu để tìm đúng đoạn?
3. Bạn thường tìm bằng cách tua video, xem transcript, lướt slide hay hỏi người khác?
4. Bước nào khiến bạn mất nhiều thời gian nhất?
5. Bạn có từng tìm được đúng video nhưng vẫn mất nhiều thời gian xác định chính xác đoạn cần xem không?
6. Nếu có hệ thống cho phép nhập câu hỏi và trả về timestamp cùng trang slide liên quan, bạn có sử dụng không?


| Nguồn                    | Số người / số mẫu | Tín hiệu xác nhận                                                                                                                                                | Tín hiệu phản bác                                                                | Nhóm sửa problem thế nào                                                                                                                                            |
| ------------------------- | ---------------------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Quick interview           |           4 sinh viên | `3/4 từng mất nhiều thời gian tua video và lướt slide để tìm lại một nội dung cụ thể; bước khó nhất là xác định đúng đoạn video cần xem` | `1/4 dùng ghi chú nên ít khi phải xem lại video`                               | `Thu hẹp actor vào sinh viên thường xuyên sử dụng video bài giảng; xác định bottleneck chính là tìm đúng đoạn nội dung thay vì thiếu tài liệu` |
| Mini poll sinh viên CNTT |           6 sinh viên | `5/6 cho rằng tính năng nhập câu hỏi sẽ giúp giảm đáng kể thời gian tra cứu`                                                                           | `1/6 cho rằng transcript/keyword search có thể đã đủ cho nhu cầu của mình` | Giữ keyword search làm baseline và kiểm chứng Semantic Retrieval có thực sự cải thiện thời gian/độ chính xác trước khi tăng AI complexity           |

Insight cần kiểm chứng:

```text
Pain không nằm ở việc sinh viên không có tài liệu.

Video và slide đã tồn tại, nhưng nội dung cần tìm nằm bên trong
một lượng lớn dữ liệu khó tra cứu.

Bottleneck chính có khả năng nằm ở việc:
"Tìm chính xác đoạn video và trang slide chứa nội dung phù hợp
với câu hỏi của sinh viên."
```

## Research giải pháp hiện có

Nhóm nghiên cứu các giải pháp hiện tại để kiểm tra xem problem đã được giải quyết đến đâu và xác định phần nào vẫn còn khoảng trống.

## YouTube Transcript

YouTube hỗ trợ xem transcript đầy đủ đối với video có captions. Người dùng có thể click vào một dòng trong transcript để nhảy trực tiếp tới thời điểm tương ứng trong video.

Điều này cho thấy transcript kết hợp timestamp đã là một pattern thực tế để giúp người dùng tránh phải tua toàn bộ video.

Nguồn chính thức:

https://support.google.com/youtube/answer/15930243


| Thành phần                 | Nội dung                                                                                                                             |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Họ giải quyết phần nào? | Chuyển nội dung lời nói trong video thành transcript và cho phép người dùng nhảy tới timestamp tương ứng               |
| Điểm mạnh                 | Đơn giản; transcript gắn với video; người dùng có thể quay lại nguồn gốc ngay                                            |
| Khoảng trống / rủi ro     | Người dùng vẫn cần biết hoặc đoán đúng từ khóa; transcript không tự liên kết đầy đủ với slide bên ngoài video |
| Bài học cho nhóm          | Timestamp phải được giữ làm metadata quan trọng và mọi kết quả tìm kiếm nên dẫn người dùng trở lại nguồn gốc    |

YouTube phù hợp làm một baseline cho bài toán:

```text
Transcript
→ Keyword Search
→ Timestamp
```

Tuy nhiên, nếu sinh viên hỏi bằng cách diễn đạt khác với từ được nói trong video thì keyword search có thể không đủ.

Ví dụ:

```text
Sinh viên hỏi:
"Tại sao container không kết nối được database?"

Trong video giảng viên nói:
"Các service trong Docker Compose phải nằm cùng network."
```

Hai đoạn có liên quan về mặt ý nghĩa nhưng có thể không chứa cùng keyword.

## Panopto Smart Search

Panopto là giải pháp gần với problem của nhóm nhất.

Theo tài liệu chính thức của Panopto, Smart Search index:

* spoken words trong video;
* on-screen text;
* slide;
* và trả kết quả ở mức timestamp.

Panopto sử dụng ASR để xử lý lời nói và OCR để nhận dạng text xuất hiện trên màn hình.

Nguồn chính thức:

https://www.panopto.com/features/video-search/

https://www.panopto.com/capabilities/ai-capabilities/

Panopto mô tả khả năng tìm kiếm trực tiếp tới "exact moment" trong recording bằng cách index spoken words, text xuất hiện trên màn hình và slide.


| Thành phần                 | Nội dung                                                                                                       |
| ---------------------------- | --------------------------------------------------------------------------------------------------------------- |
| Họ giải quyết phần nào? | Search nội dung bên trong video dựa trên transcript, text trên màn hình và slide                        |
| Điểm mạnh                 | Index nhiều loại dữ liệu; trả kết quả gắn timestamp; giảm nhu cầu tua video                           |
| Khoảng trống / rủi ro     | Là platform lớn; scope rộng hơn nhu cầu MVP của nhóm; chất lượng search phụ thuộc transcription/OCR |
| Bài học cho nhóm          | Không nên chỉ index transcript. Slide và metadata thời gian cũng nên được đưa vào retrieval        |

Pattern quan trọng rút ra:

```text
Video
→ ASR
→ Transcript + timestamp

Screen/Slide
→ OCR / slide indexing

→ Search Index
→ Query
→ Timestamp-level result
```

Đây là bằng chứng khá mạnh rằng technical direction của nhóm là khả thi.

## Google NotebookLM

NotebookLM cho phép người dùng thêm nhiều loại source, bao gồm:

* PDF;
* PowerPoint;
* Google Slides;
* audio;
* YouTube URL;
* website;
* text.

Sau đó người dùng có thể đặt câu hỏi dựa trên các source đã cung cấp.

Đối với YouTube, Google nêu rõ rằng NotebookLM import **text transcript** của video làm source chứ không import toàn bộ visual content của video. Audio upload cũng được transcribe thành text để sử dụng làm source.

Nguồn chính thức:

https://support.google.com/notebooklm/answer/16215270


| Thành phần                 | Nội dung                                                                                                                                  |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Họ giải quyết phần nào? | Semantic Q&A trên nhiều nguồn như PDF, slide, audio và YouTube transcript                                                             |
| Điểm mạnh                 | Có thể hỏi bằng ngôn ngữ tự nhiên thay vì chỉ keyword; hỗ trợ nhiều source                                                    |
| Khoảng trống / rủi ro     | YouTube source chủ yếu dựa trên transcript text; không tập trung vào việc trả chính xác timestamp + slide page                  |
| Bài học cho nhóm          | Semantic Q&A trên nhiều source là khả thi nhưng nhóm nên giữ provenance cụ thể hơn: đoạn transcript, timestamp và slide page |

## Research tổng hợp


| Nguồn / tool / case | Link                                                  | Họ giải quyết phần nào?                    | Điểm mạnh                                                  | Khoảng trống / rủi ro                                                     | Bài học cho nhóm                                                                    |
| -------------------- | ----------------------------------------------------- | ----------------------------------------------- | ------------------------------------------------------------- | ---------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| YouTube Transcript   | https://support.google.com/youtube/answer/15930243    | Transcript + jump tới timestamp                | Đơn giản, source rõ                                       | Chủ yếu transcript/keyword; không liên kết tốt với slide ngoài video | Timestamp phải được giữ làm metadata                                             |
| Panopto Smart Search | https://www.panopto.com/features/video-search/        | ASR + OCR + slide indexing + video search       | Tìm cả spoken word, on-screen text và slide; có timestamp | Platform lớn, phụ thuộc ASR/OCR                                           | Index nhiều modality và trả source position                                         |
| Google NotebookLM    | https://support.google.com/notebooklm/answer/16215270 | Q&A trên PDF, slide, audio, YouTube transcript | Semantic Q&A đa nguồn                                       | YouTube chủ yếu import transcript; không tối ưu cho timestamp retrieval | Semantic retrieval có thể tốt hơn keyword search nhưng phải giữ citation/source |

## Research takeaway

Không cần build một Agent tự lập kế hoạch phức tạp. Hướng hợp lý hơn là Workflow: dùng ASR/OCR để xử lý video và slide, semantic search để tìm nội dung liên quan, rồi trả timestamp + slide page để sinh viên kiểm tra nguồn gốc.

## Workflow Before / After

File nhóm nộp kèm: group_workflow.jpg

Nội dung workflow:

### Current State

Quy trình hiện tại gồm 5 bước, tổng thời gian ước tính khoảng **42 phút**:

```text
Mở video 2 tiếng & Slide (2')
→ Tua lướt thanh timeline (10')
→ Bấm nghe thử vô định (15') ← BOTTLENECK
→ Lướt 50 trang Slide đối chiếu (10')
→ Gõ lại code mẫu (5')
```

### Future State

Sau khi áp dụng AI-assisted retrieval, quy trình kỳ vọng giảm xuống khoảng **6 phút**:

<pre class="overflow-visible! px-0!" data-start="538" data-end="757"><div class="relative w-full mt-4 mb-1"><div class=""><div class="contents"><div class="relative"><div class="h-full min-h-0 min-w-0"><div class="h-full min-h-0 min-w-0"><div class="border border-token-border-light border-radius-3xl corner-superellipse/1.1 rounded-3xl"><div class="h-full w-full border-radius-3xl bg-(--code-block-surface) corner-superellipse/1.1 overflow-clip rounded-3xl [--code-block-surface:var(--bg-elevated-secondary)] dark:[--code-block-surface:var(--composer-surface-primary)] lxnfua_clipPathFallback"><div class="pointer-events-none absolute end-1.5 top-1 z-2 md:end-2 md:top-1"></div><div class="relative"><div class="pe-11 pt-3"><div class="relative z-0 flex max-w-full"><div id="code-block-viewer" dir="ltr" class="q9tKkq_viewer cm-editor z-10 light:cm-light dark:cm-light flex h-full w-full flex-col items-stretch ͼs ͼ16"><div class="cm-scroller"><pre class="cm-content q9tKkq_readonly m-0"><code><span>Gõ từ khóa / câu hỏi cần tìm (1')
→ AI tìm kiếm trong transcript + slide
→ Trả Timestamp + Trang Slide (1')
→ Sinh viên xem đúng đoạn video cần thiết (3') ← HUMAN BOUNDARY
→ Áp dụng code mẫu vào bài làm (1')</span></code></pre></div></div></div></div></div></div></div></div></div></div></div></div></div></pre>

### Fallback

```text
Confidence thấp → Trả Top-K gần nhất để sinh viên tự kiểm tra
Semantic search lỗi → Transcript/slide keyword search
```

### Bottleneck mới

Từ **35–45 phút manual search** chuyển thành **review 1–3 kết quả và kiểm tra nguồn gốc**. Đây là bước human quality control cần thiết.

## Before / After Impact


| Metric                          |                    Trước |                         Sau kỳ vọng | Ghi chú                 |
| ------------------------------- | -------------------------: | ------------------------------------: | ------------------------ |
| Tổng thời gian tìm nội dung |               35–45 phút |                              <5 phút | Target chính            |
| Tua/nghe video thủ công       |                  ~25 phút |      Chỉ xem đoạn được retrieve | Giảm search effort      |
| Lướt slide thủ công         |                  ~10 phút | Mở trực tiếp slide/page liên quan | Giảm manual scanning    |
| Kiểu query                     |      Keyword/phỏng đoán |       Câu hỏi ngôn ngữ tự nhiên | Semantic retrieval       |
| Output                          |     Người dùng tự tìm |        Top-K + timestamp + slide page | Có provenance           |
| Human verification              |      Xuyên suốt workflow |                  Chỉ ở bước cuối | Human boundary           |
| Risk mới                       | Không có retrieval error |        ASR/OCR/retrieval có thể sai | Cần source verification |

## Problem Statement v0


| Field              | Nội dung                                                                                                                                              |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Actor**          | Sinh viên CNTT hoặc thực tập sinh lập trình cần tra cứu lại kiến thức, code mẫu hoặc hướng dẫn trong video bài giảng và slide.      |
| **Workflow**       | Mở video/slide → tua video → nghe thử → lướt slide → đối chiếu → sử dụng nội dung.                                                      |
| **Bottleneck**     | Sinh viên không thể truy vấn trực tiếp theo nội dung cần tìm nên phải tua video và lướt slide thủ công để xác định đúng đoạn. |
| **Impact**         | Một lần tìm kiếm mất khoảng 35–45 phút; nếu xảy ra 3–4 lần/tuần có thể tiêu tốn hơn 2 giờ mỗi tuần.                               |
| **Success Metric** | Giảm thời gian tìm kiếm xuống dưới 5 phút và trả được timestamp cùng slide/page liên quan.                                              |
| **Boundary**       | Hệ thống không thay video/slide gốc làm nguồn sự thật; sinh viên vẫn phải kiểm tra nội dung gốc trước khi sử dụng.                   |

## Rule / Workflow / Agent


| Mức              | Phương án                                                                              | Khi nào đủ                                                             | Rủi ro                                                                             | Chọn?              |
| ----------------- | ----------------------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ------------------- |
| **Rule / Search** | Transcript + keyword search + slide keyword search                                        | Đủ nếu người dùng nhớ đúng keyword xuất hiện trong bài giảng | Không xử lý tốt synonym, paraphrase và câu hỏi diễn đạt khác lời giảng | Dùng làm baseline |
| **Workflow**      | ASR/OCR → chunk → index → semantic retrieval → rank → timestamp/page → human review | Workflow có các bước cố định và AI chỉ cần hỗ trợ retrieval   | ASR/OCR/retrieval có thể sai                                                      | **Chọn**           |
| **Agent**         | Agent tự quyết định search nguồn nào, gọi tool nào, search tiếp hay dừng        | Chỉ cần khi task có nhiều nhánh động và cần tự lập kế hoạch  | Over-engineering, latency, khó kiểm soát                                         | Chưa chọn         |

## Mức chọn

```text
Workflow.
```

Vì sao:

* Transcript và slide có thể xử lý/index bằng các bước cố định.
* Semantic retrieval cần AI để hiểu các cách diễn đạt khác nhau.
* Sinh viên vẫn mở timestamp/slide gốc để kiểm tra nên risk kiểm soát được.
* Chưa cần Agent vì pipeline retrieval không cần tự lập kế hoạch động.

## Problem Statement v1


| Field                                 | Nội dung                                                                                                                                                                                      |
| ------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Actor**                             | Sinh viên CNTT cần tìm lại một kiến thức, code mẫu hoặc hướng dẫn cụ thể trong video bài giảng dài và slide tương ứng khi đang làm bài tập hoặc đồ án.            |
| **Workflow**                          | Hiện tại: mở video/slide → tua/nghe thử → lướt slide → đối chiếu → sử dụng. Future: ingest → ASR/OCR → index → semantic retrieval → timestamp/page → student verification. |
| **Bottleneck**                        | Nội dung cần thiết đã tồn tại nhưng khó truy xuất theo semantic intent; người học phải tự xác định vị trí nội dung trong video và slide.                                 |
| **Impact**                            | Một lần tìm kiếm mất khoảng 35–45 phút; với 3–4 lần mỗi tuần có thể tiêu tốn hơn 2 giờ. Baseline chung cần được validation thêm với các sinh viên khác.            |
| **Success Metric**                    | Giảm retrieval time xuống dưới 5 phút; ground-truth đoạn cần tìm xuất hiện trong Top-K kết quả với tỷ lệ đủ cao; kết quả phải có timestamp/slide page.                   |
| **Boundary**                          | Hệ thống không tự sửa/chạy code và không thay video/slide gốc làm nguồn sự thật. Người dùng phải kiểm tra source trước khi áp dụng.                                      |
| **AI intervention point**             | Sau khi video và slide được ingest, AI hỗ trợ matching semantic giữa câu hỏi với transcript/slide chunks và ranking candidate.                                                      |
| **Mức chọn**                        | Workflow: ASR/OCR → indexing → semantic retrieval → ranking → timestamp/page → human review.                                                                                              |
| **Rủi ro & người thật kiểm tra** | ASR có thể nhận sai thuật ngữ kỹ thuật, OCR có thể sai code/text và retrieval có thể trả sai đoạn. Sinh viên kiểm tra video/slide gốc trước khi sử dụng.                 |


## Final decision

Decision:

```text
Go với scope nhỏ.
```

Pilot nhỏ nhất:

* Dùng 1 video bài giảng khoảng 2 giờ và bộ slide tương ứng.
* Tạo 15–20 câu hỏi có ground-truth timestamp và slide page.
* So sánh Manual Search → Keyword Search → Semantic Retrieval.
* Đo search time, Recall@K và mức độ chính xác của timestamp/page.
* Sinh viên review kết quả và mở nguồn gốc để xác nhận.

Exit / rollback:

* Nếu Keyword Search ≈ Semantic Retrieval, giữ transcript + keyword search, không tăng AI complexity.
* Nếu ASR/OCR sai nhiều, ưu tiên cải thiện preprocessing trước khi thêm AI.
* Nếu người dùng vẫn phải search/tua video nhiều lần, cải thiện retrieval hoặc chọn `Not Yet`.
* Không nâng thành Agent nếu Workflow đã đạt target.

Decision rationale:

* Problem, workflow và bottleneck rõ; target giảm thời gian tìm từ 35–45 phút xuống <5 phút.
* Có non-AI baseline để so sánh.
* AI chỉ can thiệp ở semantic retrieval/ranking, không ôm toàn bộ workflow.
* Timestamp + slide page giúp sinh viên kiểm tra lại nguồn gốc.
* Workflow tuyến tính và có human review rõ nên chưa cần Agent.

```
