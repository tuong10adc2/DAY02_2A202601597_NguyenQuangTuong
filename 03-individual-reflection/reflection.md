# 03 — Individual Reflection Example

## Đóng góp của Tường trong nhóm

| Hoạt động | Minh đã làm gì? | Kết quả |
|---|---|---|
| Scan cá nhân | Đưa ra 10 problems | Nhóm có nguồn candidate đa dạng về tài liệu và xử lý kỹ thuật |
| Pitch | Pitch bài toán tóm tắt tài liệu/slide và phân tích rủi ro khi đọc tài liệu dài | Bài được vào shortlist |
| Challenge |Đặt câu hỏi về tính chính xác của dữ liệu trích xuất và cách người dùng xác minh kết quả| Nhóm định hình rõ ràng ranh giới Human Boundary |
| Workflow | Đóng góp ý kiến hoàn thiện sơ đồ Before/After và đề xuất kịch bản Fallback khi AI tra cứu sai | Nhóm có quy trình workflow hoàn chỉnh và thực tế để đưa vào báo cáo |
| Research | Phân tích giải pháp của Panopto Smart Search, YouTube Transcript và Google NotebookLM | Nhóm rút ra bài học cốt lõi: Cần lưu Metadata Timestamp và Slide Page làm nguồn đối chiếu |
| Rule / Workflow / Agent | Phản biện việc phức tạp hóa hệ thống và đề xuất dừng ở mức Workflow | Nhóm chốt được quyết định Go với scope nhỏ thay vì làm Agent rườm rà |

## Bảng dùng AI trong reflection

| Phase | Tôi dùng AI để làm gì? | AI hữu ích ở đâu? | AI sai/hời hợt ở đâu? | Tôi sửa gì |
|---|---|---|---|---|
| Scan | Nhờ AI phân loại 10 bài toán cá nhân theo các lăng kính | Giúp sắp xếp bảng scan trực quan và nhanh chóng |Một số bài toán AI đưa ra mang tính lý thuyết, thiếu tính thực tế | Lọc bỏ ý chung chung, giữ lại các vấn đề sát với trải nghiệm làm đồ án IT|
| Workflow | Dùng AI để chuyển luồng tư duy thành dạng sơ đồ ASCII / Mermaid | Xuất nhanh cấu trúc Before/After mà không mất công vẽ tay | AI chỉ vẽ luồng lý tưởng (Happy Path) và bỏ qua kịch bản khi AI trả kết quả sai | Tự bổ sung thêm bước kiểm tra của con người và nhánh xử lý Fallback |
| Research | Tóm tắt cơ chế hoạt động của Panopto, NotebookLM| Nhanh chóng tìm ra điểm mạnh và khoảng trống của các công cụ hiện có| AI hay đưa ra các đánh giá cảm tính không kèm bằng chứng thực tế | Tìm lại tài liệu/doc chính thức của hãng để kiểm chứng thông tin trước khi đưa vào |
| Problem Statement | Nhờ AI đóng vai Challenger để phản biện các trường trong Problem Statement v0 | Phát hiện ra metric đo lường chưa rõ ràng và thiếu ranh giới xử lý của AI | AI liên tục đề xuất xây dựng hệ thống Agent tự động hóa quá đà | Ép bài toán quay về mức Workflow đơn giản, tập trung vào khâu Semantic Retrieval |

## Bài học của Tường

- Tự động hóa không có nghĩa là loại bỏ con người; trong các bài toán về tri thức, AI chỉ nên đóng vai trò trợ lý tra cứu (Retrieval) còn con người mới là người quyết định tính đúng sai.

- Một giải pháp tốt là giải pháp giải quyết đúng điểm nghẽn (Bottleneck) bằng kiến trúc đơn giản nhất có thể, thay vì cố gắng áp dụng các mô hình Agent phức tạp khi chưa thực sự cần thiết.

- Thiết kế Workflow thực tế bắt buộc phải tính đến kịch bản thất bại (Fallback) để người dùng luôn có phương án thay thế khi AI đưa ra kết quả không chính xác.

- Nghiên cứu đối thủ (Research) giúp nhóm tránh việc "chế tạo lại bánh xe bò", đồng thời học hỏi được các mô hình xử lý dữ liệu chuẩn từ những sản phẩm đi trước.

Nếu làm lại:

```text
Tôi sẽ đề xuất nhóm xây dựng sẵn một bộ câu hỏi thử nghiệm (15-20 test cases) ngay từ bước Validation để đo lường chính xác hiệu quả của Semantic Retrieval so với Keyword Search trước khi chốt Problem Statement v1.
```

---