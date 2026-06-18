An AI powered GTM agent that helps users research companies, and send outreach emails.
</> Markdown
## Demo link:
https://gtmclient-production.up.railway.app/agent/

Architecture diagram:

<img width="760" height="768" alt="Untitled Diagram drawio (2)" src="https://github.com/user-attachments/assets/e9c6d672-039e-4060-892f-31116b27d4f8" />


Architecture Overview  
The GTM Agent is a Agent-based architecture leveraging Django‑based REST API that orchestrates multiple LLM providers (Groq, OpenAI, Anthropic) via a LangChain agent. Requests from clients are routed through /api/v1/agent/chat, where prompts are constructed, models are selected (including A/B testing setups), and conversations are tracked in NeonDB (Postgres). A Go sidecar microservice handles specialized preprocessing and analytics tasks. Here is the information flow: 
User -> Django UI -> Agent Controller -> Prompt Builder -> Groq (Llama) -> Response processing -> UI Rendering

In production, the system is deployed on Railway with built‑in logging. For demo and observability purposes, a local Docker Compose setup runs Prometheus and Grafana to visualize metrics such as latency, error rates, and throughput. Below are screenshots of the UI...

<img width="1805" height="991" alt="Screenshot From 2026-06-18 09-43-53" src="https://github.com/user-attachments/assets/11f394e8-b798-4568-8497-07f77add476e" />

<img width="1805" height="991" alt="Screenshot From 2026-06-18 09-44-37" src="https://github.com/user-attachments/assets/95a95ce0-f8e6-4d10-9020-9c6f29b99a07" />

Lessons Learned: A systematic evaluation pipeline, and process with metrics that are mapped to business outcomes and requirements is crucial. Crucial to avoiding extra cost, and arriving at a solution that works for the organization. The right level of prompt engineering will provide the results needed often, and if not then perhaps fine-tunning methods. Context management, and conversation memory can save on the number of tokens used. RAG solutions can address accuracy concerns when other methods such as Response validation fail. 
