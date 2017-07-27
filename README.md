# ansible-minimal
basic ansible deployment for non-hq machines

Usage example:

```
ansible-playbook --extra-vars="ansible_user_password_sha_512=$ANSIBLE_HASH" -u root --ask-pass --diff -i 192.168.1.2, bootstrap.yml
```

After ansible user has been setup:

```
ansible-playbook -u ansible --ask-become-pass --diff --extra-vars="ansible_user_password_sha_512=$ANSIBLE_HASH" -i 192.168.1.2, bootstrap.yml
```
