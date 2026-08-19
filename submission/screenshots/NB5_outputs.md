# NB5 — Filtered Search Outputs

## NB5 Execution Results

### Recall by Filter Selectivity
```
docs: 1000   vectors: (1000, 384)
payload sample: {'doc_id': 'frontend_074', 'topic': 'frontend', 'tenant': 'globex', 'access': 'public', 'published': '2023-11-04'}

filter               sel%    post    fANN
khong filter        100.0    1.00    1.00
access=internal      23.6    0.20    1.00
tenant=acme          31.9    0.20    1.00
published >= 2026     3.8    0.00    1.00
```

### Over-fetch Analysis
```
  fetch_k   recall        % corpus
       10     0.03              1%
       50     0.27              5%
      200     0.80             20%
      500     1.00             50%
     1000     1.00            100%
     fANN     1.00              1%
```

### Tenant Test
```
tenant=acme      sel= 31.9%  post=0.20  fANN=1.00
tenant=globex    sel= 34.7%  post=0.60  fANN=1.00
tenant=initech   sel= 33.4%  post=0.20  fANN=1.00
```

### Key Finding
- **Post-filter collapses at selectivity ~4%**: Recall drops to 0.00
- **Filtered-ANN maintains recall 1.00 at all selectivity levels**
- No error messages — just silently wrong results
- Need ~50% corpus scan to recover recall via over-fetch

### Deliverable Checklist
- [x] Recall table by selectivity
- [x] Post-filter collapses at ~4% selectivity
- [x] Filtered-ANN maintains 1.00 recall
- [x] Over-fetch ladder analysis