# ansbile-inventarization
![изображение](https://github.com/user-attachments/assets/b9d58f48-7fc6-4de5-b789-de3e86354185)
- name: собираем PC name и IP address
  hosts: hq-scrub hq-clip
  gather_facts: true
  tasks:
   - name: Создаем файл с нужными данными
     сoру:
      dest: /tmp/(( ansible_hostname }.txt
      content:
       Hostname: ansible_hostname }}
       IP Address: ({ ansible_default_ipu4.address
   - name: Забираем файл с удаленного хоста.
     fetch:
       src: /tmp/ff ansible_hostname }.txt
       dest: /root/PC_INFO/
       flat: yes
