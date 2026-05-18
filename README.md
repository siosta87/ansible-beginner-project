# Ansible Beginner Project

A beginner-level Ansible project focused on automating IT lab setup on a local Linux machine (WSL/Ubuntu).

## What This Project Does

This playbook automates the creation of a basic IT lab directory structure and a blank network baseline log file on localhost.

## Files

- `inventory.ini` — Defines localhost as the target host using a local connection
- `setup_workspace.yml` — Ansible playbook that creates the `it_lab_docs/` directory and a blank `network_log.txt` file inside it

## How to Run

```bash
ansible-playbook -i inventory.ini setup_workspace.yml
```

## What Gets Created

```
~/it_lab_docs/
└── network_log.txt
```

## Skills Practiced

- Writing an Ansible inventory file
- Creating a basic playbook with tasks
- Using the `file` module to create directories and files
- Running a playbook locally with `ansible_connection=local`
- Debugging and fixing YAML syntax errors
