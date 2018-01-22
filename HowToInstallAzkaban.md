<H1>How To Install Azkaban 2 or Multi Server Mode</H1>

1. download azkaban https://github.com/azkaban/azkaban/releases
2. extract the file to your install machine
3. go to azkaban folder(cd azkaban) and run command: ./gradlew build installDist

<H2> Install mysql server</H2>
1. run command to check if the mysql-server has already been installed <br/>
$ps -Af | grep mysqld<br/>
<br/>
2. install mysql by below command:<br/>
step1 - installing mysql<br/>
$sudo apt-get update<br/>
$sudo apt-get install mysql-server<br/>

step2 - configure mysql<br/>
$mysql_secure_installation<br/>

step3 - testing mysql<br/>
$systemctl status mysql.service<br/>
<br/>
3. create database and tables for azkaban<br/>
>> run below command:<br/>
$mysql -u root -p<br/>
$CREATE DATABASE IF NOT EXISTS azkaban;<br/>
$create user 'azkaban'@'localhost' IDENTIFIED BY ‘password’;<br/>
$./azkaban-3.40.0/azkaban-db/build/sql/create-all-sql-0.1.0-SNAPSHOT.sql<br/>
$GRANT ALL ON azkaban.* TO 'azkaban'@'localhost’; FLUSH PRIVILEGES;<br/>
<br/>
<h3>Install Executor Server</h3>

as root on node where executor service will be installed
>> cd azkaban-exec-server
>> mkdir conf
>> mkdir extlib
>> mkdir plugins
>> mkdir plugins/jobtypes/
>> cp mysql-connector-java-5.1.40-bin.jar extlib/
>> vi plugins/jobtypes/commonprivate.properties
- execute.as.user=false
>> chown azkaban.azkaban /usr/local/azkaban-exec-server/



