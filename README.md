# supporttriage-ai-
AI co-worker that triages support tickets and drafts grounded replies, with a human in the loop. Built with IBM Bob for the IBM AI Builders Challenge.
README.md - SupportTriage AI
SupportTriage AI
An AI co-worker that triages support tickets and drafts grounded replies, keeping a human in the loop for
every outbound message.
Built for the IBM AI Builders Challenge (Wildcard Track) using IBM Bob as the primary development tool,
with AI as a core functional component.
Problem Statement
SMB SaaS support teams (10–200 employees) and help desks drown in high-volume, unstructured tickets
arriving via email, chat, and forms. The result:
These directly drive SLA misses and lower agent throughput.
Solution Description
SupportTriage AI follows the most durable enterprise AI pattern: intake → AI reasoning → action → human
review.
Every outbound message requires human approval. The AI prepares the next valid action; the human ships it.
AI Approach and Architecture
 Email/Chat/Form
 |
 v
 [ Intake Connector ] Normalize ticket -> structured object (Zendesk, single channel for MVP)
 |
 v
Slow triage and rising first-response times •
Inconsistent categorisation and manual routing errors •
Repetitive reply drafting that burns agent hours •
Lack of context at handoff, so agents restart investigations from scratch
•
1. Trigger — A new ticket arrives (email, chat, or form).
AI step — Classify category & priority, extract entities (account, product, error codes), summarize the
thread, and draft a suggested reply with next steps.
2.
Action — Auto-tag and route the ticket to the correct queue, then present the draft + context to an agent
for one-click send or edit.
3.
4. Feedback loop — Agent edits feed back into the system for continual improvement.
 [ Classify & Prioritize ] IBM Granite / watsonx -> category + priority labels
 |
 v
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
Guardrails (responsible AI by design):
Stack:
Selected Challenge Theme
Wildcard — Build Intelligent Systems for the Future of Work. SupportTriage AI is an AI co-worker / workflow
automation tool that reduces repetitive work, improves routing decisions, and helps support teams hit
outcomes faster.
How IBM Bob Was Used
IBM Bob served as the primary development environment to plan, develop, test, and refine the solution:
Target Users
Key Metrics
Human-in-the-loop approval for all outbound messages •
RAG grounding in account data to prevent hallucinated content •
PII redaction before model input, minimal context logging, role-based access •
IBM Bob — primary development tool (plan, build, test, refine) •
IBM Granite / watsonx — classification, summarization, generation
•
LangChain / LangFlow — orchestration of the multi-step pipeline •
RAG — retrieval grounding against account/product knowledge
•
Scaffolding the project structure and the modular intake connector •
Implementing and iterating on the classification, extraction, and summarisation steps •
Wiring up the RAG draft-generation pipeline and routing logic •
Building the agent review UI and the PII redaction guardrails •
Primary: Support team lead at an SMB SaaS company (10–200 employees) •
Secondary: Tier-1 agents, product managers, customer success managers •
First-response time
MVP Scope
To keep the prototype tight and demo-ready: one channel (email), one helpdesk (Zendesk) — classify,
summarize, draft, route, human approves. The feedback-retraining loop is roadmap, not v1.
Risks & Mitigations
Risk Mitigation
Incorrect routing /
hallucinated content
Human-in-the-loop
approval + RAG grounding
in account data
PII / data privacy
exposure
Redact sensitive fields
before model input;
minimal logging; rolebased access
Integration brittleness: Start with a single
helpdesk; modular
connectors; measure ROI
before scaling
Demo
Submitted to the IBM AI Builders Challenge — Wildcard Track.
