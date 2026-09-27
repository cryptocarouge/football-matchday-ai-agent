# Case Study — Football Matchday AI Agent

## Problem

A live football match is a stream of changing state, not a sequence of independent API responses. Multiple providers can disagree, events can arrive late or twice, and automated publishing must not repeat the same goal or react to stale information.

## Architecture decision

The system separates two parallel information paths:

1. **News radar** — collects and merges trusted news sources.
2. **Live match data** — polls multiple sports-data providers and normalizes events.

Both paths feed controlled downstream logic rather than publishing directly.

## Persistent match state

A dedicated match-state machine tracks what the system already knows: match phase, score changes and previously processed events.

This allows the workflow to reason about transitions instead of treating every poll as a new event.

## Multi-source validation and deduplication

Live providers are normalized into a common representation before they influence state. Event deduplication prevents repeated publishing when the same event appears in consecutive polls or from multiple sources.

## Editorial layer after state

The editorial/emotion layer only runs after the workflow has determined that a meaningful state transition occurred.

Media selection, publication and post verification are separate stages, keeping content generation away from the logic that decides whether an event is real and new.

## What remains private

The public repository excludes provider credentials, OpenAI keys, X/Telegram credentials, private prompts, account-specific controls and the production workflow.

## Takeaway

The project is an example of **event-driven automation with explicit state**: normalize noisy sources, detect transitions, deduplicate, then generate and publish.
