# Architecture Overview

## System Architecture

![DekaLLM System Architecture](1.png)

DekaLLM is the backend system that manages LLM usage for internal Cloudeka services, including token pricing, usage tracking, and billing integration.

---

## Architecture Layers

DekaLLM consists of three layers:

- Infrastructure Layer
- Model Layer
- Application Layer

---

## Infrastructure Layer

Provides compute resources to run the system.

- Kubernetes for orchestration and scaling
- NVIDIA GPUs for running LLM models

---

## Model Layer

Contains LLM models deployed on internal GPU infrastructure.

- Models run on Cloudeka-managed GPUs
- Lite LLM acts as a proxy to these models
- Models are exposed via OpenAI-compatible endpoints

---

## Application Layer

Core logic of Lite LLM.

- Receives incoming LLM requests
- Handles token usage and cost calculation
- Manages model routing and selection
- Collects usage data for analytics and billing

---

## Database

Used for usage tracking and performance optimization.

- PostgreSQL for persistent data (usage, pricing, billing)
- Redis for caching and temporary data

---

## Router

Handles incoming traffic and request distribution.

- NGINX as the primary router
- HAProxy used for Maverick deployments where a model runs across two GPU clusters (L40s & H100)

---

## Scaling and Health Check

Design considerations for Lite LLM.

- Horizontal scaling is preferred over vertical scaling
- More replicas perform better than fewer high-resource instances
- Separate port is used for health checking

---

## Cloudeka Integration

Integrates with internal Cloudeka billing systems.

- Usage and cost data support token-based pricing and user top-up
