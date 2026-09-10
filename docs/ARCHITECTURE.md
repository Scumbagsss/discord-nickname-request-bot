# Architecture

## Purpose

Moderated Discord nickname-change request system with automatic role-prefix preservation.

## Boundary

The public repository documents only the system boundary. The production edition contains private implementation details, persistence schemas, operational thresholds, adapters, credentials and deployment configuration.

## Components

- **Discord interaction layer** — buttons, forms, commands and/or event listeners.
- **Domain service layer** — validates state and executes the project-specific workflow.
- **Persistence/integration layer** — private production storage and external adapters.
- **Observability layer** — staff logs, error handling and operational feedback.

## Workflow

1. User submits requested nickname
2. Validate request
3. Staff reviews
4. Apply or reject change
5. Preserve managed prefix rules

## Why the implementation is private

The production code is a commercial/private implementation. The portfolio edition intentionally prevents direct deployment while still documenting the engineering scope.
