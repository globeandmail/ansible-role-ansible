# ansible-role-ansible
Install Ansible itself on Ubuntu target host(s), in a python virtual environment.

#### This role will install the dependency 'python3-minimal' and use Python3.5 for the venvs.

#### Please note that you must specify the tag "infra" in order for this playbook to do anything.

To update an ansible installation, specify ansible_inst_state=forcereinstall

Default Variables
-----------------
    ansible_inst_ver: "2.9"
    ansible_inst_path: "~/venvs/ansible-{{ansible_inst_ver}}"
    ansible_venv_python: "python3.5"
    ansible_inst_state: "present"

Example Playbook for Applying/Installing Multiple Instances of Ansible
----------------------------------------------------------------------
    - hosts: all
      become: yes
      roles:
      - { role: ansible-role-ansible, ansible_inst_ver: ">=2.9,<2.10", ansible_inst_path="~/venvs/ansible-2.9" }
      - { role: ansible-role-ansible, ansible_inst_ver: ">=2.8,<2.9", ansible_inst_path="~/venvs/ansible-2.8", ansible_inst_state: "forcereinstall" }
