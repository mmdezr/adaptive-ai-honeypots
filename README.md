# Adaptive AI Honeypots (Cowrie + ELK + Random Forest + LinUCB)

Adaptive honeypot system for corporate-style threat monitoring using an SSH honeypot (Cowrie),
Elastic Stack for observability, and an AI-driven adaptation layer (state classification + contextual bandit).

## Components
- **Cowrie (SSH honeypot)**: containerized build/runtime profiles.
- **ELK pipeline**: Filebeat + Logstash parsing/enrichment + dashboards.
- **AI layer**:
  - Random Forest: session/state classification
  - LinUCB: decision policy to select the next deception profile

## Repository layout
- `cowrie/` Cowrie container build + runtime examples + profiles
- `elk/` Logstash pipeline, Filebeat config, GeoIP guidance
- `ia/` Python code for training, control and analysis
- `scripts/` helper scripts

## Quick start (high level)
1. Build and run Cowrie (Podman) using `cowrie/build/Containerfile`
2. Deploy ELK pipeline and point Filebeat to Cowrie JSON logs
3. Run the AI controller to adapt profiles based on observed behavior

## GeoIP databases
MaxMind GeoLite2 databases are not included. See `elk/logstash/GeoIP/README.md`.

## Security & ethics
Run only in a controlled environment. Do not expose real production services. Never store secrets in configs.
