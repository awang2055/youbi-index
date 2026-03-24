# Youbi 1000 Backend — System Design

## Overview
Youbi 1000 is a weekly updated, credibility-driven creator ranking system.

The backend system must:
- ingest multi-platform data
- normalize metrics
- calculate engagement-first scores
- apply anti-gaming logic
- generate rankings
- preserve full history

---

## System Architecture

### Layers

1. Ingestion Layer
- Fetch data from:
  - Youbi internal
  - TikTok
  - Instagram
  - YouTube
- Store raw payloads
- Track ingestion_runs

2. Normalization Layer
- Convert platform-specific data into unified schema
- Normalize:
  - engagement
  - growth
  - counts
- Assign data_quality_score

3. Identity Layer
- Map accounts to creators
- Track handle changes
- Avoid duplicate creators

4. Aggregation Layer
- Combine multi-platform metrics
- Compute:
  - engagement_rate
  - growth rates
  - activity score

5. Fraud Detection Layer
- Detect anomalies:
  - fake growth
  - bot engagement
  - abnormal patterns
- Output:
  - fraud_score
  - penalty_factor

6. Scoring Layer
- Apply weighted scoring
- Normalize metrics
- Store component scores

7. Ranking Layer
- Generate rank lists:
  - global
  - category
  - country
- Compute rank_change

8. Publishing Layer
- Provide query-ready outputs:
  - leaderboard
  - creator profile
  - trend data

---

## Core Tables

### creators
Master identity

### creator_accounts
Platform accounts

### creator_account_snapshots
Daily metrics

### creator_metrics_daily
Aggregated per creator

### creator_trust_scores
Internal Youbi trust metrics

### ranking_runs
Each weekly computation

### ranking_results
Rank outputs

### creator_rank_history
Historical tracking

### ingestion_runs
Scraping execution logs

---

## Data Flow

1. ingest → raw data
2. normalize → structured metrics
3. resolve identity
4. aggregate metrics
5. detect fraud
6. calculate scores
7. generate ranking
8. store results

---

## Scheduling

- Weekly: Monday 00:00 UTC
- Allow manual rerun
- Allow backfill

---

## Observability

Track:
- ingestion success rate
- missing data %
- anomaly rate
- ranking stability

---

## Failure Handling

- Missing platform data → degrade gracefully
- Failed ingestion → partial ranking allowed
- Extreme anomalies → flagged, not dropped

---

## API Requirements

- get_top_rankings
- get_creator_profile
- get_rank_history
- get_category_rankings
- get_rising_creators

---

## Future Extensions

- Real-time signals
- Fan segmentation
- Creator monetization analytics
- Brand discovery tools
