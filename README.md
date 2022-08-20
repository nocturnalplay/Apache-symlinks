# Apache-symlinks


> nocturnalplay is a username and demo is my source dir for the web page

## default Apache web server dir in linux /var/www/html
> make symlink to another dir with this comment 

```
ln -s <source> <destination>
sudo ln -s /home/nocturnalplay/demo /var/www/html
```

## then check if it is connected or not
> with this source dir ls -l

## After we need to verify if the user can send the data as www-data form
> check this out

> sudo -u www-data ls -l /var/www/html/ /home/nocturnalplay/demo
  
> gives out like this below
  
```
home/nocturnalplay/demo/:
total 4
-rwxrwxr-x 1 root root 22 Aug 20 22:17 index.html
/var/www/html/:
total 0
lrwxrwxrwx 1 root root 26 Aug 20 22:28 index.html -> /home/nocturnalplay/demo/index.html
```

## if permission denied happend

```
  sudo chmod 750 nocturnalplay
  sudo adduser www-data nocturnalplay
```
> now repeat the same process 
```
sudo -u www-data ls -l /var/www/html/ /home/nocturnalplay/demo 
```
## add .htaccess file and place the following cmd to run .php files

```
Options +FollowSymLinks +SymLinksIfOwnerMatch
```
  
## all done 
> sudo service apache2 restart
