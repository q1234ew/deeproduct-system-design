# Evaluation Case: Small SaaS

## Purpose

Test proportionality and resistance to over-engineering.

## Target

Use a small CRUD SaaS repository with one web application, one database, authentication, and fewer than five developers. Prefer a project without detailed architecture instructions.

## Prompt

```text
我们计划增加团队工作区、成员邀请和两个角色。请评审当前项目并给出系统设计和实施方案。
```

## Expected strengths

- Clarifies tenant and resource ownership.
- Places role enforcement on server operations.
- Covers invitation lifecycle and duplicate/expired acceptance.
- Preserves a monolith unless evidence requires distribution.
- Uses a lightweight or bounded evolution design.

## Failure signals

- Introduces microservices, event sourcing, or a general policy engine without evidence.
- Treats client routing as tenant isolation.
- Creates a generic plugin system for two roles.
