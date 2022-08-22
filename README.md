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
 - `sudo systemctl install nginx`
 - 
 Review and Launch 
 
## AWS AMIs
 
### app user data setup

```
#!/bin/bash

sudo apt-get update -y

sudo apt-get upgrade -y

sudo systemctl install nginx -y

sudo systemctl start nginx 

sudo systemctl enable nginx

sudo apt-get purge nodejs npm

curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -

sudo apt-get install -y nodejs

sudo apt-get install -y npm

sudo npm install pm2 -g

sudo apt-get update -y

sudo apt-get upgrade -y

```

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

### app ami 



### db ami 
