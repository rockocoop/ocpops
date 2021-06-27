# ocpops




Repository for OCP operations


## Project Creation Template ##
### To disable the option for user to create projects:

https://docs.openshift.com/container-platform/4.6/applications/projects/configuring-project-creation.html#disabling-project-self-provisioning_configuring-project-creation


### Playbook createproj.yaml ###
- Create ClusterResourceQuota
- Create Projects
- Limit Ranges
- Add admin role to group on created projects

Update inventory file and then run from bastion:

```
ansible-playbook -i ../inventories/inventory createproj.yaml 
```

## Role for CRQ management ##

### ocproles/resourcequota.yaml ###

- gives the user or group when assigned the ability to create, edit and delete resource quotas on the assigned project

#### add to cluster ####
```
oc apply -f ocproles/resourcequota.yaml
```

#### give permission to user ####
```
oc adm policy add-role-to-user managerq {username} -n {project}
```

#### give permission to group ####
```
oc adm policy add-role-to-group managerq {groupname} -n {project}
```


### ocproles/clusterresourcerole.yaml ###

- Allow user or group to view the clusterresourcequotas

#### add to cluster ####
```
oc apply -f ocproles/clusterresourcequota.yaml
```

#### give permission to user ####
```
oc adm policy add-cluster-role-to-user managerq {username}
```

#### give permission to group ####
```
oc adm policy add-cluster-role-to-group managerq {groupname}
```

