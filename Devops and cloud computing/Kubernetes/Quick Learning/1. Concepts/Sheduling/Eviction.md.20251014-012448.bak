# Cue
* What are evictions in Kubernetes?
* Why do they happen?
* Who can initiate them?
* How does Kubernetes handle them?
# Key Points
* **Definition:**
  * Evictions terminate or delete running pods from a node.
* **Reasons:**
  * **Resource constraints** (CPU, memory, disk).
  * **Pod failures** or node issues.
* **Initiation:**
  * Can be triggered by the **system** automatically.
  * Can be done **manually** by administrators via the API.
* **Types:**
  * **Graceful evictions:** Allow pods to clean up resources before termination.
  * **Forceful evictions:** Immediately terminate pods.
* **Mechanisms to manage:**
  * **Preemption:** Higher-priority pods can evict lower-priority ones.
  * **Pod Disruption Budgets (PDBs):** Limit voluntary evictions to minimize service impact.
* **Importance:**
  * Necessary for cluster **health, stability, and resource management**.
# Summary
Evictions in Kubernetes remove pods from nodes when resources are constrained or failures occur. They can be graceful or forceful, initiated by the system or admins. Tools like preemption and pod disruption budgets help manage evictions while minimizing service disruption.

