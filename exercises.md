# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Khi temperature = 0.0, phản hồi ổn định, chính xác và ít thay đổi giữa các lần gọi. Khi temperature = 0.5 hoặc = 1.0, câu trả lời bắt đầu đa dạng hơn. Ở mức 1.5, phản hồi ngẫu nhiên, ít chính xác. 

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ đặt temperature = 0.2 hoặc 0.3. Mức này giúp chatbot trả lời ổn định, chính xác và nhất quán, điều quan trọng trong hỗ trợ khách hàng, đồng thời vẫn giữ được tính đa dạng, linh hoạt trong cách diễn đạt.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Với 10.000 người dùng mỗi ngày, mỗi người thực hiện 3 lần gọi API và mỗi lần ~350 token, tổng số tokens / ngày là: 10000 * 3 * 350 = 10,500,000 (tokens).
Chi phí cho GPT-4o là: (10,500,000 / 1000)*0.010 = 105 ($/ngày)
Chi phí cho GPT-4o-mini là: (10,500,000 / 1000)*0.0006 = 6.30 ($/ngày)
Vậy, GPT-4o đắt hơn khoảng 16.7 lần so với GPT-4o-mini cho workload này

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o phù hợp cho các nhiệm vụ cần lập luận phức tạp, phân tích sâu hoặc chất lượng phản hồi cao, ví dụ như trợ lý lập trình. GPT-4o-mini phù hợp cho các tác vụ đơn giản và quy mô lớn như chatbot FAQ, trả lời câu hỏi cơ bản hoặc xử lý văn bản đơn giản, nơi mà chi phí là yếu tố quan trọng.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất khi phản hồi dài hoặc người dùng cần cảm giác phản hồi ngay lập tức, chẳng hạn như trong chatbot hoặc trợ lý viết nội dung. Việc hiển thị từng phần của câu trả lời giúp giảm cảm giác chờ đợi và tăng trải nghiệm người dùng. Non-streaming thì phù hợp hơn với các tác vụ ngắn hoặc khi ứng dụng cần xử lý toàn bộ phản hồi trước khi hiển thị, chẳng hạn nhưu trong các hệ thống xử lý batch hoặc API backend.


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
