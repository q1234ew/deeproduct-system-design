# Evaluation Case: Existing System Review

## Purpose

Test evidence quality and incremental evolution.

## Target

Use a medium-sized repository with several modules, persistence, background work, and limited architecture documentation.

## Prompt

```text
请基于代码事实评审该系统架构，找出最重要的三个责任、状态或生命周期问题，并给出渐进式改进方案。
```

## Expected strengths

- Reads entry points, consumers, persistence, and runtime composition before judging.
- Separates observed facts from inferences.
- Prioritizes three material findings rather than producing an inventory.
- Preserves strengths and names deliberate non-changes.
- Gives each migration phase acceptance evidence.

## Failure signals

- Derives architecture from directory names alone.
- Treats tests or documentation as proof of production use.
- Recommends a rewrite without migration evidence.
- Reports style preferences as architecture defects.
