# Football Matchday AI Agent

An event-driven football intelligence and publishing system built with n8n.

The private project was created around matchday automation for a football fan account. The public version focuses on the reusable engineering: live-state handling, multi-source validation, deduplication, editorial generation and publication control.

## What it demonstrates

- Fixture discovery across multiple competitions
- Matchday scheduling
- Live match polling
- Multi-source live-event normalization
- Persistent match-state machine
- Event deduplication
- News radar and source merging
- Editorial review gates
- Context-aware reaction generation
- Media selection and validation
- X publishing
- Telegram control and review flows
- Health checks for external data sources

## Architecture

```text
Fixtures / Schedules
        |
        v
   Match Detection
        |
        +-------------------+
        |                   |
        v                   v
   News Radar          Live Match Data
        |                   |
 Multi-source Merge    Multi-source Merge
        |                   |
 Dedup / Review Gate   Normalize Events
        |                   |
        +---------+---------+
                  |
                  v
          Match State Machine
                  |
                  v
          Editorial / Emotion
                  |
                  v
          Media Validation
                  |
                  v
             Publish
                  |
                  v
          Verify + Persist
```

## Why a state machine matters

A live match is not just a stream of isolated events. The agent maintains state so that goals, score changes, match phases and previously handled events can influence what happens next without reposting the same event.

## Security boundary

The public repository excludes:

- OpenAI keys
- X OAuth credentials
- Telegram credentials/chat IDs
- Account-specific prompts
- Private publishing controls
- Production workflow JSON

## Disclaimer

Independent fan-automation engineering project. Not affiliated with FC Porto, any football club, league, broadcaster or sports-data provider.
