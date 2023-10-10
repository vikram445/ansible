---
- name: Install Multiple Packages
  hosts: localhost
  become: yes
  tasks:
     
    - name: Install Multiple Packages
      apt:
        update_cache: yes
        name:
          - mysql-server
          - openjdk-11-jdk
          - tomcat9
          - maven
        state: present
![image](https://github.com/vikram445/ansible/assets/79625874/b89b69c4-1b27-4321-bd80-74e48cc7230f)

    - name: Clone repository
      git:
        repo: https://github.com/opstree/spring3hibernate
        dest: /home/ubuntu/spring3hibernate

![image](https://github.com/vikram445/ansible/assets/79625874/881f75cf-ac01-4050-ae63-a7d7f87e629f)

       
    - name: Generate war  file
      shell: 
        chdir: /home/ubuntu/spring3hibernate
        cmd: "mvn clean install"

![image](https://github.com/vikram445/ansible/assets/79625874/3c2e1b6e-9f4c-4ef1-a31c-728f87dd99e7)

        

    - name: Restart Tomcat service
      service:
        name: tomcat9
        state: restarted
