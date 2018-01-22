<H1>How To Install Azkaban 2 or Multi Server Mode</H1>

1. download azkaban https://github.com/azkaban/azkaban/releases
2. extract the file to your install machine
3. go to azkaban folder(cd azkaban) and run command: ./gradlew build installDist

<H2> Install mysql server</H2>
1. run command to check if the mysql-server has already been installed <br/>
$ps -Af | grep mysqld<br/>
<br/>
2. install mysql by below command:
step1 - installing mysql<br/>
$sudo apt-get update<br/>
$sudo apt-get install mysql-server<br/>

step2 - configure mysql<br/>
$mysql_secure_installation

step3 - testing mysql
$systemctl status mysql.service
<br/>
3. create database and tables for azkaban
run below command:
$mysql -u root -p
$CREATE DATABASE IF NOT EXISTS azkaban;
$create user 'azkaban'@'localhost' IDENTIFIED BY ‘password’;
$./azkaban-3.40.0/azkaban-db/build/sql/create-all-sql-0.1.0-SNAPSHOT.sql
$GRANT ALL ON azkaban.* TO 'azkaban'@'localhost’; FLUSH PRIVILEGES;
<br/>
<h3>Install Executor Server</h3>


