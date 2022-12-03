# Docker - Ansible Assignment 


## Workflow:-

*  I chosen one assignment 

*  First of all I created a docker-compose.yml file
    
    ```version: "3.3"
     services:
      nginx_container:
       image: nginx:latest
       ports:
         - 80:80 ```

*  I composed a docker-compose.yml file by using the below command.
  
     ``` sudo docker compose up -d  ```
    
    ![Screenshot_20221201_013209](https://user-images.githubusercontent.com/116748521/204896855-9fa4aa82-aba4-48d7-a36c-e00cc76082df.png)



*  And also I created a playbook.yml file

     ```---
         - name: create nginx container using docker compose
           become: yes
           hosts: localhost
           tasks:
            - name: docker_compose nginix deployment
              community.docker.docker_compose:
                 project_src: /home/anji/ansible-docker-compose-deployment
                 files:
                   - "docker-compose.yml"
                 state: present

           become: true
           vars:
            - ansible_python_interpreter: /usr/bin/python3```
	


*  After that I run a command like.

    ``` sudo ansible-playbook playbook.yml ```

*  At that time I got an error like.

    ![Screenshot_20221201_013609](https://user-images.githubusercontent.com/116748521/204897622-c66b2ec5-4205-4199-a333-670b99e19406.png)

*  Because of I had some mistakes in playbook.yml 

*  After that I reopened my playbook.yml and I fixed my errors. At that
   time it was working like.

    ![Screenshot_20221201_014110](https://user-images.githubusercontent.com/116748521/204898482-672ce51d-ae73-40b3-82f0-b9cc947f5df3.png)

*  I created one new folder that was ```docker-port-binding``` by using below command 

     ``` mkdir docker-port-binding ```
    
*  I entered that folder by using the below command.

    ``` cd docker-port-binding ```

*  In docker-port-binding I wrote a ```script.sh``` file.

    ![Screenshot_20221201_015554](https://user-images.githubusercontent.com/116748521/204901009-4364f1ab-98db-4650-8467-02fd454046f3.png)

*  And also I gave  ``` a+x ```  to ``` script.sh ```
 
*  I run the script.sh by using the below command
   
     ``` ./script.sh  ```

*  I got a running container.

     ![Screenshot_20221201_020551](https://user-images.githubusercontent.com/116748521/204902894-78aede12-73ef-470b-b81b-4d118b7db7d6.png)

*  I created one more folder ``` docker-volume-mounting ``` by using the below command.
      
      ``` mkdir docker-volume-mounting ```

*  I entered that folder by using the below command.
 
     ``` cd docker-volume-mounting ```

*  In docker-volume-mounting I wrote a ``` script.sh ```

     ![Screenshot_20221201_021223](https://user-images.githubusercontent.com/116748521/204903907-d54e6514-b43c-4179-9a20-474d26e9b13e.png)


*  In ``` script.sh ``` I wrote a command like.

     ``` docker run --name my-container --mount type=bind source=/tmp,target=/tmp -d busybox:latest ```

*  And I ran below command like.

     ``` docker ps | grep my-container | grep -i up ```
       
     ![Screenshot_20221201_022215](https://user-images.githubusercontent.com/116748521/204905608-f926f09a-80f6-4c1f-a24f-7e6d33e1bbad.png)

*  And finally I used one more command like.
     ``` docker exec -it my-container /bin/bash cd /tmp;cat EOF >> abcd text << EOF ```
     
     ![Screenshot_20221201_022453](https://user-images.githubusercontent.com/116748521/204906061-4a2e3b27-edd7-43ab-a7ac-11fff19f9813.png)

*  And finally it was successfully completed.

      ![Screenshot_20221201_022623](https://user-images.githubusercontent.com/116748521/204906524-e821dd26-51a3-49b6-bc94-85e7063a5884.png)

