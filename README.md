# ansbile-inventarization

- name: собираем PC name и IP address
  hosts: hq-srv hq-cli
  gather_facts: true
  tasks:
   - name: Создаем файл с нужными данными
     сoру:
      dest: /tmp/{{ ansible_hostname }}.txt
      content: |
       Hostname:{{ ansible_hostname }}
       IP Address: ({ ansible_default_ipv4.address }}
   - name: Забираем файл с удаленного хоста.
     fetch:
       src: /tmp/{{ ansible_hostname }}.txt
       dest: /root/PC_INFO/
       flat: yes
