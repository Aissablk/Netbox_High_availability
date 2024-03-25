# Playbook: PostgreSQL, pgpool, and Netbox Deployment
## Descriptions
This Ansible playbook automates the deployment and configuration of PostgreSQL, pgpool, and Netbox on multiple nodes. It assumes a CentOS/RHEL 8 environment.
The playbook is divided into multiple plays, each responsible for specific tasks.


- The first play installs and configures PostgreSQL on standby_nodes and primary_nodes.


- The second play sets up PostgreSQL clusters on primary_nodes.


- The third play configures PostgreSQL Standby nodes for replication.

- The fourth play installs pgpool on pgpool1.


- The fifth play installs and configures Netbox on netbox hosts.


- Ensure that appropriate SSH keys are set up for passwordless authentication between host.

## Prerequisites

- **Ansible**: Installed on the control machine 2.10 Version.
- **SSH Access**: Access to target hosts via SSH.
- **Privileged Access**: Root or sudo access to execute privileged tasks and other required acess.



**Before running the playbook**, ensure that all of these requirements are satisfied :


- PostgreSQL is not installed on any of the four VMs.
- The wget package is not installed on Pgpool VM.
- postgresql-devel, make, @development, gcc, and gcc-c++ packages not installed on pgpool VM.
- The following packages are not installed on netbox VM:
  
   gcc, libxml2-devel, libxslt-devel, libffi-devel, libpq-devel, openssl-devel, redhat-rpm-config, python38, python38-pip, python3-virtualenv, python38-devel.
-  Netbox VM is not be updated.
- The policycoreutils package needs to be present on netbox VM . 



## Usage

1. **Clone Repository**: Clone this repository to your local machine:

    ```bash
    git clone "https://github.com/your_repository.git"
    cd your_repository
    ```

2. **Edit iventory file**: Edit the `inv.yml` file to include the IP addresses or hostnames of your target nodes under appropriate groups (`standby_nodes`, `primary_nodes`, `pgpool1`, `netbox`, etc.).

3. **Customize Variables**: Customize variables in the playbook according to your environment. The variables are defined in the playbook itself.

4. **Execute Playbook**: Execute the playbook using the following command:

    ```bash
    ansible-playbook -i inv.yml play.yml 
    ```
5. **testing**: put this adress on ur browser https://IP_ADRESS_NETBOX_VM:443 





