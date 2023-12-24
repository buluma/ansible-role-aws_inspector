# [Ansible role aws_inspector](#aws_inspector)

AWS Inspector installation for Linux.

|GitHub|Version|Issues|Pull Requests|
|------|-------|------|-------------|
|[![github](https://github.com/buluma/ansible-role-aws_inspector/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-aws_inspector/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-aws_inspector.svg)](https://github.com/buluma/ansible-role-aws_inspector/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-aws_inspector.svg)](https://github.com/buluma/ansible-role-aws_inspector/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-aws_inspector.svg)](https://github.com/buluma/ansible-role-aws_inspector/pulls/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-aws_inspector/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  vars:
    aws_inspector_role_test_mode: true

  pre_tasks:
    - name: Update apt cache
      apt: update_cache=yes cache_valid_time=600
      when: ansible_os_family == 'Debian'
      changed_when: false
  tasks:
    - name: "Include buluma.aws_inspector"
      ansible.builtin.include_role:
        name: "buluma.aws_inspector"
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-aws_inspector/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - role: buluma.bootstrap
    - role: buluma.ca_certificates
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-aws_inspector/blob/master/defaults/main.yml):

```yaml
---
# defaults file for aws_inspector

aws_inspector_url: "https://inspector-agent.amazonaws.com/linux/latest/install"
aws_inspector_installer_dest: /tmp/aws_inspector_agent_installer

awsagent_state: started
awsagent_enabled: true

aws_inspector_role_test_mode: false

aws_inspector_proxy_enabled: false
aws_inspector_https_proxy: 127.0.0.1:8080
aws_inspector_http_proxy: 127.0.0.1:8080
aws_inspector_no_proxy: 169.254.169.254
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-aws_inspector/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | Version |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Ansible Molecule](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-bootstrap.svg)](https://github.com/shadowwalker/ansible-role-bootstrap)|
|[buluma.ca_certificates](https://galaxy.ansible.com/buluma/ca_certificates)|[![Ansible Molecule](https://github.com/buluma/ansible-role-ca_certificates/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-ca_certificates/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-ca_certificates.svg)](https://github.com/shadowwalker/ansible-role-ca_certificates)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-aws_inspector/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[EL](https://hub.docker.com/repository/docker/buluma/enterpriselinux/general)|all|
|[Debian](https://hub.docker.com/repository/docker/buluma/debian/general)|all|
|[Ubuntu](https://hub.docker.com/repository/docker/buluma/ubuntu/general)|all|

The minimum version of Ansible required is 2.12, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-aws_inspector/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-aws_inspector/blob/master/CHANGELOG.md)

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-aws_inspector/blob/master/LICENSE).

## [Author Information](#author-information)

[buluma](https://buluma.github.io/)


### [Special Thanks](#special-thanks)

Template inspired by [Robert de Bock](https://github.com/robertdebock)
