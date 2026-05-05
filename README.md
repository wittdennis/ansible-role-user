# User

Ansible role to manage a user and its public key.

## Requirements

None.

## Role Variables

| name                   | description                                                                                                                                                                                              | mandatory | default       |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------: | ------------- |
| user_login             | Login of the user                                                                                                                                                                                        |     X     | `""`          |
| user_password_hash     | Password hash for the user. Look [here](https://docs.ansible.com/ansible/latest/reference_appendices/faq.html#how-do-i-generate-encrypted-passwords-for-the-user-module) for a guide how to create this. |     X     | `""`          |
| user_public_key_file   | File path to the public ssh key for the user                                                                                                                                                             |     X     | `""`          |
| user_sudo_superuser    | User ability to sudo as the superuser                                                                                                                                                                    |           | `false`       |
| user_shell             | Default shell of the user                                                                                                                                                                                |           | `"/bin/bash"` |
| user_comment           | Comment for the user                                                                                                                                                                                     |           | `""`          |
| user_additional_groups | List of additional groups the user should be added to                                                                                                                                                    |           | `[]`          |

## Dependencies

None.

## Example Playbook

```yaml
# Create a normal user
- hosts: servers
  roles:
      - role: wittdennis.user
        vars:
        user_login: "myuser",
        user_password_hash: "password_hash",
        user_public_key_file: "~/.ssh/id_ed25519.pub"

# Create an user with sudo rights and custom shell
- hosts: servers
  roles:
      - role: wittdennis.user
        vars:
        user_login: "myuser",
        user_password_hash: "password_hash",
        user_public_key_file: "~/.ssh/id_ed25519.pub"
        user_sudo_superuser: true
        user_shell: "/bin/zsh"
```

## License

MIT
