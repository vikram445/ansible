ANSIBLE ASSIGNMENT-1

UserManager:

1. Create a group:
   
   ansible server1 -m group -a "name=team1"

      ![Screenshot from 2023-10-09 23-20-24](https://github.com/vikram445/ansible/assets/79625874/4b70ddfe-6f07-498d-953d-deeaff736dee)


2. Add the user Nitish to the team1 group and create the home directory:

   ansible server1 -m user -a "name=Nitish group=team1 createhome=yes"

     ![image](https://github.com/vikram445/ansible/assets/79625874/1dc4dc26-5776-40c5-b1e5-bf41df6bd257)


3. Ensure the user Nitish has read, write, and execute access to the home directory:

   ansible server1 -m file -a "path=/home/Nitish owner=Nitish group=team1 mode=0755"

     ![image](https://github.com/vikram445/ansible/assets/79625874/ce091ac4-8c0f-466a-b32e-c820ec6c407a)



5. Ensure that all users of the same team have read and execute access to the home directory of fellow team members:

   # For the 'team' directory

   ansible server1 -m file -a "path=/home/Nitish/team owner=Nitish group=team1 mode=0770 state=directory"

     ![image](https://github.com/vikram445/ansible/assets/79625874/6da23d56-7418-4a9c-9970-ea4ff478faae)


   # For the 'ninja' directory

   ansible server1 -m file -a "path=/home/Nitish/ninja owner=Nitish group=team1 mode=0777 state=directory"

     ![image](https://github.com/vikram445/ansible/assets/79625874/638e7d89-ad9b-4992-a5fb-ee4c94a00117)


These ad hoc commands perform the same tasks as the tasks defined in your Ansible playbook but are executed individually on the command line.

Additional Features:

Change user Shell -

    ansible server1 -m user -a "name=Nitish shell=/bin/bash" -b

   ![image](https://github.com/vikram445/ansible/assets/79625874/8697ca81-a382-4757-a21d-f84bac48b27b)


Change user password -

    ansible server1 -m user -a "name=Nitish password='{{ '12345' | password_hash('sha512') }}'" -b

   ![image](https://github.com/vikram445/ansible/assets/79625874/eea98c82-97ec-4101-b69c-f523f0307758)

    

Delete user -

    ansible server1 -m user -a "name=Nitish state=absent remove=true " -b

   ![image](https://github.com/vikram445/ansible/assets/79625874/65d7344c-70d5-426d-b08f-f8692bf7f166)


Delete Group - 

    ansible server1 -m group -a "name=team1 state=absent " -b

   ![image](https://github.com/vikram445/ansible/assets/79625874/380f76b5-b622-45a3-9e68-eb6a59973a13)

    

List user or Team - 

    ansible server1 -m shell -a "getent group"

   ![image](https://github.com/vikram445/ansible/assets/79625874/b60c9730-3fc2-4992-86f8-4fc8fae374f8)

    
    ansible server1 -m shell -a "getent passwd"

   ![image](https://github.com/vikram445/ansible/assets/79625874/2efe6b05-5458-4ea1-b579-4cf3709ff827)

