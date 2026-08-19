# NB2 — Hybrid Search RRF Outputs

## NB2 Execution Results

### Precision@10 by Mode
```
Quality — Precision@10 (% of top-10 in matching topic)
  Keyword (BM25)   :  77.8%
  Semantic (vector):  73.2%
  Hybrid  (RRF=60) :  78.6%   <- wins overall

Quality by query type:
  type           n       kw     sem     hyb
  exact         15   96.7%  88.7%  96.7%
  paraphrase    15   33.3%  24.0%  32.0%
  mixed         20   97.0%  98.5% 100.0%
```

### Key Findings
- Hybrid wins overall by +0.8pp vs keyword, +5.4pp vs semantic
- Hybrid wins 100% on mixed queries (keyword + semantic intent)
- Keyword wins on exact queries (96.7%) due to exact keyword matching
- Semantic struggles on paraphrase queries (24.0%) with bge-small model

### Deliverable Checklist
- [x] Table with 3 modes (kw/sem/hyb)
- [x] Hybrid > both other modes overall
- [x] Breakdown by query type (exact/paraphrase/mixed)
