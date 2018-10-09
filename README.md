# LgHS Infra

## Setup

```bash
virtualenv -p python3 .venv
source .venv/bin/activate

pip install -r requirements.txt
```

You will need to run `source .venv/bin/activate` again every time you come back to the repository.


## Provisionning a server

After creating a server, you need to provision it to have access to it with your normal user. To do so, add the server to the inventory and run the following command:

```bash
ANSIBLE_SSH_ARGS="-i ~/.ssh/<root-key>" ansible-playbook -u root playbooks/provision.yml
```

Once this is done, you can run the global role to set it up based on the inventory configuration:

```bash
ansible-playbook -l <new-server> playbooks/global.yml
```
