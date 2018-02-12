cans.pip-configure
==================

[![Build Status](https://travis-ci.org/cans/pip-configure.svg?branch=master)](https://travis-ci.org/cans/pip-configure)
[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-cans.pip--configure-blue.svg?style=flat-square)](https://galaxy.ansible.com/cans/pip-configure)
[![License](https://img.shields.io/badge/license-GPLv2-brightgreen.svg?style=flat-square)](LICENSE)

Ansible Role to setup pip to access private package indices and other
Python package sources


Requirements
------------

This role has the requirements of Ansible's
[template](http://docs.ansible.com/ansible/template_module.html) module.


Role Variables
--------------

This role variables are namespaced using the `pip_config_` prefix.


### Default variables

- `pipconfig_dir`: the directory in which install pip's configuration
  file. Make sure it is in a safe place, see comment on `pip_config_dir`
  item below. (default: `~/.pip/`);
- `pipconfig_dir_mode`: the mode to set on the `pip_config_dir`
  directory. This it will contain a file that points you to different
  network locations, you should make to not leave yourself open to
  some misdirecting you by replacing its content with malicious one.
  Only you and the root usr should be able to write in it or any of its
  parents (defaults: 0500);
- `pipconfig_file`: the name to give to pip configuration file
  (default: `pip.conf`);
- `pipconfig_file_mode`: the mode to set on the `pip_config_file` file.
  Be mindful that you may need to put credentials in it. Tightening the
  permission is recommanded (default: 0400);
- `pipconfig_timeout`: the duration in seconds pip will wait for any
  package index to respond before droping the connexion and try with
  the next (default: 10).

You most likely do not need to modify the value of the `pip_config_dir`
and `pip_config_file` variables. But since pip supports many locations
for its configuration, these allow you to do it if you fancy it.

The `pipconfig_timeout` variable you may want to adjust depending on
where are stored the packages you need. The lower the value, the less
you wait, but the higher the risk of unexpected failures.


### Input variables

This are the variables you need to set for the role to actuall do
something, useful:

- `pipconfig_extra_index_urls`: the list of extra PyPI index you want
  pip to look for packages from (default: `[]`).
- `pipconfig_find_links_urls`: the list of extra web resources pip
  should scan for links to Python packages (default: `[]`);

You can define either or both of them.


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
