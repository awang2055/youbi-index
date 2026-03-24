# AGENTS.md — Youbi 1000 Backend

## Purpose
This repository builds the Youbi 1000 backend: a transparent, engagement-first, anti-gaming creator ranking system.

## Core Principles
1. Depth over breadth: engagement > followers
2. Transparency: every score must be explainable
3. Anti-gaming: detect and penalize manipulation
4. Reproducibility: every ranking run is replayable
5. Historical continuity: never overwrite past data
6. Configurable scoring: no hardcoded weights

## Coding Conventions
- Language: Python (ETL/jobs), SQL (Postgres)
- Style: explicit, readable, production-minded
- Avoid premature abstractions
- Prefer small services over large monolith classes

## Repository Structure
/backend
  /app
    /models
    /services
    /repositories
    /jobs
    /api
    /config
  /migrations
  /scripts
  /tests
/product
  youbi1000_backend.md
  youbi1000_scoring.md
  youbi1000_methodology.md

## Data Rules (MANDATORY)
- Never overwrite historical snapshots
- Append-only for metrics and ranking results
- All timestamps must be UTC
- Every record must be traceable to a source_run_id
- Store raw payloads whenever possible

## Pipeline Rules
- Pipeline must be idempotent
- Partial failures must not stop entire run
- Each stage must log metrics and errors
- Support rerun for same date

## Ranking Rules
- All ranking logic must be configurable
- No hidden adjustments
- All outputs must include score breakdown
- Fraud penalties must be explicit

## Fraud Detection
- Must not silently filter creators
- Always record:
  - fraud_score
  - penalty_applied
  - reason

## Database Practices
- Use proper indexing
- Use foreign keys
- Use unique constraints
- Avoid JSON unless necessary (except raw payloads)

## Migrations
- Every schema change must have migration
- Never modify existing data in-place
- Use additive changes

## Testing
Must include tests for:
- ranking reproducibility
- fraud penalty application
- missing data handling
- multi-platform aggregation

## Documentation
Every major module must include:
- purpose
- inputs
- outputs
- failure modes

## Non-goals
- Do NOT optimize prematurely
- Do NOT build real-time system yet
- Do NOT rely on one platform
