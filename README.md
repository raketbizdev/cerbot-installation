# Fresh cerbot Installation

1. Goto https://certbot.eff.org/
2. Select type of `Webserver` and `OS`. You will see instruction below once you selecte Webserver and OS follow the instructions.
3. Your Done.

Note: you need to run as admin to to the server.

# Cerbot Already Install

1. Check if Cerbot is already installed by typing `apt-cache policy certbot | grep Installed` apt for ubunto yum for linux anc centos.
2. once you find `cerbot-auto shell` move that copy to your root folder and make sure the cerbot file is permission 755.
3. then run 
```
sudo ./certbot-auto certonly  --webroot -w /your/root/folder -d www.yourdomain.com -d yourdomain.com -d search.yourdomain.com
```
4. If you have different webroot add this filter `--webroot -w /your/root/folder` and add this to your virtual host or server block 
```
location ^~ /.well-known/acme-challenge/ {

  default_type "text/plain";
  root         /your/root/folder;

 }

 location = /.well-known/acme-challenge/ {
  return 404;
 }
```
5 done.
