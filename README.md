Role Name
=========

[![Build Status](https://travis-ci.org/cans/pip-config.svg?branch=master)](https://travis-ci.org/cans/pip-config)

Ansible Role to setup pip to access private package indices and other
Python package sources


Requirements
------------

This role has the requirements of Ansible's
[template](http://docs.ansible.com/ansible/template_module.html) module.


Role Variables
--------------

This role variables are namespaced using the `pip_config_` prefix.

- `pip_config_dir`: the directory in which install pip's configuration
  file (default: `~/.pip/`);
- `pip_config_extra_index_urls`: the list of extra PyPI index you want
  pip to look for packages from (default: `[]`).
- `pip_config_file`: the name to give to pip configuration file
  (default: `pip.conf`);
- `pip_config_find_links_urls`: the list of extra web resources pip
  should scan for links to Python packages (default: `[]`);
- `pip_config_timeout`: the duration in seconds pip will wait for any
  package index to respond before droping the connexion and try with
  the next (default: 10).

You most likely do not need to modify the value of the `pip_config_dir`
and `pip_config_file` variables. But since pip supports many locations
for its configuration, these allow you to do it if you fancy it.

The `pip_config_timeout` variable you may want to adjust depending on
where are stored the packages you need. The lower the value, the less
you wait, but the higher the risk of unexpected failures.


Dependencies
------------

This role has no dependencies.


Example Playbook
----------------

    - hosts: servers
      vars:
        pip_config_extra_index_urls:
          - https://my-pypi.domain.com/simple
        pip_config_find_links_urls:
          - https://my.domain.com/packages.html
           
      roles:
         - { role: "cans.pip-config" }


License
-------

The Ansible role pip-config is free software: you can redistribute it
and/or modify it under the terms of the GNU General Public License
version 2 as published by the Free Software Foundation.

pip-config is distributed in the hope that it will be useful, but
WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with cans.package-sources. If not, see <http://www.gnu.org/licenses/>.


Author Information
------------------

Copyright © 2017, Nicolas CANIART
