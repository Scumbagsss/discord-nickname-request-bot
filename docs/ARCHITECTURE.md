# Discord Nickname Request Workflow — architecture notes

> This is a **suggested technical boundary for a private-source module**, not a claim that all components are implemented or active in a particular deployment.

## Objective

A nickname change seems simple until it has to preserve group naming conventions, route staff approval and avoid Discord permission failures. The feature-level case study describes that review workflow.

## Conceptual responsibilities

**1. Member application.** Collect a proposed nickname and the user's reason.

**2. Validation.** Validate length, format and any managed prefix expectations.

**3. Staff decision.** Create an identifiable request for staff review.

**4. Nickname adapter.** Record an approve/reject decision with reviewer context.

**5. Outcome / audit.** Attempt the change through an authorized adapter and report its outcome.

## Review risks and recommended tests

| Concern | Failure mode | Verification to add |
|---|---|---|
| Concurrent requests | Two requests may race to rename the same member | Define one pending request or explicit supersession |
| Role-prefix overlap | A requested name may already include a managed prefix | Normalize via a shared prefix policy |
| Identity and authority | Approval button visibility is not sufficient security | Re-check staff permissions before applying |
| Discord API failure | Nickname mutation can fail after approval | Preserve decision and record delivery status separately |

## Integration and permissions

The Discord interaction layer should treat its inputs as untrusted. A server-side handler must establish the principal, check authorization for the concrete operation and return user-safe errors. The persistence or external API adapter is separately responsible for safe updates, retries and recovery. The public `src/public_interface.py` is only a surface sketch; **none of these safeguards can be confirmed by running it**.

## Production/public boundary

No real member IDs, credentials, channel IDs, private schemas, moderation rules or live logs should appear in this repository. The architectural context belongs to the wider [DeadCity platform case study](https://github.com/Scumbagsss/BOT). For a separately developed runnable example, see the [ticket workflow backend](https://github.com/Scumbagsss/advanced-discord-ticket-bot).
