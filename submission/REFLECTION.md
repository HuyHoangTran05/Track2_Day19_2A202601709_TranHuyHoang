# Reflection — Lab 19

**Tên:** Huy Hoang Tran
**Cohort:** A20-K1
**Path đã chạy:** lite

---

## Câu hỏi (≤ 200 chữ)

Trên golden set 50 queries, **hybrid thắng trung bình** (78.6%) so với keyword (77.8%) và semantic (73.2%). Tuy nhiên, breakdown theo loại query cho thấy bức tranh phức tạp hơn:

- **Exact queries**: Keyword và hybrid cùng thắng (96.7%) vì BM25 bắt keyword match hoàn hảo.
- **Paraphrase queries**: Semantic thắng (24.0% vs 32.0% hybrid vs 33.3% keyword) — thú vị là hybrid không tốt nhất ở đây vì RRF có thể bị BM25 kéo xuống.
- **Mixed queries**: Hybrid thắng tuyệt đối (100%) — đây là lý do hybrid tổng thể thắng.

**Khi không dùng hybrid:**
1. Query có keyword cụ thể rõ ràng → pure BM25 đủ và nhanh hơn nhiều (P99 ~3ms vs ~120ms).
2. Latency budget cực kỳ thấp → semantic/hybrid quá chậm.
3. Corpus nhỏ, semantic không cần thiết → BM25 đủ.

**Bonus observation:** NB6 cho thấy agentic retrieval (rule-based planner) đánh bại single-shot với recall +38% ở cùng ngân sách 16 docs — chứng minh tách câu hỏi ghép thành nhiều intent là chiến lược quan trọng.

---

## Điều ngạc nhiên nhất khi làm lab này

**Filtered search (NB5):** post-filter sập về recall 0.00 ở selectivity ~4% mà không có error message gì — chỉ là kết quả sai một cách im lặng. Đây là loại bug cực kỳ nguy hiểm trong production vì không ai biết có vấn đề cho đến khi user phàn nàn.

---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [x] Pair work với: Claude Code assistant
