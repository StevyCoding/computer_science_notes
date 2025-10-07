## Questions
* What is contention?
* What are monitoring tools?
* What are optimization techniques?
* What types of res are needed?
## Key Points
**Topic:** Monitoring & optimizing res usage in K8s
* Essential for efficient & effective res utilization.
**Monitoring Tools**
* **Metrics Server** – collects res usage data.
* **Prometheus** – metrics & alerting.
* **CRI (Container Runtime Interface)** – monitors container-level data.
**Optimization Methods**
* Set **requests & limits**.
* Use **HPA (Horizontal Pod Autoscaler)**.
* Implement **pod affinity/anti-affinity** rules.
* Configure **node selection** to reduce contention & optimize res usage.
## Summary
K8s monitoring tools track res usage, while optimization techniques (HPA, requests/limits, affinity rules) balance workloads & prevent contention, ensuring effective use of cluster res.

