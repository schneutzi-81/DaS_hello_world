# Azure Cost Optimization Agent

## Overview

This repository will host a greenfield Azure-native cost optimization agent for **one Azure subscription**. The solution will use **Azure Cost Management exports/APIs**, **Azure Advisor**, **Azure Resource Graph**, and **tagging hygiene** signals to generate **daily manual reports** using **Azure AI Foundry**.

The first release is intentionally **report-only**: it will find opportunities, prioritize them, generate audience-specific summaries, and support review workflows without changing Azure resources automatically.

## Agreed v1 Scope

- **Data source:** Azure Cost Management exports / APIs
- **Additional inputs:** Azure Advisor, Azure Resource Graph, tagging hygiene
- **Generative AI layer:** Azure AI Foundry / multi-model setup
- **Scope:** one subscription
- **Refresh cadence:** daily
- **Outputs:** executive summary and engineering action list
- **Automation boundary:** report-only

## Target Architecture

### 1. Ingestion Layer
- Pull cost and usage data from Azure Cost Management
- Pull optimization signals from Azure Advisor
- Pull inventory and ownership context from Azure Resource Graph
- Pull tagging completeness / hygiene signals
- Schedule daily refresh runs

### 2. Data Layer
- Store raw exports and API payloads
- Normalize costs, recommendations, inventory, and ownership metadata
- Track recommendation history, status, savings estimate, confidence, and report inclusion

### 3. Optimization Engine
- Apply deterministic FinOps rules
- Identify waste, underutilization, rightsizing, reservation, and hygiene opportunities
- Score recommendations by savings potential, effort, confidence, and risk

### 4. AI Layer
- Use Azure AI Foundry for:
  - executive summaries
  - engineering action lists
  - explanation generation
  - follow-up Q&A over the latest report dataset
- Ground model outputs with normalized cost and inventory data

### 5. Reporting Layer
- Generate a daily executive summary
- Generate a daily engineering action list
- Support export-ready formats for manual sharing and review

### 6. Review Workflow
- Provide a lightweight review experience for findings
- Track lifecycle states:
  - new
  - accepted
  - deferred
  - rejected
  - completed

### 7. Security and Operations
- Use managed identity and least-privilege RBAC
- Use Key Vault for secrets and configuration
- Add telemetry, audit logging, and job monitoring

## Backlog Breakdown

### Workstream 1: Solution Architecture
- Define end-to-end Azure-native architecture
- Select core services for orchestration, storage, AI, reporting, and UI
- Define extension points for later remediation automation

### Workstream 2: Cost and Metadata Ingestion
- Ingest Azure Cost Management exports/APIs
- Ingest Azure Advisor recommendations
- Ingest Azure Resource Graph inventory and relationships
- Ingest tagging hygiene signals
- Define daily refresh orchestration and error handling

### Workstream 3: Data Model and Storage
- Define raw, curated, and semantic layers
- Model recommendation entities and report entities
- Define retention, partitioning, and query patterns

### Workstream 4: Optimization and Prioritization Engine
- Define deterministic FinOps rules
- Define prioritization logic
- Define recommendation confidence scoring
- Define recommendation lifecycle workflow

### Workstream 5: Azure AI Foundry Layer
- Design prompt flows for executive summaries
- Design prompt flows for engineering action lists
- Define retrieval context and grounding strategy
- Define safety and hallucination guardrails

### Workstream 6: Reporting Workflow
- Define executive summary template
- Define engineering action list template
- Define daily generation process
- Define delivery and export formats

### Workstream 7: Review Experience
- Define dashboard or lightweight app surface
- Support filtering, status updates, and report history
- Support reviewer notes and action tracking

### Workstream 8: Security and Observability
- Define RBAC model
- Define managed identity usage
- Define Key Vault usage
- Define logs, metrics, alerts, and audit coverage

### Workstream 9: Delivery Plan
- Break implementation into phases
- Keep v1 report-only
- Plan later phases for approval flows, ticketing, and guarded remediation

## Proposed Delivery Phases

### Phase 1: Foundations
- Set up repository structure
- Define architecture and data contracts
- Define service boundaries

### Phase 2: Data Ingestion
- Implement Cost Management, Advisor, Resource Graph, and tagging ingestion
- Store and normalize daily snapshots

### Phase 3: Recommendation Engine
- Implement optimization logic and recommendation scoring
- Add lifecycle tracking

### Phase 4: AI and Reporting
- Integrate Azure AI Foundry
- Generate executive and engineering reports

### Phase 5: Review Experience
- Build the review dashboard / app surface
- Add filters, states, and report history

### Phase 6: Hardening
- Add security controls
- Add observability and operational runbooks

## Open Decisions

- Preferred backend stack
- Preferred frontend stack
- Preferred report output formats
- Exact sample export schema / columns for the first ingestion contract

## Notes

- This repo is currently effectively empty, so the implementation assumes a **greenfield build**.
- The GitHub backlog should remain aligned with this file so the planning view is consistent for remote review.
