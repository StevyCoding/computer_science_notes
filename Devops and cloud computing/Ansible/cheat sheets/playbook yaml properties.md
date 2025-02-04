# Playbook most commons properties 

Here's a table explaining the most common properties in an Ansible playbook:  

| **Property**   | **Description** | **Example** |
|--------------|---------------|------------|
| `name` | A human-readable name for the play or task, making output more readable. | `name: Install Apache` |
| `hosts` | Specifies target hosts or groups from the inventory. | `hosts: web_servers` |
| `become` | Enables privilege escalation (e.g., sudo) for tasks requiring root access. | `become: yes` |
| `tasks` | Defines a list of tasks to be executed on target hosts. | `tasks: [...]` |
| `package` | Manages software packages using package managers like `apt`, `yum`. | `apt: name=nginx state=present` |
| `template` | Uses Jinja2 templates to configure files dynamically. | `template: src=config.j2 dest=/etc/config` |
| `copy` | Copies files from the control machine to target hosts. | `copy: src=file.txt dest=/tmp/file.txt` |
| `command` | Executes a command on the target machine (not idempotent). | `command: echo "Hello"` |
| `shell` | Runs shell commands on the target machine (not idempotent). | `shell: uptime` |
| `notify` | Triggers handlers when a task makes changes. | `notify: Restart Apache` |
| `handlers` | Defines tasks that execute only when notified. | `handlers: [...]` |
| `vars` | Defines variables within a playbook. | `vars: app_version: 1.2.3` |
| `roles` | Imports reusable roles to structure playbooks efficiently. | `roles: - webserver` |
| `tags` | Assigns tags to tasks for selective execution. | `tags: [install, config]` |
| `when` | Sets conditions for task execution. | `when: ansible_os_family == "Debian"` |
| `loop` | Repeats a task multiple times with different values. | `loop: [user1, user2]` |
| `with_items` | Iterates over a list (alternative to `loop`). | `with_items: [pkg1, pkg2]` |
| `environment` | Sets environment variables for a task. | `environment: PATH: "/usr/local/bin:$PATH"` |
| `ignore_errors` | Continues playbook execution even if a task fails. | `ignore_errors: yes` |