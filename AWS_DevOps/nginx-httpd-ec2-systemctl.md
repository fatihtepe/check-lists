- to see all running services
```
systemctl -a
```
- nginx and httpd do not work at same time and to stop one of the.

```
systemctl stop nginx
```
or 
```
systemctil stop httpd
```
to activate
```
systemctl start httppd
```
port 80: nginx and httpd use same both if you run both of them at the same time. They will not run(crush)

```to remove nginx from your ec2```
```
sudo yum remove nginx
``` 

