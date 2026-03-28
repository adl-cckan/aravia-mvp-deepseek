# ARAVIA AGENT BUILDER — INTEGRATION GUIDE
## MVP v1.0 | Ching Kan's PhD-Practice Intelligence System

---

## QUICK START

```bash
pip install streamlit crewai crewai-tools openai
streamlit run aravia_chat_interface.py
```

---

## PHASE 2 INTEGRATION CHECKLIST
When Ching Kan completes Phase 2 (20-year knowledge structuring):

### Step 1 — Load the Knowledge Base
Replace all `[PROJECT X placeholder]` tags in both agent prompts with:
- Actual project names, locations, years
- Key design decisions and outcomes
- Photos / drawings (as base64 for Vision tool)
- Community feedback and post-occupancy notes

### Step 2 — Add to Agent Backstory
In `design_critic_agent` and `thesis_explainer_agent`, update the
`backstory` field with the structured knowledge from Phase 2.

### Step 3 — Index the Thesis
Feed each thesis chapter into a vector store (Chroma / Pinecone).
Connect via `VectorStoreRetrievalTool` in the Thesis Explainer Agent.

### Step 4 — Test
Run 10 sample critique sessions with real Aravia projects.
Run 10 sample thesis questions across all chapters.
Calibrate temperature and max_tokens per agent.

---

## ARCHITECTURE

```
aravia_chat_interface.py   ← Streamlit UI (Deliverable 3)
├── design_critic_agent    ← CrewAI Agent (Deliverable 1)
│   ├── VisionTool         ← Reads uploaded design images
│   ├── FileReadTool       ← Reads PDFs and plans
│   └── PhD Framework      ← Heterotopias, Arendt, Lefebvre, LFD, AR
└── thesis_explainer_agent ← CrewAI Agent (Deliverable 2)
    ├── FileReadTool        ← Reads thesis chapters
    └── VectorStore (TBD)  ← Phase 2 knowledge base
```

---

## ENVIRONMENT VARIABLES NEEDED
```
OPENAI_API_KEY=sk-...        # or ANTHROPIC_API_KEY
SERPER_API_KEY=...           # for web search (optional)
CALENDLY_LINK=https://calendly.com/aravia/15min
```

---

## DEPLOYMENT OPTIONS
- **Local**: `streamlit run aravia_chat_interface.py`
- **Cloud**: Deploy to Streamlit Cloud (free tier available)
- **Embedded**: Export as iframe into Aravia website or Notion
- **Custom Domain**: Use Cloudflare Tunnel for aravia.studio/ai

---

*Built for Aravia Studio | Ching Kan's PhD-Practice Integration*
*Phase 2 integration slot reserved — ready to auto-populate.*
