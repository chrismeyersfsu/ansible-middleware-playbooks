# ansible-middleware-playbooks

## Purpose

This repository provides a set of generic roles and reusable playbooks for deploying JBoss Middleware and associated CI / CD tooling.

## Getting Started

1. Update group_vars/all/all.yml to reflect your environment
2. Update inventory.yml to reflect your environment
3. Clone the [JBoss EAP Role](https://github.com/rhtconsulting/jboss_eap) into your [Ansible Roles Path](http://docs.ansible.com/ansible/intro_configuration.html#roles-path). Future version will support galaxy to make this easier.
4. TODO: ansible-galaxy install

Transfer Methods
----------

These playbooks and their required roles support a few different mechanisms for transferring the product zip files to the target host. You can set the variable `transfer_method` to select the method, which can be set at multiple levels. The default is set in [group vars](https://github.com/rhtconsulting/ansible-middleware-playbooks/blob/master/group_vars/all/all.yml).

### csp-to-host
This method uses the [custom redhat_csp_download module](library/redhat_csp_download.py) to download the product binaries from the [Red Hat Customer Portal](https://access.redhat.com/downloads/). This requires network access from the target host to the Red Hat Customer Portal, but has the advantage of being fully automated. Each of the roles have sensible defaults already set.

The following variables are required:
- `rhn_username`
- `rhn_password`

### copy-from-controller
This method requires you to download the product binaries from the [Red Hat Customer Portal](https://access.redhat.com/downloads/) and then add them to the files directory. This has the benefit of supporting installs when the target host does have public internet connectivity, but requires a manual step before the playbook can be run. Each of the roles have sensible defaults already set, and the .gitignore will ignore .zip files.

## Red Hat Subscriptions

These playbooks require binaries from the [Red Hat Customer Portal](https://access.redhat.com/downloads/), so you'll need a valid subscription. Developers can get a $0 subscription through the [Red Hat Developer Program](http://developers.redhat.com/products/eap/download/).

## Roles Used By These Playbooks

1. [JBoss EAP](https://github.com/rhtconsulting/jboss_eap)
2. [JBoss BxMS](https://github.com/rhtconsulting/jboss_bxms)

## Best Practices

We're following the [OpenShift Ansible Best Practices](https://github.com/openshift/openshift-ansible/blob/master/docs/best_practices_guide.adoc)

## Relevant Links

[Ansible roles](http://docs.ansible.com/ansible/playbooks_roles.html "Ansible Roles")
