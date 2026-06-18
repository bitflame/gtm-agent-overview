An AI-powered agentic application that assists users with company research, prospect analysis, and personalized outreach generation using LangChain, Llama 3, and Groq.



## Source Code Availability

This repository provides an overview of the architecture, deployment, and capabilities of the GTM Agent.

The full source code is intentionally private. The project incorporates proprietary work related to agent orchestration, prompt engineering, deployment, and observability that I use as part of my professional portfolio.

I am happy to discuss the implementation details, design decisions, and architecture with hiring managers, recruiters, and interview teams upon request.

The following technologies and platforms were used to build this solution:

* Python
* Django
* LangChain
* Groq
* Llama 3
* Railway
* Go
* Prometheus
* Grafana

The project uses LangChain to orchestrate interactions with Llama 3 models hosted on Groq, enabling low-latency responses while maintaining a flexible agent-based architecture. The solution combines AI orchestration, cloud-native deployment, and observability practices to provide a production-oriented learning environment for agentic AI development.


</> Markdown
## Demo link:
https://gtmclient-production.up.railway.app/agent/

Architecture diagram:

<img width="760" height="768" alt="Untitled Diagram drawio (2)" src="https://github.com/user-attachments/assets/e9c6d672-039e-4060-892f-31116b27d4f8" />


Architecture Overview  
The GTM Agent is a Agent-based architecture leveraging Django‑based REST API that orchestrates multiple LLM providers (Groq-Llama 3.x, Groq-DeepSeek, Groq-Qwen, Groq-Gemma, Groq Mistral) via a LangChain agent. Requests from clients are routed through /api/v1/agent/chat, where prompts are constructed, models are selected (including A/B testing setups), and conversations are tracked in NeonDB (Postgres). A Go sidecar microservice handles specialized preprocessing and analytics tasks. Here is the information flow: 
User -> Django UI -> Agent Controller -> Prompt Builder -> Groq (Llama) -> Response processing -> UI Rendering

## Observability

The application includes a Go-based sidecar service that provides operational telemetry and monitoring capabilities.

Metrics are exported to Prometheus and visualized through Grafana dashboards, allowing visibility into:

* Request volume
* Response latency
* Error rates
* Service health
* Application performance

This observability layer was designed to mirror production monitoring practices commonly used in cloud-native deployments.

## Why I Built This

I built GTM Agent to deepen my understanding of agentic AI systems and modern LLM application development.

The project allowed me to explore:

* Agent orchestration
* Prompt engineering
* LLM integration
* Cloud deployment
* Monitoring and observability
* Production-oriented architecture

My goal was not simply to call an LLM API, but to build and operate a complete AI-powered application from development through deployment. It allowed me to validate the impact of prompts to the outcome, and evaluate instances which required other solutions such as RAG.


In production, the system is deployed on Railway with built‑in logging. For demo and observability purposes, a local Docker Compose setup runs Prometheus and Grafana to visualize metrics such as latency, error rates, and throughput. Below are screenshots of the UI...

<img width="1805" height="991" alt="Screenshot From 2026-06-18 09-43-53" src="https://github.com/user-attachments/assets/11f394e8-b798-4568-8497-07f77add476e" />

<img width="1805" height="991" alt="Screenshot From 2026-06-18 09-44-37" src="https://github.com/user-attachments/assets/95a95ce0-f8e6-4d10-9020-9c6f29b99a07" />

## Challenges and Lessons Learned: A systematic evaluation pipeline, and process with metrics that are mapped to business outcomes and requirements is crucial. Crucial to avoiding extra cost, and arriving at a solution that works for the organization. The right level of prompt engineering will provide the results needed often, and if not then perhaps fine-tunning methods. Context management, and conversation memory can save on the number of tokens used. RAG solutions can address accuracy concerns when other methods such as Response validation fail. 

