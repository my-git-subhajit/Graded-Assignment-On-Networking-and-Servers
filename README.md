# Graded-Assignment-On-Networking-and-Servers

# Step 1: Launch an ec2 instance
# Login to AWS account > click on launch instance > give a name to the server, select ubuntu OS, select a key pair, and also make sure to add the right Security Group so that you can SSH into the server.
# Once the instance's up and running, SSH into the server.
ssh -i "myEC2key01.pem" ubuntu@54.82.44.176

# Change to root user

sudo -i

# update OS

apt-get update && apt-get upgrade -y

# installing wget, wget will be used to download from a website

apt-get install wget -y

# Step 2: installing nginx

apt-get install nginx -y

# start nginx service

systemctl start nginx

# check the status of the service

systemctl status nginx

# Once checked it's up and running, enable the service

systemctl enable nginx
# also use the open the public ip, to check if the nginx default page populates.

# installing unzip

apt-get install unzip -y

# Step 3: downloading template

wget https://www.tooplate.com/zip-templates/2098_health.zip

# unzip the zip file

unzip 2098_health.zip

# copy all the files in the extracted folder to /var/www/html

cp -r 2098_health/* /var/www/html

# restart nginx service

systemctl restart nginx

# open the website and you will see that the new website is deployed.

# Step 4: Navigate to /etc/nginx/sites-available/default

vim default

# change to insert mode

server {
   listen 80;
   listen [::]:80;

   server_name awesomeweb.com;
};

# save the file

# restart nginx service

systemctl restart nginx
