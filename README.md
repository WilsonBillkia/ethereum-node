# Ansible playbook for building baremetal geth/lighthouse nodes


This just copies the steps published here https://github.com/remyroy/ethstaker/blob/main/merge-goerli-prater.md. Thanks for an excellent guide!

NB This is configured for goerli - using the flag in the geth.service file in this repo.

NB For validators, DONT FORGET to put your address in the lighthousevalidator.service file where marked. 

(This guide assumes you have ansible installed on a management host, are running the following steps from it, and have an adequately specified linux host with ssh server configured and ready to be the target for the build) 

# Instructions

1. Add the IP address or hostname of the host you want to build to your inventory file (default: /etc/ansible/hosts) under a new group named geth_nodes 

2. Update --suggested-fee-recipient flag in the lighthousevalidator.service file with payment address for validator

3. Run the following `git clone https://github.com/WilsonBillkia/ethereum-node/`

4. Download the latest Lighthouse executable from here https://github.com/sigp/lighthouse/releases and save it as lighthouse under the files directory. 

5. Run `ansible-playbook jwt_token_create.yml` to generate a jwt token and copy it to a world readable location

6. Run `ansible-playbook geth_validator_build.yml` The playbook should perform all the steps necessary to install and enable the geth, beacon and validator services.

7. When tou are ready to move the staking and lighthouse executables to any hosts just use the new playbooks for each and they will transfer across.

