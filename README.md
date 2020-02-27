# ovirt_ansible_backup
A simple method to export running oVirt VMs to OVA format for backup purposes using Ansible.

Blog post: https://blog.silverorange.com/backing-up-ovirt-vms-with-ansible-4c2fca8b3b43

**Update:** With latest updates, it is now possible to run playbooks from any host without direct access to storage. You must however have pubkey access from the host running ansible to the host specified in the vars inteded for exports.

The CA certificate should be available in the same location specified in playbooks on the oVirt hosted engine VM. It should also be possible to download the CA through via the oVirt admin e.x. https://example.com/ovirt-engine/services/pki-resource?resource=ca-certificate&format=X509-PEM-CA

Fill in the rest of the vars as needed (note: you should only need to make changes in main.yml) and pay special attention to the timeout values, especially if you intend to export large VMs.

Run the playbook using `ansible-playbook main.yml` -- add a crontab entry to automate the process.

## Relevant Ansible modules used:

* https://docs.ansible.com/ansible/latest/modules/ovirt_vm_module.html
* https://docs.ansible.com/ansible/latest/modules/ovirt_auth_module.html
* https://docs.ansible.com/ansible/latest/modules/ovirt_event_info_module.html
* https://docs.ansible.com/ansible/latest/modules/ovirt_host_info_module.htm
* https://docs.ansible.com/ansible/latest/modules/shell_module.html
