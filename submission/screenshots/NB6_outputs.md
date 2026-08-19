# NB6 — Agentic Retrieval Outputs

## NB6 Execution Results

### Tool Schema
```json
{
  "name": "search_docs",
  "description": "Search the internal Vietnamese technical documentation corpus...",
  "input_schema": {
    "properties": {
      "query": {"type": "string", "description": "One single-intent question."},
      "topic": {"type": "string", "enum": ["cloud", "ai_ml", "security", ...]}
    }
  }
}
```

### Planner Demo (compound question)
```
Question: "tu dong mo rong theo luong luong va can bang tai giua nhieu region"
call 1: {'query': 'tu dong mo rong theo luong luong va can bang tai giua nhieu region', 'top_k': 16, 'topic': 'ai_ml'}
```

### Benchmark Results (same budget: 16 docs total)
```
strategy              recall  balance   calls       ms
single-shot            0.526     0.08     1.0    109.9
agentic (no filter)    0.906     0.93     2.3    194.8
agentic (+filter)      0.823     0.76     2.3    238.3

Delta recall vs single-shot:
  tach cau +0.380
  tach + filter +0.297
```

### Key Findings
- **Agentic (no filter) wins**: +38.0% recall vs single-shot
- **Balance improved dramatically**: 0.93 vs 0.08
- Rule-based planner (no LLM) sufficient for question decomposition
- Agentic costs more calls but within same budget constraint

### Reflection Demo
```
filter quá chặt (since_year=2027): 0 kết quả
filter hợp lý: 8 kết quả
agent phản tỉnh: 2 call → 8 kết quả (sau khi nới filter)
```

### Deliverable Checklist
- [x] Tool schema with enum topic
- [x] Agentic > single-shot on recall AND balance
- [x] Same budget comparison
- [x] Reflection recovers from bad filter