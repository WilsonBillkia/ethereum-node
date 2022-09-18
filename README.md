# ethereum-node
An idempotent ansible script to build an ethereum role on Linux.

This is just a compilation of the steps published here https://github.com/remyroy/ethstaker/blob/main/merge-goerli-prater.md

NB This is configured for goerli - for other networks change the flag in the geth.service file in this repo.

NB For validators, dont forget to put your address in the lighthousevalidator.service file where marked. 

(This guide assumes you have ansible installed, are running the following steps from your management host, and have a suitable host ready and communicating with your management node using ssh) 

# Instructions

1. Add the IP address of the host you want to build to your ansible inventory file (default: /etc/ansible/hosts) under a group named geth_node 

2. Run the following 'git clone https://github.com/WilsonBillkia/ethereum-node/ && cd ethereum-node'

3. Download the latest Lighthouse exectuable from here https://github.com/sigp/lighthouse/releases and save it as lighthouse_exe under the files directory. 

4. Run ansible-playbook geth_validator_build.yml

The node should perform all the steps necessary to build the geth node and enable the geth, beacon and validator services. For non-validator nodes just leave out any steps which reference the validator from the main playbook.
