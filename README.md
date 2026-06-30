SupportTriage AI
An AI co-worker that triages support tickets and drafts grounded replies, keeping a human in the loop for every
outbound message.
Problem Statement
• Slow triage and rising first-response times
• Inconsistent categorisation and manual routing errors
• Repetitive reply drafting that burns agent hours
• Lack of context at handoff, so agents restart investigations from scratch
Solution Description
1. Trigger — A new ticket arrives (email, chat, or form).
AI step — Classify category & priority, extract entities (account, product, error codes), summarize the
thread, and draft a suggested reply with next steps.
2.
Action — Auto-tag and route the ticket to the correct queue, then present the draft + context to an agent
for one-click send or edit.
3.
4. Feedback loop — Agent edits feedback into the system for continual improvement.
AI Approach and Architecture
 Email/Chat/Form
 |
 v
 [ Intake Connector ] Normalise ticket -> structured object (Zendesk, single channel for
MVP)
 |
 v
 [ Classify & Prioritize ] IBM Granite / watsonx -> category + priority labels
 |
 v
Guardrails (responsible AI by design):
Stack:
Wildcard — Build Intelligent Systems for the Future of Work. SupportTriage AI is an AI co-worker / workflow
automation tool that reduces repetitive work, improves routing decisions, and helps support teams hit outcomes
faster.
IBM Bob served as the primary development environment to plan, develop, test, and refine the solution:
 [ Extract & Summarize ] Entities (account, product, error codes) + concise thread summary
 |
 v
 [ Draft Reply (RAG) ] Grounded in account/product data to prevent hallucination
 |
 v
 [ Auto-tag & Route ] Route to correct agent queue
 |
 v
 [ Agent Review UI ] Human-in-the-loop: review draft + context, one-click send or edit
• Human-in-the-loop approval for all outbound messages
• RAG grounding in account data to prevent hallucinated content
• PII redaction before model input, minimal context logging, role-based access
• IBM Bob — primary development tool (plan, build, test, refine)
• IBM Granite / watsonx — classification, summarisation, generation
• LangChain / LangFlow — orchestration of the multi-step pipeline
• RAG — retrieval grounding against account/product knowledge
Selected Challenge Theme
How IBM Bob Was Used
• Scaffolding the project structure and the modular intake connector
• Implementing and iterating on the classification, extraction, and summarisation steps
• Wiring up the RAG draft-generation pipeline and routing logic
• Building the agent review UI and the PII redaction guardrails
Target Users
• Primary: Support team lead at an SMB SaaS company (10–200 employees)
• Secondary: Tier-1 agents, product managers, customer success managers
Key Metrics
• First-response time
To keep the prototype tight and demo-ready: one channel (email), one helpdesk (Zendesk) — classify, summarise,
draft, route, human approves. The feedback-retraining loop is roadmap, not v1.
Submitted to the IBM AI Builders Challenge — Wildcard Track.
• % auto-routed correctly
• Agent time saved
• SLA compliance
MVP Scope
Risks & Mitigations
Demo
• Live demo/presentation video (max 3 min): coming soon
• Repository: this repo
