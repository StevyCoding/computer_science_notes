# Questions
- What's RBCA ?
- How to use it ?
- His importance ?
# Key points
- **Role-Base Access control (RBCA)**
	- method of controlling access to k8s res based on the roles assigned to usr or grp.
	 - create roles & binding them to usr or grp
	 - Roles => defined as a set of rules that determine what action can be performed on a specific res
	 - Res can be restricted /granted based on the **permissions** defined in the role
	 - help ensure **security** and **integrity** of Kubernetes cluster
# Summary 
RBAC is a method to control acess to k8s cluster based on roles of usr & grp. It allow you to create roles & assign them to usr or grp. A role = defined set of rules that specify what actions can be performed on a specific res. A res can be restricted/granted based on the perms listed in the role.
![[Pasted image 20250926115910.png]]