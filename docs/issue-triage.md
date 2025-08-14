# Issue Triage Workflows

This document describes a comprehensive system for triaging GitHub issues using the Gemini CLI GitHub Action. This system consists of two complementary workflows: a real-time triage workflow and a scheduled triage workflow.

## How it Works

```mermaid
graph TD
    subgraph "Triggers"
        A[Issue Opened or Reopened]
        B[Scheduled Cron Job]
        C[Manual Dispatch]
        D[Issue Comment with '@gemini-cli /triage' Created]
    end

    subgraph "Gemini CLI Action"
        E[Get Issue Details]
        F{Issue needs triage?}
        G[Analyze Issue with Gemini]
        H[Apply Labels]
    end

    A --> E
    B --> E
    C --> E
    D --> E
    E --> F
    F -- Yes --> G
    G --> H
    F -- No --> J((End))
    H --> J
```
