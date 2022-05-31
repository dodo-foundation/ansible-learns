#### ansible-glt-clone-playbook

---

```yml
# file name = clone.yml
---
- name: ansible playbooks
  hosts: all
  vars:
    GIT_USERNAME: "fourtimes"
    GIT_TOKEN: "ghp_ZJZ1uTvI9SBytt42nMxxxxxxxxxxx"
    DESTINATIN: "/tmp/github"
    BRANCH_NAME: "dev"
  tasks:
    - name: Get updated files from git repository
      git: 
        repo: https://{{ GIT_USERNAME }}:{{ GIT_TOKEN }}@github.com/FourTimes/dummy.git
        dest: "{{ DESTINATIN }}"
        single_branch: yes
        version: "{{ BRANCH_NAME }}"

```

_execution_

```bash

ansible-playbook clone.yml

```
