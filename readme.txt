By default, Ansible will try to manage all of the machines referenced in a play in parallel. For a rolling update use case, you can define how many hosts Ansible should manage at a single time by using the serial keyword:
---
- name: test play
  hosts: webservers
  serial: 2
  gather_facts: False

  tasks:
    - name: task one
      command: hostname
    - name: task two
      command: hostname
In the above example, if we had 4 hosts in the group ‘webservers’, 2 would complete the play completely before moving on to the next 2 hosts:
  serial: "30%"
    max_fail_percentage: 30   
===========


ansible-playbook -i host.inv site.yml -t vmtag -K --check --step



