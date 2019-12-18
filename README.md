This is working code of accessing springboot REST API through zuul over https using nginx


nginx.conf file is to be added to /etc/nginx/sites-enabled inside aws vm instance

Steps to verify the setup

1) run docker container of mongo for springboot application

command --  docker run --name mongo -d  -p 27017:27017 mongo 

2) build the image of demoMongoDb and run in container

 commands -- 1) docker build -t demo-boot .
             2) docker run -d -p 8080:8080 demo-boot
             
3) build the image of zuul-gateway and run in container        

 commands -- 1) docker build -t zuul .
             2) docker run -d -p 8092:8092 zuul 
             
 Testing the setup
 
 1) url to store data to mongo
 
    --- aws-ip:8080/create?firstName=firstnamedemo&lastName=lastnamedemo&age=25
    We can see one use created
 
 2) accessing through zuul
 
 ---https://demo-test.stackroute.io:8099/demo-mongo/getAll
 
 we will get data 
