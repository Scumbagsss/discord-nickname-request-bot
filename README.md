# Nickname Request Bot

> **Portfolio showcase — production source is private and this repository is intentionally non-runnable.**

Moderated Discord nickname-change request system with automatic role-prefix preservation.

## What it demonstrates

- Persistent request panel
- Nickname and reason modal
- Staff review channel
- Approve/reject decisions
- Automatic nickname update
- Role-prefix compatibility

## Technology

Python • discord.py • Persistent Views • Role-aware processing

## High-level workflow

1. User submits requested nickname
2. Validate request
3. Staff reviews
4. Apply or reject change
5. Preserve managed prefix rules

## Public interface preview

The public skeleton exposes only the architectural surface:

- `submit_request(...)`
- `validate_nickname(...)`
- `review_request(...)`
- `apply_nickname(...)`

The production implementations behind these methods are withheld. See [`NOTICE.md`](NOTICE.md).

## Repository contents

- `src/public_interface.py` — non-runnable interface skeleton;
- `docs/ARCHITECTURE.md` — high-level design;
- `examples/config.example.jsonc` — sanitized configuration shape;
- `LICENSE` — explicit all-rights-reserved notice.

## Status

Production-tested private project / portfolio edition.
