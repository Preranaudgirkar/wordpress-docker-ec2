 WordPress + MySQL on Docker (AWS EC2)
 Overview
This project demonstrates deploying WordPress using Docker containers on an AWS EC2 instance.

 Architecture
- MySQL Container → Database (stores WordPress data)
- WordPress Container → Application

 Setup Steps

 1. Install Docker
sudo dnf install docker -y
sudo systemctl start docker

 2. Run MySQL Container
docker run -d --name mydb \
-e MYSQL_ROOT_PASSWORD=root \
-e MYSQL_DATABASE=wordpressdb \
mysql

 3. Run WordPress Container
docker run -d -p 8080:80 --name mywordpress \
-e WORDPRESS_DB_HOST=mydb:3306 \
-e WORDPRESS_DB_USER=root \
-e WORDPRESS_DB_PASSWORD=root \
-e WORDPRESS_DB_NAME=wordpressdb \
--link mydb:mysql \
wordpress

 Access
http://<your-ec2-public-ip>:8080

 Learning
- Docker basics
- Container communication
- Deploying apps on AWS EC2
