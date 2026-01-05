# AI Research Agent → PDF Report Generator (n8n)

This n8n workflow implements an **autonomous AI research agent** that takes a user query, performs grounded web research using SERP-based sources, synthesizes a structured technical report, converts it into a PDF, and sends the result via email.

The workflow is **template-ready**, credential-safe, and designed to demonstrate production-style agent orchestration rather than prompt-only automation.

---

## What this workflow does

1. Receives a user query via chat input  
2. Uses an AI agent with enforced web grounding (SERP API)  
3. Cross-verifies information from multiple sources  
4. Generates a structured technical report  
5. Converts the report into a styled PDF  
6. Emails the generated PDF as an attachment  

---

## Key features

- Autonomous research agent (LangChain-based)
- Mandatory web grounding using SERP API
- Memory-enabled conversational context
- Structured, citation-ready output
- HTML → PDF conversion
- Email delivery
- No hardcoded secrets
- Reusable, template-safe design

---

## Workflow architecture

Chat Trigger
    ↓
AI Agent (LLM + SERP Tool + Memory)
    ↓
HTML Renderer (JavaScript)
    ↓
HTML → PDF
    ↓
Email (PDF attachment)


---

## AI Agent behavior

The AI Agent is instructed to:

- Perform **at least one web search**
- Cross-check important claims across multiple sources
- Prefer official documentation and technical write-ups
- Avoid marketing content and shallow explanations
- Match depth to user intent
- Produce:
  - Clearly titled sections
  - Short paragraphs and bullet points
  - Citations
  - A **TL;DR section** with 5–7 bullet points

The output is explicitly designed for **direct PDF conversion**.

---

## Inputs

### Required input

- **chatInput**  
  The research question or topic to investigate.

---

## Outputs

- A generated **PDF research report**
- Delivered via **email attachment**

---

## Required credentials

Users must configure the following credentials after importing the workflow:

- OpenAI API (or compatible provider)
- SERP API (for web search grounding)
- Gmail OAuth2 (for sending emails)
- HTML → PDF service credentials

> Credentials are **not exported** with the workflow and must be added by each user.

---

## Setup instructions

1. Import the workflow JSON into n8n  
2. Configure the required credentials  
3. (Optional) Set environment variables  
4. Activate the workflow  
5. Send a chat message to trigger a research run  

---

## Customization ideas

- Replace Gmail with Slack, Discord, or cloud storage  
- Add a model selector for cost vs. quality routing  
- Add validation for citation count or structure  
- Store generated PDFs instead of emailing  
- Extend the memory window for long-running research sessions  

---

## Intended use cases

- Technical research summaries  
- Architecture and system design analysis  
- Concept and literature exploration  
- Internal documentation generation  
- AI-assisted research workflows  

---

## Limitations

- Quality depends on SERP API coverage  
- Not intended for real-time news accuracy  
- Minimal PDF styling by design  
- Long queries may increase token usage

---

## Environment variables (optional)

env
NOTIFICATION_EMAIL=your@email.com  
