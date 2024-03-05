User
=========

Ansible role to manage a user and its public key.

Requirements
------------

None.

Role Variables
--------------

| name                  | description                                                                                                                                                                                              | mandatory | default       |
| --------------------  | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------: | ------------- |
| user__login           | Login of the user                                                                                                                                                                                        |     X     | `""`          |
| user__password_hash   | Password hash for the user. Look [here](https://docs.ansible.com/ansible/latest/reference_appendices/faq.html#how-do-i-generate-encrypted-passwords-for-the-user-module) for a guide how to create this. |     X     | `""`          |
| user__public_key_file | File path to the public ssh key for the user                                                                                                                                                             |     X     | `""`          |
| user__sudo_superuser  | User ability to sudo as the superuser                                                                                                                                                                    |           | `false`       |
| user__shell           | Default shell of the user                                                                                                                                                                                |           | `"/bin/bash"` |
| user__comment         | Comment for the user                                                                                                                                                                                     |           | `""`          |

Dependencies
------------

None.

Example Playbook
----------------

```yaml
# Create a normal user
- hosts: servers
  roles:
      - role: wittdennis.user
        vars:
        user__login: "myuser", 
        user__password_hash: "password_hash", 
        user__public_key_file: "~/.ssh/id_ed25519.pub"

# Create an user with sudo rights and custom shell
- hosts: servers
  roles:
      - role: wittdennis.user
        vars:
        user__login: "myuser", 
        user__password_hash: "password_hash", 
        user__public_key_file: "~/.ssh/id_ed25519.pub"
        user__sudo_superuser: true
        user__shell: "/bin/zsh"
```

License
-------

MIT
