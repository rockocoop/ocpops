# ocpops




Repository for OCP operations


## Project Creation Template ##
### To disable the option for user to create projects:

https://docs.openshift.com/container-platform/4.6/applications/projects/configuring-project-creation.html#disabling-project-self-provisioning_configuring-project-creation


### Playbook for creating a project with the following objects included:
- Default node-selector
- Limit Ranges


## Cluster Resource Quota ##
Template for creating CRQ


## Role for CRQ management ##
A role that you can give to a user so they can do the following:
- View their CRQ
- Edit the RQ on all projects they have admin rights on
