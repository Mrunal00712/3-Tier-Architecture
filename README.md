# **3-Tier-Architecture**
'''
User --> WebApp(Word Press)  --> DataBase(My-SQL)

first we have to launch the mysql database , i'm launching the my sql data base with volume so that if my data base goes down my data will store in the HOST os ,, My-SQL server stores data in /var/lib/mysql



Step 1 : Launching MY-SQL database
[root@ip-172-31-23-32 ~]# docker run -dit --name db -e MYSQL_ROOT_PASSWORD=redhat -e MYSQL_DATADASE=mydb  -e MYSQL_USER=vimal  -e MYSQL_PASSWORD=redhat  -v  /mydata:/var/lib/mysql  mysql:latest


Good network practice is if two operating systems want to connect  with each other don’t rely on IP address for the connection  The one thing we never change in the container is the name Instead of using an IP address, we can use a name this concept is called container linking 


Step 2 : launching WordPress 
[root@ip-172-31-23-32 ~]# docker run -dit --name mywp -p 8080:80 --link db wordpress:latest

Step 3 : Go to browser
URL : hostip:8080/wp-admin/setup-config.php


// HelpFul commands
#docker inspect (containerID/Name) --> to get the ip adderss of cantainer
#docker rm -f $(docker ps -a -q)
'''
