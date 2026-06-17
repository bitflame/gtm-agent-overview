Demo link
https://gtmclient-production.up.railway.app/agent/

Architecture diagram:

<img width="760" height="768" alt="Untitled Diagram drawio (2)" src="https://github.com/user-attachments/assets/e9c6d672-039e-4060-892f-31116b27d4f8" />


Architecture Overview  
The GTM Agent is a Django‑based REST API that orchestrates multiple LLM providers (Groq, OpenAI, Anthropic) via a LangChain agent. Requests from clients are routed through /api/v1/agent/chat, where prompts are constructed, models are selected (including A/B testing setups), and conversations are tracked in NeonDB (Postgres). A Go sidecar microservice handles specialized preprocessing and analytics tasks.

In production, the system is deployed on Railway with built‑in logging. For demo and observability purposes, a local Docker Compose setup runs Prometheus and Grafana to visualize metrics such as latency, error rates, and throughput.
