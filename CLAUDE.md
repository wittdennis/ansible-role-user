# Ansible

- only set `become: true` on a task if it actually fails without it; do not add it defensively or by copying it onto neighboring tasks
