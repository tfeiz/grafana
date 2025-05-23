# grafana
<br>
grafana by docker	
<br>
Step 1:
<br>
Create a docker-compose.yml file for Grafana
Create a directory and a compose file


```bash
mkdir grafana
cd grafana
nano docker-compose.yml
```

after pasting content run fllowing command

```bash
docker-compose up -d
```
<br>
Step 2:
<br>
Set up your subdomain
<br>
Go to your DNS provider panel (Cloudflare, your hosting panel, etc.) and create an A record:
<br>

```bash
Type: A
Name: grafana
TTL: 300
TTL: 300
```
<br>
Step 3: 
<br>
Install and configure NGINX as a reverse proxy
<br>
Install NGINX:


```bash
sudo apt install nginx -y
```

Create a new configuration file:
<br>
```bash
sudo nano /etc/nginx/sites-available/grafana
```
Paste configuration of grafana
Then Enable it:
```bash
sudo ln -s /etc/nginx/sites-available/grafana /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl reload nginx
```
<br>

Step 4: 
<br>
(Optional but recommended) Enable HTTPS with Let's Encrypt
<br>
Install Certbot:
<br>
```bash
sudo apt install certbot python3-certbot-nginx -y
```
<br>

Obtain a free SSL certificate:
<br>

```bash
sudo certbot --nginx -d grafana.example.com
```

<br>

Step 5: 
<br>
Access Grafana
<br>
Now, open your browser and visit:
<br>

http://grafana.example.com

<br>
or if SSL is enabled:

<br>

https://grafana.example.com


<br>
Default login credentials:
<br>

Username: admin
<br>

Password: admin (you will be asked to change it)
