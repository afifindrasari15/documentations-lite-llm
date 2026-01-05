# Architecture Overview

## System Architecture

This document describes the high-level architecture of the system.



**More replicas are better than fewer replicas with high memory / CPU**

- Horizontal scaling works better for LiteLLM than vertical scaling.
    - Improves throughput and reduces tail latency under concurrent load.
- Separate port for health checking

> **Haproxy is for maverick, because its deployed in two cluster (L40s & H100)**: PostgreSQL for persistent storage 
