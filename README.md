# AWS & Instance Automation

### Four pillars

- Flexibility 
- Availability 
- Ease of Use 
- Robustness 


### AWS Avialability Zones

- The AWS Cloud spans 84 Availability Zones within 26 geographic regions around the world, with announced plans for 24 more Availability Zones and 8 more AWS Regions in Australia, India, Indonesia, Israel, New Zealand, Spain, Switzerland, and United Arab Emirates (UAE).

![image](https://user-images.githubusercontent.com/104793540/185908679-fa8e3631-13a6-448f-99aa-4dce13441921.png)

Private clouds for banks and goverment agencies 

![image](https://user-images.githubusercontent.com/104793540/185910165-283a7ce2-5ac8-47ab-b510-3899612901b5.png)



### User data for instance automation 

![image](https://user-images.githubusercontent.com/104793540/185909352-1eb1d4e8-332a-4187-a094-495426c99ef6.png)

On AWS

<div align="center">
  
![image](https://user-images.githubusercontent.com/104793540/185448666-63595b2b-530c-439e-bb9a-483115eddc51.png)
![image](https://user-images.githubusercontent.com/104793540/185448828-8e82c3a2-74c3-43cb-9fd4-b314379849a2.png)
![image](https://user-images.githubusercontent.com/104793540/185448957-d5823f02-46a5-47ca-bbb7-8974d16c9f78.png)
![image](https://user-images.githubusercontent.com/104793540/185449268-b5bdbc89-100a-4492-984b-928f77816059.png)
![image](https://user-images.githubusercontent.com/104793540/185449416-5e55df12-27cc-4653-bfd7-ac43e1932491.png)
![image](https://user-images.githubusercontent.com/104793540/185449473-00a7ee80-6b8e-45bf-8927-e225cf9b9d1a.png)
![image](https://user-images.githubusercontent.com/104793540/185449540-1719ba44-196f-43bd-8133-2a125f4855c6.png)
![image](https://user-images.githubusercontent.com/104793540/185449680-eac82c52-9d6b-414d-a116-6f4ad38e186e.png)
 </div>
 
  scripting 
  
 - `#!/bin/bash`
 - `sudo apt-get update`
 - `sudo apt-get upgrade`
 - `sudo apt install nginx –y`
 - 
 Review and Launch 
 
## AWS AMIs
 
### app user data setup

```
#!/bin/bash

sudo apt-get update -y
sudo apt-get upgrade -y

sudo apt install nginx -y
sudo systemctl restart nginx
sudo systemctl enable nginx


sudo apt-get purge nodejs npm
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install -y nodejs
sudo apt-get install npm -y

```

```
#!/bin/bash

sudo apt-get update -y
sudo apt-get upgrade -y

sudo apt install nginx -y
sudo systemctl restart nginx
sudo systemctl enable nginx


sudo apt-get purge nodejs npm
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install -y nodejs
sudo apt-get install npm -y

sudo apt install npm -y
npm install express -y
npm install mongoose -y

```

![image](https://user-images.githubusercontent.com/104793540/185957058-d3974c8c-3635-4662-83d9-c49c78a55b92.png)
![image](https://user-images.githubusercontent.com/104793540/185957163-829c610e-9c2e-420f-9616-f7a1ed1764d5.png)

migrating files from local host to instance:
- in local terminal run > scp -i ~/.ssh/eng122.pem -r /c/Users/Ayan/aws ubuntu@ec2-34-247-162-174.eu-west-1.compute.amazonaws.com: (ensure correct public ip4 dns for your instance and keyname&file path) 

- git clone is better and faster - REDO
- ssh into app ec2
- cd app
- sudo apt install npm
- npm install express -y
- npm install mongoose -y
- npm install
- npm start

![image](https://user-images.githubusercontent.com/104793540/185958290-5b377268-ed10-4159-8e04-4ca7bf605139.png)

![image](https://user-images.githubusercontent.com/104793540/185958201-b392dc2d-b9b9-4f87-a369-54e8a350b8dd.png)

reverse proxy:
- cd /etc
- cd nginx
- cd sites-available
- sudo nano default
- proxy_pass http://localhost:3000;
- sudo systemctl restart nginx
- cd app 
- npm start

In app make env variable persistent:
- The variable must be written in the .bashrc file in the home/ubuntu folder where .bashrc is located
- ls -a 
- sudo nano .bashrc > export DB_HOST=mongodb://IPv4_db_ip:27017/posts (public db up)
- set up env variable: export DB_HOST=mongodb://IPv4_db_ip:27017/posts then printenv DB_HOST
- cd app
- cd seeds
- node seed.js
- npm start

 ![image](https://user-images.githubusercontent.com/104793540/185964479-1fe23386-1306-4e66-829f-c706993c2af0.png)


### db user data setup

```
#!/bin/bash

sudo apt-get update -y

sudo apt-get upgrade -y

sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv D68FA50FEA312927

echo "deb https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list

sudo apt-get update -y

sudo apt-get upgrade -y

 sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20 

sudo systemctl restart mongod

sudo systemctl enable  mongod

sudo systemctl status  mongod
```

- include app private ipv4 in security group for port 27017
- edit mongodb file
- cd /etc
- sudo nano mongod.conf
- go to network interfaces change to 0.0.0.0 - cant do this in production
- sudo systemctl restart mongod sudo systemctl enable mongod sudo systemctl status mongocd

![image](https://user-images.githubusercontent.com/104793540/185965436-cd4ceb13-6e1d-4bc2-b567-55bd4c0cc657.png)



![image](https://user-images.githubusercontent.com/104793540/185966575-53107b71-69f3-4d58-ac35-f02256053637.png)

### app ami 

![image](https://user-images.githubusercontent.com/104793540/186126863-a7cebc3b-99af-4cf7-8783-7702880bc7a5.png)

```
#!/bin/bash

sudo apt-get update -y

sudo apt-get upgrade -y

sudo systemctl restart nginx -y

sudo systemctl enable nginx

git clone https://github.com/ASalad42/deployment.git

cd deployment

sudo chmod +x provision.sh

sudo ./provision.sh

```

### db ami 

```
#!/bin/bash

sudo apt-get update -y

sudo apt-get upgrade -y
sudo systemctl restart mongod

sudo systemctl enable  mongod

sudo systemctl status  mongod
```
