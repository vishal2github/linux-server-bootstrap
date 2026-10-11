# Linux Server Bootstrap with Ansible

A learning and portfolio project focused on automating Linux server configuration using Ansible.

The goal is to develop a reusable, role-based automation structure for configuring web servers across development and production environments.

### Project Goals

- Automate common Linux server configuration tasks.
- Separate environment-specific settings from reusable automation.
- Use Ansible roles to keep tasks organized and maintainable.
- Manage Nginx configuration with Jinja2 templates and handlers.
- Develop repeatable and testable infrastructure automation practices.

### Current Features

- Separate development and production inventories.
- Web-server and database host groups.
- Reusable common and webserver roles.
- Package installation using Ansible's APT module.
- Nginx configuration templating.
- Configuration validation before deployment.
- Handler-based Nginx reloads.
- Environment-specific variables and a host-level override example.
- Conditional Fail2Ban package installation.
- Task tags for selective execution.

Features should be considered implemented and tested only to the extent verified in the current version of the repository.

### Repository Structure

```
```

### Prerequisites

- Ansible installed on the control machine.
- SSH access to the target Linux servers.
- Python available on the managed hosts, as required by the selected Ansible modules.
- A Debian-family target system for the current APT-based implementation.
- Appropriate privilege-escalation permissions for tasks requiring root access.

**Note:** Use disposable virtual machines for initial testing.

### Running the Playbook

Run commands from the repository root.

Check the development inventory:  
`ansible-inventory -i inventory/dev/hosts --graph`

Check playbook syntax:  
`ansible-playbook -i inventory/dev/hosts playbooks/site.yml --syntax-check`

Preview the planned development run:  
`ansible-playbook -i inventory/dev/hosts playbooks/site.yml --check --diff`

Apply the configuration to development servers:  
`ansible-playbook -i inventory/dev/hosts playbooks/site.yml`

**Note:** For production, explicitly select the production inventory. Test changes in development first and verify the production target hosts before applying them.

### Environment Configuration

Development and production use separate inventories and environment-specific variables.

The intended configuration includes:
- Development Nginx port: 8080
- Production Nginx port: 80
- Fail2Ban package installation controlled by an environment variable

**Note:** The host-specific override for web-prod-2 is retained as a learning example to demonstrate variable precedence. It should be reviewed before any production deployment.

### Security Notes

- Do not commit passwords, private SSH keys, access tokens, or other secrets.
- Keep SSH host-key verification enabled.
- Use Ansible Vault or another suitable secret-management mechanism for sensitive variables.
- Review firewall rules and remote access before applying security changes.
- Test configuration changes on disposable systems before using them on important servers.

### Planned Enhancements

- Linux security-hardening role.
- User and SSH-key management.
- More complete Fail2Ban configuration and service management.
- Encrypted sensitive variables using Ansible Vault.
- Automated linting and syntax checks.
- Role testing and CI integration.
- Improved deployment verification and error handling.

**Note:** This is an evolving project. The implemented features, test coverage, and documentation will be updated as development progresses.
