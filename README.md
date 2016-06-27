# What's included?
Vagrant provisioned with
* Ubuntu 14.04 (64bit)
* PHP7 
* node 4.x
* MySQL 5.x
* Apache 2.x (>= 2.4)
  
see voodoo.sh for details, plugins and modules


# Setup

## Project settings
Clone this repository
```
git clone https://github.com/wskc/web-stack.git
```

Navigate to your project root and
```
vagrant up
```
This will provision the machine, set up the synced folder, permissions... (see voodoo.sh)

__Synced folder (default): `/var/www`__

Using the provided main.conf grants you full access to configure and enhance your virtual host.

Provide your server name in
```
ServerName PROJECTNAME.DOMAIN
```
go ahead and change the following (not required)
```
DocumentRoot /var/www
```
and
```
<Directory /var/www>
```

## Client settings
Add an host entry for your nutritious development universe, open your hosts file

#### OSX & Linux
```
/etc/hosts
```

#### Windows
```
C:\Windows\System32\drivers\etc
```

and add an new entry
```
127.0.0.1   myproject.local

```

---

## Reach your app
```
myproject.local:8080
```

---

# Details & default configuration
SSH Host / Port: 127.0.0.1:2222  
SSH User: vagrant  
SSH Password: vagrant  
DB Host: 127.0.0.1  
DB Port: 3306  
DB User: root  
DB Password: vagrant  
DB Default Schema: main  

Hostname: webstack.local  
Forwarded Port(s): 80 -> 8080  

MySQL will be installed while provisioning the machine.  
You can use it directly on the machine or via SSH tunnel (e.g. `ssh vagrant@127.0.0.1 -p 2222 -L 3306:localhost:3306`)

---

# Examples
### Laravel
```
<VirtualHost *:80>
    ServerName myfancyproject.local

    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/laravel/public

    ErrorLog ${APACHE_LOG_DIR}/main-error.log
    CustomLog ${APACHE_LOG_DIR}/main-access.log combined

</VirtualHost>
  
<Directory /var/www/laravel/public>
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
</Directory>
```

### Wordpress
```
<VirtualHost *:80>
    ServerName wordpress.local

    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/wp

    ErrorLog ${APACHE_LOG_DIR}/main-error.log
    CustomLog ${APACHE_LOG_DIR}/main-access.log combined

</VirtualHost>
  
<Directory /var/www/wp>
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
</Directory>
```

---

# Appendix
This is just a simple and quick way to set up an running development environment,  
**don't use any of those configurations or settings in production.**  
Feel free to contribute! :)