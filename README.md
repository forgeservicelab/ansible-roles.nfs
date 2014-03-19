NFS
===

Sets up a NFS Higly Available cluster based on Heartbeat and DRBD infrastructure.

Requirements
------------

The target machines for this role (exactly 2) must appear on the inventory file grouped under one and only one host group, the `group_names` variable is used to configure HA resources.

This role is a client of the [ha-disk role](https://git.forgeservicelab.fi/ansible-roles/ha-disk), please read the documentation on that role for more information on prerequisites.

Role Variables
--------------

- `heartbeat_service_name` - Name of the service to be managed by heartbeat as it appears on `/etc/init.d`, defaults to `nfs-kernel-server`.
- `OS_FLOATIP` - Floating (Virtual) IP assigned to he HA cluster, read by the [ha-disk role](https://git.forgeservicelab.fi/ansible-roles/ha-disk).
- `ALLOWED_IPS` - **List** of IPs of the machines allowed to mount the NFS share; read from [ha-disk role](https://git.forgeservicelab.fi/ansible-roles/ha-disk). On OpenStack this should be the IP of the public interface on the network router.
- `primary` - Flag that indicates the target host in which to run tasks that only need to be executed in one node. This is expected to be an inventory variable within the host group.


Dependencies
------------

This role is dependent on the following roles, make sure you have made them available to your playbook.
  
- [common role](https://git.forgeservicelab.fi/ansible-roles/common)
- [ha-disk role](https://git.forgeservicelab.fi/ansible-roles/ha-disk)
  
Variables read from other roles:

- `ALLOWED_IPS` - Read from [ha-disk role](https://git.forgeservcelab.fi/ansible-roles/ha-disk) unless overriden.

Author Information
------------------
  
[Forge Servicelab Team](http://forgeservicelab.fi)
