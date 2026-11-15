# AI Agent Observability and Evaluation

## 1. Overview

Langfuse is integrated with the Nexora AI PM Automation Platform to provide observability and support the evaluation of AI agent outputs.

The observability approach focuses on the Planning Agent, Risk Agent and Validation Agent.

## 2. Why Observability Is Required

AI agents can generate incorrect, incomplete or inconsistent outputs.

Observability helps the team:
- Understand agent execution.
- Inspect generated outputs.
- Identify failures and quality issues.
- Review agent behaviour.
- Evaluate output quality over time.

## 3. Architecture

n8n Cloud orchestrates the AI agents and sends trace data to Langfuse using the OpenTelemetry-compatible ingestion endpoint.

The main observations include:

1. Planning Agent
2. Risk Agent
3. Validation Agent

The trace structure is designed to provide a consolidated view of the agent execution.

## 4. Langfuse Integration

Langfuse receives trace data through its OpenTelemetry ingestion endpoint.

The integration uses:
- HTTP POST request.
- OpenTelemetry JSON trace payload.
- Basic authentication using Langfuse public and secret keys.
- Content-Type: application/json.
- Langfuse ingestion version header.

Credentials must be stored securely and must never be committed to GitHub.

## 5. Agent-Level Observability

### Planning Agent

Monitor:
- Generated project work items.
- Number of work items.
- Project plan output.
- Planning execution status.

### Risk Agent

Monitor:
- Identified risks.
- Risk probability and impact.
- Risk scores.
- Risk owners.
- Recommended mitigations.

### Validation Agent

Monitor:
- Validation status: PASS, WARNING or FAIL.
- Identified issues.
- Warnings.
- Recommended actions.
- Risk coverage and mitigation mapping.

## 6. Human Evaluation

The prototype uses human evaluation rather than relying solely on automated LLM-as-a-Judge scoring.

Reviewers inspect agent outputs in Langfuse and provide quality scores.

Suggested evaluation dimensions:

| Agent | Evaluation Criteria |
|---|---|
| Planning Agent | Completeness, timeline accuracy, scope alignment |
| Risk Agent | Risk identification, assessment quality, mitigation coverage |
| Validation Agent | Issue detection, risk coverage, validation accuracy |

## 7. Manual Scoring Scale

A suggested scoring scale:

| Score | Meaning |
|---|---|
| 1.0 | Excellent |
| 0.8 | Good |
| 0.5 | Needs improvement |
| 0.2 | Poor |
| 0.0 | Unusable |

Scores should be accompanied by reviewer comments to explain the assessment.

## 8. Evaluation Process

1. Execute the n8n workflow.
2. Open Langfuse.
3. Locate the relevant trace.
4. Inspect the agent observations and outputs.
5. Review the generated result against project requirements.
6. Assign a manual quality score.
7. Add reviewer comments.
8. Review scores and trends to identify improvement areas.

## 9. Security and Governance

- Never expose Langfuse secret keys.
- Keep API credentials in n8n credentials.
- Avoid sending unnecessary personal or confidential information in traces.
- Ensure generated plans and risk recommendations receive appropriate human review.

## 10. Current Implementation Status

The Langfuse health check and trace ingestion have been tested successfully, and traces are visible in Langfuse.

Manual human evaluation is the selected evaluation approach.

Automatic token usage, cost and real execution latency should only be reported when those metrics are actually captured and verified.
