# NB4 — Feast Feature Store Outputs

## NB4 Execution Results

### Cell 2: Parquet Files Generated
```
Wrote 3 Parquet sources to app/feast_repo/data
  item_popularity.parquet  9.7 KB
  query_velocity.parquet  2.3 KB
  user_profile.parquet  2.8 KB
```

### Cell 3: feast apply
```
No project found in the repository. Using project name lab19 defined in feature_store.yaml
Applying changes for project lab19
Created project lab19
Created entity user
Created entity item
Created feature view user_profile_features
Created feature view item_popularity_features
Created feature view query_velocity_features
Created sqlite table lab19_item_popularity_features
Created sqlite table lab19_query_velocity_features
Created sqlite table lab19_user_profile_features
```

### Cell 4: feast materialize-incremental
```
Materializing 3 feature views to 2026-08-19 03:35:33+00:00 into the sqlite online store.
user_profile_features from 2026-07-20 03:35:45+00:00 to 2026-08-19 03:35:33+00:00:
item_popularity_features from 2026-08-18 03:35:45+00:00 to 2026-08-19 03:35:33+00:00:
query_velocity_features from 2026-08-19 02:35:45+00:00 to 2026-08-19 03:35:33+00:00:
```

### Cell 5: Online Lookup
```
Single lookup: 60.41ms (cold start)
{'user_id': 'u_001', 'reading_speed_wpm': 187, 'preferred_language': 'vi',
 'topic_affinity': 'cloud', 'queries_last_hour': 11, 'distinct_topics_24h': 4}
```

### Cell 6: Batch Latency Benchmark
```
Online lookup latency over 100 calls:
  P50 = 0.27ms
  P95 = 0.38ms
  P99 = 0.61ms
PASS — online lookup P99 < 10ms (0.61ms)
```

### Cell 7: PIT Join DataFrame
```
  user_id           event_timestamp  reading_speed_wpm topic_affinity
0   u_003 2026-08-19 03:35:33+00:00                201       database
1   u_002 2026-08-19 02:35:33+00:00                194       security
```

### Deliverable Checklist
- [x] feast apply succeeded (3 feature views)
- [x] materialize completed (3 views to online store)
- [x] online lookup P99 = 0.61ms << 10ms ✓
- [x] PIT join DataFrame created
