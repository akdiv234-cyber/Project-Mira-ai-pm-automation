# Program Charter
## Nexora AI Project Management Automation Platform

### 1. Program Vision

Build an AI-powered Project Management and Technical Program Management automation platform that reduces manual project management effort and improves planning consistency, risk visibility, validation and reporting.

The platform follows a human-in-the-loop approach: AI generates recommendations, while authorized people retain decision-making authority.

### 2. Business Problem

Project Managers and Technical Program Managers often spend significant time on:
- Creating project plans and roadmaps.
- Identifying and assessing project risks.
- Reviewing work-item quality and dependencies.
- Preparing weekly status reports.
- Following up on approvals and project decisions.

The objective is to streamline these activities through AI agents and workflow automation.

### 3. Project Scope

**In scope**
- Project Context Agent
- AI Planning Agent
- Risk Assessment Agent
- Validation Agent
- Gmail-based human approval
- Jira work-item creation
- Weekly project status reporting
- Langfuse tracing and observability
- Human evaluation of agent outputs

**Out of scope**
- Autonomous approval of project plans.
- Creating Jira work items without approval.
- Replacing human Project Managers.
- Automated financial and resource forecasting.

### 4. Technology Stack

- n8n Cloud – Workflow orchestration
- OpenAI – AI model capabilities
- Jira – Project work-item management
- Gmail – Human-in-the-loop approval
- Langfuse – AI observability and evaluation

### 5. Success Criteria

Proposed targets to measure during pilot evaluation:

| Metric | Target |
|---|---|
| Project plan preparation | Under 30 minutes of human review |
| Risk assessment | High-priority risks have owners and mitigations |
| Validation | All plans pass the required quality gate before approval |
| Jira creation | 100% require human approval |
| Weekly reporting | Under 15 minutes of preparation |
| Observability | Agent traces visible in Langfuse |

These are proposed targets, not yet verified results.

### 6. Key Stakeholders

- Program Sponsor
- AI Project Manager / Technical Program Manager
- Project Managers
- Technical Lead
- AI / ML Engineers
- QA and Testing Team
- Business Stakeholders
- Risk Owners

### 7. Governance and Decision-Making

- AI agents generate recommendations and outputs.
- Human reviewers approve or reject generated plans.
- Validation failures must stop the approval process.
- Warnings require human review.
- High-impact risks must be escalated to the relevant owner.
- Approved plans are sent to Jira for work-item creation.

### 8. Key Risks

- Incorrect or incomplete AI-generated plans.
- Missing risk mitigations.
- Poor dependency mapping.
- Jira integration failures.
- Exposure of credentials or sensitive data.
- Incomplete observability and evaluation data.

### 9. Rollout Approach

1. Initial workflow development.
2. Agent integration and validation.
3. Controlled testing and human review.
4. Jira and reporting integration.
5. Langfuse observability and evaluation.
6. Pilot assessment and improvements.

### 10. Project Status

Prototype / Initial implementation.

The platform has working agent workflows, Jira integration, human approval and reporting capabilities. Observability and evaluation are being developed and refined.
