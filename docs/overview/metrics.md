# Metrics

## Metrics & Observability

- **Custom performance metrics added**
    - TTFT (Time To First Token)
    - TPS (Tokens Per Second)
    - Latency

![](2.png)

- **Metrics are stored in Redis instead of in-memory**
    - Needed to aggregate metrics across multiple replicas.
    - Native LiteLLM metrics break when running more than one replica because:
        - Each pod keeps metrics in its own memory.
        - No global aggregation exists by default.

![](3.png)

- **Metrics are scraped from service using cortex**
