"Assignment 5:
Topics Covered:  (User Authentication, User Authorization)
     Assignment on Authentication and Authorization
        Their is an organization which has 3 teams
            - Developer
            - Devops
            - Testing

![image](https://github.com/vikram445/ansible/assets/79625874/026dddde-472e-42bb-9df0-571373d98a3a)

 First you need to create 9 dummy jenkins jobs.Each job will print their jobname, build number.
            For Developer create 3 dummy jobs.In developer view
                job1:- dev-1
                job2:- dev-2
                job3:- dev-3                
            For Testing create 3 dummy jobs. In testing view
                job1:- test-1
                job2:- test-2
                job3:- test-3
            For Devops create 3 dummy jobs. In devops view
                job1:- devops-1
                job2:- devops-2
                job3:- devops-3

                
![image](https://github.com/vikram445/ansible/assets/79625874/2c7c3a14-e860-4e82-8837-1dc551d63a5d)

![image](https://github.com/vikram445/ansible/assets/79625874/ec070fab-06fe-4533-a47e-b024eea697da)
            

                
        Users in each team: 
            developer: [ They can see only dev jobs, can build it, see workspace and configure it ]
                - developer-1 
                - developer-2 
![image](https://github.com/vikram445/ansible/assets/79625874/ae736316-89cf-4533-b64b-99c815f6569b)

                
            testing: [ They can see all test jobs ,can build it, see workspace and can configure it, | They can also view dev jobs ]
                - testing-1 
                - testing-2 
![image](https://github.com/vikram445/ansible/assets/79625874/91fa03df-063c-4d4e-b2ab-bdd80fd3bff3)

                
            devops:  [ They can see all devops jobs ,can build it, see workspace and can configure it, | They can also view dev and test jobs  ]
                - devops-1 
                - devops-2

![image](https://github.com/vikram445/ansible/assets/79625874/ebae0e17-2f94-469f-9691-be60eb2003bb)

            admin
                -  admin-1 [ It will have full access ]
        See what Authorization strategy suits it and implement it.
        Also go through all authorization strategy
        Legacy mode
        Project Based
        Matrix Based
        Role-Based
        Point 2:-
        Enable SSO with Goggle"

![image](https://github.com/vikram445/ansible/assets/79625874/50cccd53-5db4-46b2-84c1-668ebe6a5097)


