# ansible_jenkins
Collection of Playbooks for server patching and configuration management across applications and databases

USERKEYS.YML

This playbook creates a jenkins user on the remote servers with full sudo access by copying over related public key in order to allow operational jobs from a centralized jenkins server configured with the Ansible plugin:

Jenkins ansible plugins info:
https://wiki.jenkins.io/display/JENKINS/Ansible+Plugin

PATCHING_PLAYBOOK.YML

This playbook will take care to patch the RedHat/CentOS hosts called by ansible running 4 of the following tasks:

TASK 1 : Check and make sure that the RedHat systems only are subscribed with RHN

TASK 2 : Apply all the security and bug-fix patches only omitting 3rd party repos

TASK 3 : Reboot the servers

TASK 4 : Wait for the servers to come back up after the reboot (SSH connection) within 400 seconds and exit

NOTE Ansible will run the playbook as the Jenkins user, which is the user that Jenkins is running as.

JENKINS_LOCAL_PATCH.YML

Will take care to upgrade the Jenkins server itself.
Ansible Has to run with the -c local option.
On the jenkins job has to be set in the Additional parameters section under the ansible configuration 
