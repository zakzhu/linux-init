# Linux-Init

<!-- [![build status][shield-build]][info-build] -->

[![gitter room][shield-gitter]][info-gitter]
[![license][shield-license]][info-license]
[![release][shield-release]][info-release]
[![prs welcome][shield-prs]][info-prs]

> Ansible playbook for linux initialization on cloud environment.

[TOC]

## Requirements

- **Platforms:**
  - CentOS-7
- **Dependencies:**
  - ansible

## Installation

- ```bash
  yum -y install ansible
  ```

- ```bash
  git clone https://github.com/zakzhu/linux-init.git
  ```

## Usage

- ```bash
  cd linux-init
  ```
- ```bash
  vim inventories/staging/host_vars/localhost.yml
  ```

  > ```yaml
  > # EXAMPLE: sys_account_primary_groups variable
  > # sys_account_primary_groups:
  > #   group1:
  > #     name:
  > #     gid:
  > #   group2:
  > #     name:
  > #     gid:
  > #   # ...
  > #sys_account_primary_groups:
  >
  > # EXAMPLE: sys_account_secondary_group variable
  > # sys_account_secondary_groups:
  > #   group1:
  > #     name:
  > #     gid:
  > #   group2:
  > #     name
  > #     gid:
  > #   # ...
  > #sys_account_secondary_groups:
  >
  > # EXAMPLE: sys_account_users variable
  > # sys_account_users:
  > #   user1:
  > #     name:
  > #     comment:
  > #     uid:
  > #     # optionally sets the user's primary group
  > #     primary_group:
  > #     # type: list
  > #     secondary_groups:
  > #     home:
  > #     shell:
  > #     # plain text
  > #     password:
  > #     # type: bool
  > #     needs_generate_ssh_key:
  > #   user2:
  > #     # ...
  > #   # ...
  > #sys_account_users:
  >
  > ascii_banner_company: Your Company
  >
  > chrony_ntp_servers:
  >   - ntp1.aliyun.com
  >   - ntp2.aliyun.com
  >   - time1.cloud.tencent.com
  >   - time2.cloud.tencent.com
  >
  > resolv_nameservers:
  >   - 223.5.5.5
  >   - 223.6.6.6
  >
  > yum_repos_mirrors_hosts:
  >   - "mirrors.aliyun.com"
  >   - "mirrors.cloud.tencent.com"
  >   - "mirrors.huaweicloud.com"
  >   - "mirrors.tuna.tsinghua.edu.cn"
  >   - "mirrors.ustc.edu.cn"
  > ```

- ```bash
  ansible-vault encrypt inventories/staging/host_vars/localhost.yml
  ```

- ```bash
  ansible-playbook --ask-vault-pass -i inventories/staging/hosts.ini site.yml
  ```

## Contributing

See the [contribution guide][info-contribute].

## Frequently asked questions

Please see [FAQ.md][info-faq] for frequently asked questions.

## Thanks

The following excellent people helped massively:

- [Rowan Manning](https://rowanmanning.com)
- [Breeze Yan](https://github.com/yanruogu)
- [Nicolas Brousse](https://www.shell-tips.com/)

## License

Linux-Init is licensed under the [LGPL-2.1][info-license] license.
Copyright &copy; 2020, Zak Zhu

[info-build]: https://travis-ci.org/github/zakzhu/linux-init
[info-contribute]: CONTRIBUTING.md
[info-faq]: FAQ.md
[info-gitter]: https://gitter.im/zakzhu/linux-init
[info-license]: LICENSE
[info-release]: https://github.com/zakzhu/linux-init/releases
[info-prs]: https://github.com/zakzhu/linux-init/pulls
[shield-build]: https://img.shields.io/travis/zakzhu/linux-init
[shield-gitter]: https://img.shields.io/gitter/room/zakzhu/linux-init
[shield-license]: https://img.shields.io/github/license/zakzhu/linux-init
[shield-release]: https://img.shields.io/github/v/release/zakzhu/linux-init
[shield-prs]: https://img.shields.io/badge/PRs-welcome-brightgreen
