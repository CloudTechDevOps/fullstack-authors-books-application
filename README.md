# Learn It Right Way
This project is a full-stack web application built using React js for the frontend, Express js for the backend, and MySQL as the database. The application is designed to demonstrate the implementation of a 3-tier architecture, where the presentation layer (React js), application logic layer (Express js), and data layer (MySQL) are separated into distinct tiers.


## User Interface Screenshots 
#### Dashboard
![Dashboard](./frontend/public/ss/dashboard.png)

#### Books
![Dashboard](./frontend/public/ss/books.png)

#### Authors
![Dashboard](./frontend/public/ss/authors.png)


# Setting up the Data Tier

```
create a rds database in sasme vpc
```
### Setting up the Application Tier

## conncet to your  backend instance

#### Install GIT
```
sudo yum update -y

sudo yum install git -y

git — version
```

#### Install node.js
1. To install node version manager (nvm)
```
sudo dnf install -y nodejs
```
### Install pm2
```
npm install -g pm2
```
### Install mysql or mariadb for database initilization
```
sudo yum install mariadb105-server -y
```
#### Clone repository
```
git clone https://github.com/CloudTechDevOps/fullstack-autors-books-application.git
```
### Switch to backend
```
cd fullstack-authors-books-application
cd backend
```
### change the database details  in db.js
### *** vi configs/db.js***
```
const mysql = require('mysql2');

const db = mysql.createConnection({
   host: 'rds endpoint',
   port: '3306',
   user: 'radmin',
   password: 'rds-password',
   database: 'react_node_app'
});

module.exports = db;
```
### Initilize the database 
```
mysql -h <rdsendpoint> -u admin -p<rdspassword> < db.sql


```
### Everything is completed run the follwing commnds for backend execution
```
npm install
pm2 start server.js --name "veera"
pm2 startup
sudo systemctl enable pm2-root
sudo pm2 save
```

## Setting up the Presentation Tier

# conncet to your  front end instance
#### Install GIT
```
sudo yum update -y

sudo yum install git -y

git — version
```

#### Install node.js
1. To install node version manager (nvm)
```
sudo dnf install -y nodejs
```
### Install httpd (apache)
```
sudo yum install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
```
#### Clone repository
```
git clone https://github.com/CloudTechDevOps/fullstack-autors-books-application.git
```
###Switch to frontend
```
cd fullstack-authors-books-application
cd frontend
```
### In frontend path .env file is there if not existis please create .env file 
```
VITE_API_URL=http://3.85.56.86/api   // for public deploymnet changee this ip accoording to your backned
VITE_API_URL= "/api"      // for proxy use this one
```
#### Run the following commnads in frontend 
```
npm install
npm run build
sudo cp -r dist/* /usr/share/nginx/html
```

### Now access the frontend with public ip 
### hit public ip you will get this responce 
#### Dashboard
![Dashboard](./frontend/public/ss/dashboard.png)

### add the autors and books 
                                                   thank you 

