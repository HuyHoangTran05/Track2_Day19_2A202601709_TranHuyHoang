# NB7 — Semantic Cache Outputs

## NB7 Execution Results

### Threshold Sweep Analysis
```
Threshold sweep:
   threshold   savings     wrong
        0.75       80%       0
        0.85       60%       0
        0.95       20%       0
        0.99        0%       0
```

### Key Findings
- **Lower threshold** = higher savings (more hits) but risk of wrong answers
- **Higher threshold** = safer but fewer cache hits
- Sweet spot depends on tolerance for incorrect answers

### Cross-Tenant Security Demo
```
With namespaced=True (secure):
  tenant_a sees: answer_A
  tenant_b sees: answer_B
  No leak: True ✓

With namespaced=False (INSECURE - for demo only):
  tenant_a sees: answer_B  <- LEAKED!
  tenant_b sees: answer_B
  No leak: False ✗
```

### Security Implications
- **namespaced=True** is REQUIRED for production
- Cross-tenant cache leak is a **security incident**, not a caching bug
- Different tenants may have same questions but different authorized answers

### Deliverable Checklist
- [x] Threshold sweep showing savings vs accuracy tradeoff
- [x] Cross-tenant leak demo (with namespaced=False)
- [x] Security fix demonstration (namespaced=True)
