Ansible Role: apache\_exporter
==========================

[![Build Status](https://travis-ci.org/atosatto/ansible-apache_exporter.svg?branch=master)](https://travis-ci.org/atosatto/ansible-apache_exporter)
[![Galaxy](https://img.shields.io/badge/galaxy-atosatto.apache_exporter-blue.svg?style=flat-square)](https://galaxy.ansible.com/atosatto/apache_exporter)

Install and configure Prometheus apache\_exporter.

Requirements
------------

An Ansible 2.2 or higher installation.<br />
This role makes use of the Ansible `json_filter` that requires `jmespath` to be installed on the Ansible machine.
See the `requirements.txt` file for further details on the specific version of `jmespath` required by the role.

Role Variables
--------------

Available variables are listed below, along with default values (see defaults/main.yml):

    apache_exporter_release_tag: "latest"

The apache\_exporter release to be installed.
By default, the latest release published at https://github.com/prometheus/apache\_exporter/releases.

    apache_exporter_release_url: ""

If set, the role will download apache-exporter from the provided URL instead of using the download URL indicated in the apache\_exporter Github release metadata.

    apache_exporter_user: "apache_exporter"
    apache_exporter_group: "apache_exporter"

apache\_exporter system user and group.

    apache_exporter_install_path: "/opt"

Directory containing the downloaded apache\_exporter release artifacts.

    apache_exporter_bin_path: "/usr/local/bin"

Directory to which the apache\_exporter binaries will be symlinked.

    apache_exporter_listen_address: "127.0.0.1:9100"

The apache\_exporter WebServer listen ip address and port.<br/>
**NOTE**: the apache\_exporter metrics will be available at `{{ apache_exporter_listen_address }}/metrics`.

    apache_exporter_log_level: "info"

apache\_exporter logs verbosity level.

    apache_exporter_additional_cli_args: ""

Additional command-line arguments to be added to the apache\_exporter service unit.
For the complete refence of the available CLI arguments please refer to the output
of the `apache_exporter --help` command.

Dependencies
------------

None.

Example Playbooks
-----------------

    $ cat playbook.yml
    - name: "Install and configure Prometheus apache_exporter"
      hosts: all
      roles:
        - { role: atosatto.apache_exporter }

Testing
-------

Tests are automated with [Molecule](http://molecule.readthedocs.org/en/latest/).

    $ pip install tox

To test all the scenarios run

    $ tox

To run a custom molecule command

    $ tox -e py27-ansible29 -- molecule test -s apache_exporter-latest

License
-------

MIT

Author Information
------------------

Andrea Tosatto ([@\_hilbert\_](https://twitter.com/_hilbert_))
