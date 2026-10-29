# Ansible Beginner Project

A local Linux or WSL/Ubuntu lab that creates an IT documentation workspace with Ansible.

## Included files

- [inventory.ini](inventory.ini): local target inventory
- [setup_workspace.yml](setup_workspace.yml): creates the workspace and baseline file

## Requirements

- Linux or WSL/Ubuntu
- Python and Ansible installed in that environment
- A writable home directory for the user running the playbook

## Run

Open a terminal in the repository folder, then check the inventory and playbook:

```bash
ansible-inventory -i inventory.ini --list
ansible-playbook -i inventory.ini setup_workspace.yml --syntax-check
ansible-playbook -i inventory.ini setup_workspace.yml --check --diff
```

Apply the playbook:

```bash
ansible-playbook -i inventory.ini setup_workspace.yml
```

## Expected result

- ~/it_lab_docs exists as a directory.
- ~/it_lab_docs/network_log.txt exists.
- Existing contents of network_log.txt are preserved.

Verify:

```bash
ls -ld ~/it_lab_docs
ls -l ~/it_lab_docs/network_log.txt
```

## Implementation notes

The playbook uses the gathered environment fact ansible_facts['env']['HOME'] to find the target user's home directory. The copy task creates an empty baseline file only when it is missing.

The cleanup corrected the original HOME lookup and removed touch-based timestamp changes on every run. A fresh Ansible execution and repeat-run check are still needed in the lab environment. No execution output is included in this repository.

## Skills practiced

Ansible inventory, YAML playbooks, gathered facts, directory and file management, and repeatable local configuration.
