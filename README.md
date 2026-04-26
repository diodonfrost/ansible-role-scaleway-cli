ansible-role-scaleway-cli
=============

Ansible role to install the latest version of the Scaleway CLI ([scaleway-cli](https://github.com/scaleway/scaleway-cli))

Requirements
------------

This role requires:
- Ansible 2.10 or higher
- Python 3.x
- Internet access to download Scaleway CLI from GitHub releases

Role Variables
--------------

The following variables are available:

| Variable | Description | Default |
|----------|-------------|---------|
| `scaleway_cli_version` | Version of Scaleway CLI to install. Use 'latest' for the most recent version or specify a version like 'v2.55.0' | `latest` |
| `scaleway_cli_path` | Directory where the `scw` binary will be installed | `{{ _scaleway_cli_default_path }}` |
| `scaleway_cli_pkg_url` | Full URL to the Scaleway CLI binary to download | `{{ _scaleway_cli_default_pkg_url }}` |
| `scaleway_cli_checksum_verify` | Whether to verify the SHA256 checksum of the downloaded binary | `true` |
| `scaleway_cli_checksum_url` | Full URL to the Scaleway CLI SHA256SUMS file used to verify the downloaded binary | `{{ _scaleway_cli_default_checksum_url }}` |

Dependencies
------------

This role has no dependencies on other roles.

Example Playbook
----------------

Basic usage:

```yaml
- hosts: servers
  roles:
    - role: diodonfrost.scaleway_cli
```

With custom version:

```yaml
- hosts: servers
  roles:
    - role: diodonfrost.scaleway_cli
      vars:
        scaleway_cli_version: "v2.55.0"
```

With custom installation path:

```yaml
- hosts: servers
  roles:
    - role: diodonfrost.scaleway_cli
      vars:
        scaleway_cli_path: "/opt/scaleway-cli/bin"
```

Local Testing
-------------

This project uses [Molecule](http://molecule.readthedocs.io/) to aid in the
development and testing.

To develop or test you'll need to have installed the following:

* Linux (e.g. [Ubuntu](http://www.ubuntu.com/))
* [Docker](https://www.docker.com/)
* [Python](https://www.python.org/) (including python-pip)
* [Ansible](https://www.ansible.com/)
* [Molecule](http://molecule.readthedocs.io/)
* [Libvirt](https://libvirt.org/) (If you test a system other than Linux)
* [Vagrant](https://www.vagrantup.com/downloads.html) (If you test a system other than Linux)

Testing with Docker
-------------------

```shell
# Install requirements
pip install -r requirements-dev.txt

# Test ansible role with ubuntu 24.04
molecule test

# Test ansible role with ubuntu 22.04
image=ansible-ubuntu:22.04 molecule test

# Test ansible role with alpine latest
image=ansible-alpine:latest molecule test
```

Testing with Vagrant and Libvirt
--------------------------------

```shell
# Test ansible role with FreeBSD
molecule test -s freebsd

# Test ansible role with Windows
molecule test -s windows
```

License
-------

Apache Software License 2.0

Author Information
------------------

This role was created in 2026 by diodonfrost.
