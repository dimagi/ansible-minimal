# ansible-minimal

Basic ansible deployment for non-hq machines.

## Usage example:

The following will bootstrap a set of dimagi users on a new machine.

**Create enviroment files**

See `environments/emm` for examples.

**Setup ansible user password**

First choose a password. Then generate a sha-512 hash:

```
mkpasswd -m sha-512 [my secret password]
```


Next put this password hash in your environment (make sure to keep the quotes!):

```
export ANSIBLE_HASH='[output of previous command]'
```

**Finally, run the bootstrap command**

You should replace the references to the `emm` environment with the files you created.

```
ansible-playbook -u root --ask-pass --extra-vars="ansible_user_password_sha_512=$ANSIBLE_HASH" -i environments/emm/inventory.ini -e @environments/emm/public.yml bootstrap.yml --diff
```

After ansible user has been setup:

```
ansible-playbook -u ansible --ask-become-pass -i environments/emm/inventory.ini -e @environments/emm/public.yml bootstrap.yml --diff
```
