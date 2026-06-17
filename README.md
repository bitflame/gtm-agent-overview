Demo link
https://gtmclient-production.up.railway.app/agent/

Architecture diagram

Architecture Overview  
The GTM Agent is a Django‑based REST API that orchestrates multiple LLM providers (Groq, OpenAI, Anthropic) via a LangChain agent. Requests from clients are routed through /api/v1/agent/chat, where prompts are constructed, models are selected (including A/B testing setups), and conversations are tracked in NeonDB (Postgres). A Go sidecar microservice handles specialized preprocessing and analytics tasks.

In production, the system is deployed on Railway with built‑in logging. For demo and observability purposes, a local Docker Compose setup runs Prometheus and Grafana to visualize metrics such as latency, error rates, and throughput.
