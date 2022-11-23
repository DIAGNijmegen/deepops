Example DeepOps configuration
=============================

This directory provides an example configuration for NVIDIA DeepOps.
The files in this directory will help determine the behavior of the Ansible playbooks and other scripts that DeepOps uses to set up your systems.

For more details on how this works, see [how to configure DeepOps](../docs/deepops/configuration.md).

Configuring Deepops for SOL
============================
To configure Deepops for the SOL cluster   
* Git clone the deepops-sol-config and deepops repositories from Github
* Copy and paste the config folder into the deepops folder and rename it to config, since all commands should be run from within the deepops folder, and assumes the config is within this directory. If not, then the inventory file will have to be specified using the -i flag in the ansible commands. 
* Follow the steps from https://github.com/NVIDIA/deepops/tree/master/docs/slurm-cluster to set up the virtual environment and deploy the deepops cluster on the nodes. Additionally, you might need to add -k, -K, and/or -i flags within the ansible commands to specify ssh/sudo passwords and the location of the inventory, respectively. 

Configuring the mounts for SOL
==============================
To mount the drives from Blissey and Chansey onto the machines, simply run the mounts.yml playbook from the config's playbook folder (config/playbooks/mounts.yml) using the following command:

``` 
ansible-playbook config/playbooks/mounts.yml -k --ask-vault-pass 
``` 

Or, if you need to specifiy only an exact list of nodes, run:
```ansible
ansible-playbook config/playbooks/mounts.yml -k --ask-vault-pass -l <nodename_1,nodename_2,...>
where nodename is the node or nodes in question