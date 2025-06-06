# 🚀 Node.js Application to Check Database Connection

This project demonstrates how to set up a Node.js app in Docker to connect with a MySQL database.

1. Install docker on Ubuntu
```sudo apt update -y && sudo curl https://get.docker.com | bash```
2. `git clone https://github.com/awsdevop183/nodejs-mysql-test.git`

3. Update app.js file with appropriate DB credentials

4. Connect to your DB and Create Database and Table as per mysql.db file

5. Create Docker image with `docker build -t testdb .`

6. Create a container from the image `docker run -d --name db -p 90:3000 testdb`




# Node Application to check ASG

1. Create an EC2(Ubuntu) for Mysql
2. Install Docker using `curl https://get.docker.com | bash`
3. Then run `docker run -d --name mysql-server -e MYSQL_ROOT_PASSWORD=Admin123 -p 3306:3306 mysql:8.0`
4. `docker ps` (to get container_id)
5. `docker exec -it container_id bash`
6.  `sudo apt install mysql-server -y` (To install mysql)
7.  `mysql -u root -p` (then enter admin password from above command)
8.  `ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'Admin123';
    FLUSH PRIVILEGES;` (type this is mysql prompt to change password if not set or if necessary.)
    
9.   ```
      CREATE USER 'admin'@'%' IDENTIFIED BY 'Admin123';
      GRANT ALL PRIVILEGES ON *.* TO 'admin'@'%' WITH GRANT OPTION;
      FLUSH PRIVILEGES;
      CREATE DATABASE movieDB;
     ```

10. `USE movieDB;`
```
CREATE TABLE movies (
id INT AUTO_INCREMENT PRIMARY KEY,
title VARCHAR(255) NOT NULL,
genre VARCHAR(50),
release_year INT);

INSERT INTO movies (title, genre, release_year) VALUES
('Inception', 'Sci-Fi', 2010),
('The Matrix', 'Sci-Fi', 1999),
('Interstellar', 'Sci-Fi', 2014),
('The Godfather', 'Crime', 1972),
('Pulp Fiction', 'Crime', 1994);
```
11. Run this command in /home/ubuntu# and Change bind address to 0.0.0.0
    
`sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf`

`sudo systemctl restart mysql`

===========================================================================
# Create another Instance:
# Strictly Mysql, No Docker

`git clone https://github.com/awsdevop183/nodejs-mysql-test.git`

`cd nodejs-mysql-test`

Update app.js with Mysql Instance Private IP

Do `curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -`

Do `sudo apt install nodejs -y`

`node app.js` (Output: Server is running on http://localhost:3000
Connected to the MySQL database.)

✅`npm install` ( ❗ Error: Cannot find module 'express' occurs)

✅ `lsof -i :3000` (❗ Error: Port 3000 already in use)
DO `kill -9 PID` ( # To kill PID)

Visit in browser: http://your-ec2-ip:3000/

============================================================================
# Create another Instance:
# Strictly using Docker

`git clone https://github.com/awsdevop183/nodejs-mysql-test.git`

`cd nodejs-mysql-test`

Update app.js with Mysql Instance Private IP

Install docker on Ubuntu if working along with docker.

```sudo apt update -y && sudo curl https://get.docker.com | bash```

`docker build -t movies .`

`docker run -d --name movies -p 80:3000 movies`

`docker update --restart=always movies`
