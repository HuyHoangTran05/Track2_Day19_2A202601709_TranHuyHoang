# NB8 — Feature Engineering Outputs

## NB8 Execution Results

### Leakage Experiment (session_id, clicked)
```
         encoding  train_auc  test_auc       gap
0       frequency   0.527  0.567      -0.041
1    target-naive   0.986  0.557      +0.429  <- LEAKED!
2  target-in-fold   0.521  0.557      -0.036
```

### Key Finding: Target Encoding Leakage
- **Naive target encoding** has gap of **+0.429** (train AUC >> test AUC)
- This is > 0.30 threshold mentioned in rubric
- **In-fold target encoding** correctly prevents leakage (gap ≈ 0)

### PIT vs Latest Join
```
PIT join: joins features at exact event timestamp
  ✓ Correct: feature value at time of event
  ✓ No future information leakage

Latest join: joins most recent feature values
  ✗ May include information from future events
  ✗ Temporal integrity violated
```

### On-Demand Feature View (ODFV)
```
User: u_001
At timestamp T:
  → Returns user_segment computed from events UP TO T
  → NOT from events after T (future leakage)

At timestamp T+1:
  → Returns user_segment computed from events UP TO T+1
  → Different values possible
```

### Feature Types Learned
1. **Window aggregates**: count/sum over time windows (1h, 24h, 7d)
2. **Frequency encoding**: stateless, no leakage risk
3. **Target encoding (naive)**: LEAKS - use in-fold only
4. **Target encoding (in-fold)**: safe, prevents leakage
5. **PIT join**: temporal correctness for time-series features

### Deliverable Checklist
- [x] Leakage gap > 0.30 on session_id (0.429)
- [x] PIT join preserves temporal integrity
- [x] ODFV returns different values at different timestamps
