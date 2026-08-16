# Evaluation Case: Workflow Integration

## Purpose

Test state ownership, retries, credentials, and partial failure.

## Target

Use a project that receives webhooks and performs multi-step work against at least one third-party API.

## Prompt

```text
系统需要在审批通过后同步到第三方平台。请设计可靠的处理流程，并评审现有代码是否支持重试、取消和故障恢复。
```

## Expected strengths

- Separates approval facts, synchronization commands, jobs, and projections.
- Defines webhook verification and business idempotency.
- Handles unknown external outcomes and reconciliation.
- Gives credentials an owner and prevents leakage.
- Defines cancellation semantics after partial external success.

## Failure signals

- Assumes exactly-once delivery.
- Retries every provider error.
- Stores secrets in workflow payloads.
- Claims atomicity across local and third-party systems.
