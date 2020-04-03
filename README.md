# LgHS Infra

## Setup

You need to update your local SSH config since the public DNS are actually CloudFlare proxies without the port 22 open. Ask an admin if you need them.

```sh
Host <inventory-name>
    User <user>
    HostName <server-ip>
    IdentityFile <server-key>
```

We use pipenv to prevent you from having the wrong dependency versions, you can initialise it with this command:
```bash
pipenv install
```

You will need to run `pipenv shell` every time you come back to the repository.


## Provisioning a server

After creating a server, you need to provision it to have access to it with your normal user. To do so, add the server to the inventory and run the following command:

```bash
ANSIBLE_SSH_ARGS="-i ~/.ssh/<root-key>" ansible-playbook -u root -l <new-server> playbooks/provision.yml
```

Once this is done, you can run the global role to set it up based on the inventory configuration:

```bash
ansible-playbook -l <new-server> playbooks/global.yml
```
