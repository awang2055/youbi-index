# Youbi 1000 Scoring System

## Philosophy

Youbi 1000 ranks creators based on:
- real engagement
- real fan relationships
- sustainable growth
- trust and credibility

NOT:
- vanity followers
- inflated metrics

---

## Score Components

Total Score = weighted sum

### 1. Community Score (30%)
Derived from Youbi internal metrics:
- response rate
- fan satisfaction
- complaint rate
- contribution/helpfulness

### 2. Cross-Platform Engagement (20%)
From:
- likes
- comments
- shares
- engagement rate

Focus:
- recent content (7–30 days)

### 3. Active Fan Growth (20%)
- follower growth
- subscriber growth
- normalized across size

### 4. Paid Messages (15%)
- volume
- unique senders
- recency

### 5. Gifts & Tips (15%)
- total value
- distribution
- repeat support

---

## Normalization

All metrics must be normalized:
- scale to comparable ranges
- avoid domination by large accounts
- cap outliers

Example:
normalized = log(metric + 1) / max_log_value

---

## Fraud Detection

### Signals
- abnormal spikes
- inconsistent engagement
- bot-like patterns

### Output
- fraud_score (0–1)
- penalty_factor

### Application
final_score = score_total * (1 - penalty_factor)

---

## Tier Classification

Top 10 → Diamond
Top 100 → Gold
Top 500 → Silver
Top 1000 → Bronze

---

## Edge Cases

### New creators
- boost growth weight
- reduce historical dependence

### Missing data
- reduce weight proportionally
- do not assign zero blindly

### Multi-platform imbalance
- normalize per platform

---

## Example

Small creator:
- 50K followers
- high engagement
- strong growth

Large creator:
- 5M followers
- low engagement

Result:
→ small creator ranks higher

---

## Configurable Weights

Stored in scoring_profiles:

{
  "community": 0.30,
  "engagement": 0.20,
  "growth": 0.20,
  "messages": 0.15,
  "gifts": 0.15
}

---

## Output Requirements

Each ranking result must include:
- total score
- component scores
- fraud penalty
- explanation

---

## Transparency Commitment

- No pay-for-placement
- Fully explainable rankings
- Continuous monitoring
