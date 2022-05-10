redhat rpm-package-query.md

```yml
---
# version-finder.yml
- name: Package versions findings
  hosts: all
  tasks:
  - name: GET INPUT VERSIONS
    debug:
      msg: "Expects 1 arguments"
    when: packages is not defined
  - name: GET PACKAGE VERSIONS
    shell: "rpm -qa {{ item }}"
    loop: 
      - "{{ packages }}"
    register: _version_details
    when: packages is defined
  - name: PRINT THE PACKAGE VERSIONS
    debug:
      msg: "{{ _version_details.results | json_query('[].stdout_lines[]') }}"
    when: packages is defined
```

Execution command

```bash
ansible-playbook version-finder.yml -e packages=httpd
```
