# Azure Cost Optimization Agent

This repository contains the planning docs for a greenfield Azure-native cost optimization agent.

## Scope
- One Azure subscription
- Daily refresh cadence
- Azure Cost Management exports/APIs as the primary input
- Azure Advisor, Azure Resource Graph, and tagging hygiene as supporting signals
- Azure AI Foundry for summarization and report generation
- Report-only v1 with no automatic remediation

## Outputs
- Executive summary
- Engineering action list
- Review workflow and backlog structure

See `plan.md` for the full architecture and delivery breakdown.
