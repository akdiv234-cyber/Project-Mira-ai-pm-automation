# AI PM Automation – Workflow Design

## 1. Overview

The Nexora AI PM Automation Platform uses n8n Cloud to orchestrate multiple AI agents that support project planning, risk management, validation, approval and reporting.

The solution is designed around human oversight and controlled automation.

## 2. End-to-End Workflow

The workflow follows these stages:

1. Project input is provided through a project description or downloaded Excel file.
2. Project Context Agent extracts and standardizes project information.
3. Planning Agent generates project phases, milestones, timelines and work items.
4. Risk Agent identifies project risks, assesses probability and impact, and recommends mitigations.
5. Validation Agent checks the project plan and risk coverage.
6. An IF node evaluates the validation result.
7. Gmail sends the plan for human review and approval.
8. Following approval, Jira creates the corresponding project work items.
9. Weekly Status Agent prepares project progress reports.
10. Langfuse receives agent traces for observability and human evaluation.

## 3. AI Agent Responsibilities

### Project Context Agent

**Purpose:** Extract structured project information.

Responsibilities:
- Identify project name and client.
- Extract business objectives.
- Identify project duration.
- Extract major capabilities.
- Prepare standardized project context.

### Planning Agent

**Purpose:** Generate a structured project roadmap.

Responsibilities:
- Create Epics, Features, User Stories and Tasks.
- Define timelines and dependencies.
- Identify milestones.
- Assign responsible roles.
- Generate project work items for Jira.

### Risk Agent

**Purpose:** Identify and assess project risks.

Responsibilities:
- Identify delivery, technical, integration and security risks.
- Assess probability and impact.
- Assign risk scores.
- Recommend mitigation actions.
- Identify risk owners.

### Validation Agent

**Purpose:** Act as a project plan quality gate.

Responsibilities:
- Check required work items.
- Identify duplicates.
- Review dependencies.
- Check milestones and acceptance criteria.
- Validate risk coverage.
- Identify missing mitigations and ownership.
- Return PASS, WARNING or FAIL with recommendations.

## 4. Human-in-the-Loop Approval

Gmail is used to notify the reviewer about the generated project plan.

The reviewer evaluates the plan and decides whether it should proceed.

- Approved: Continue to Jira work-item creation.
- Rejected: Return the plan for revision.

AI-generated recommendations do not replace human approval.

## 5. Jira Integration

Jira is used as the project management system.

The workflow creates approved project work items and retrieves existing issues for reporting and tracking.

## 6. Weekly Status Reporting

The reporting workflow retrieves Jira issues and uses project information to prepare a weekly status report.

The report supports project progress reviews and stakeholder communication.

## 7. Observability – Langfuse

Langfuse is used to monitor AI agent execution through traces and observations.

The observability design covers:
- Planning Agent execution.
- Risk Agent execution.
- Validation Agent execution.
- Agent outputs and relevant attributes.
- Human evaluation and quality scores.

Manual evaluation is used to assess the quality of agent outputs.

## 8. Technology Components

| Component | Responsibility |
|---|---|
| n8n Cloud | Workflow orchestration |
| OpenAI | AI model execution |
| Jira | Work-item management |
| Gmail | Human approval |
| Langfuse | Observability and evaluation |

## 9. Governance

- Human approval is required before Jira creation.
- Validation warnings require review.
- Validation failures should prevent progression.
- Credentials must be stored securely.
- AI-generated outputs must be reviewed before operational use.

## 10. Implementation Status

The prototype includes working agent workflows, Jira integration, Gmail approval and weekly reporting. Langfuse tracing has been demonstrated, with observability and evaluation capabilities being refined.
