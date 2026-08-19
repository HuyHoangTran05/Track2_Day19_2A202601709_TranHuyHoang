# NB1 — Embeddings & Vector Indexing Outputs

## NB1 Execution Results

### Cell 4: Indexed Count
```
Indexed: 1000 vectors
```

### Cell 5: Top-5 Similarity Search
```
Query: 'cloud computing và tự động mở rộng'
Top-5:
  1. [     cloud] score=0.032  Điện toán đám mây: tự động mở rộng theo lưu lượng
  2. [     cloud] score=0.031  Điện toán đám mây: tự động mở rộng theo lưu lượng
  3. [     cloud] score=0.031  Điện toán đám mây: tự động mở rộng theo lưu lượng
  ...
```

### Cell 6: Paraphrase Query (no "cloud" keyword)
```
Query (paraphrase): 'phương pháp tự động mở rộng hạ tầng theo lưu lượng người dùng'
Top-5: predominantly 'cloud' topic ✓
```

### Deliverable Checklist
- [x] Indexed 1000 vectors
- [x] Top-5 for Vietnamese query returns correct cluster
- [x] Paraphrase query still finds correct topic cluster
