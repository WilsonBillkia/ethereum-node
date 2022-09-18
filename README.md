# ethereum-node
An idempotent ansible script to build an ethereum role on Linux.
This is just a compilation of the steps published by remy here https://github.com/remyroy/ethstaker/blob/main/merge-goerli-prater.md

. Set up ansible 

. Add the IP addresses of the hosts you want to build to your ansible inventory  file (default: /etc/ansible/hosts) under a group named geth_node 

. git clone https://github.com/WilsonBillkia/ethereum-node/ && cd ethereum-node

. Download the latest Lighthouse exectuable from here https://github.com/sigp/lighthouse/releases and save it as lighthouse_exe under the files directory. 

. Run ansible-playbook geth_validator_build.yml
