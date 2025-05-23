# grafana
grafana by docker	
Step 1: Create a docker-compose.yml file for Grafana
Create a directory and a compose file
####################

mkdir grafana
cd grafana
nano docker-compose.yml

####################
after pasting content run fllowing command
####################

docker-compose up -d

####################
Step 2: Set up your subdomain
Go to your DNS provider panel (Cloudflare, your hosting panel, etc.) and create an A record:
********************

Type: A
Name: grafana
Value: <Your server's public IP>
TTL: 300

********************
Step 3: Install and configure NGINX as a reverse proxy
Install NGINX:
####################

sudo apt install nginx -y

####################
Create a new configuration file:
####################

sudo nano /etc/nginx/sites-available/grafana

####################
Paste configuration of grafana
Then Enable it:
####################

sudo ln -s /etc/nginx/sites-available/grafana /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl reload nginx

####################
Step 4: (Optional but recommended) Enable HTTPS with Let's Encrypt
Install Certbot:
####################

sudo apt install certbot python3-certbot-nginx -y

####################
Obtain a free SSL certificate:
####################

sudo certbot --nginx -d grafana.example.com

####################
Step 5: Access Grafana
Now, open your browser and visit:
********************

http://grafana.example.com

********************
or if SSL is enabled:

********************

https://grafana.example.com


********************
Default login credentials:

Username: admin

Password: admin (you will be asked to change it)
