# Questions / Cues

* What is a quota?
* How to assign a quota?
* Utility of quotas?
# Notes

* Help limit res usage for specific groups of res in k8s.
* Can be set for CPU, mem, other res, & for other nbr of obj in a namespace.
* Ensure fair res distribution across diff team or proj within a cluster.
* Can be apply to individual namespace.
* k8s support soft (less strict) & hard (more strict) quotas.
* Can be manage with k8s API or YAML.
# Summary
A Kubernetes **Quota** controls res usage in a namespace, ensuring fair res distribution and cluster stability. It can limit CPU, mem, storage, and nbr of obj. Quotas can be **hard (strict)** or **soft (flexible)** and are applied via YAML or k8s API, helping teams manage res efficiently.


