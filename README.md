# Ansible playbook for building baremetal geth/lighthouse nodes


This program copies the steps published here https://github.com/remyroy/ethstaker/blob/main/merge-goerli-prater.md. Thanks for an excellent guide!

NB This is configured for goerli - using the flag in the geth.service file in this repo.

NB For validators, your address goes in the lighthousevalidator.service file where marked. 

(This guide assumes you have ansible installed, a suitable linux host with ssh server ready to be the target for the build) 

# Instructions

1. Clone this repo and cd into it

2. Add the hosts you want to turn into geth nodes to your ansible inventory file (default: /etc/ansible/hosts) under a group named geth. Use the vars in the example testinv.yml for reference 

3. Put payment address for validator in --suggested-fee-recipient flag in the lighthousevalidator.service file

4. Download the Lighthouse executable (https://github.com/sigp/lighthouse/releases) and save it as lighthouse_archive.gz under files 

5. Move the staking and lighthouse executables to geth hosts with copy_executable.yml and copy_staking_cli.yml

6. Run `ansible-playbook geth_build.yml` The playbook installs the dependencies, then geth, then sets up geth, beacon and validator services under Systemd.

7. Run `ansible-playbook jwt_token_create.yml` to generate a jwt token and copy it to a world readable location

NB There are tools for node backup included: backup_nodes.yml fetches any keys for the configured chain (eth_chain_id) and toml configs off each geth host. create_toml dumps toml configs on each geth host then copies them back to the management host, using ansible fetch. 
