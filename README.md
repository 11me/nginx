# Nginx config as reverse proxy
1. Install nginx
```sh
sudo apt install nginx
```
2. Install certbot
```sh
sudo apt install certbot
```
3. Obtain certs
```sh
sudo certbot certonly --standalone --preferred-challenges http -d example.com
```
4. Copy example.com.conf
```sh
cp exmaple.com.conf sites/my-domain.com.conf
```
DO NOT FORGET TO CHANGE CONTENT OF example.com.conf

5. Change the `/etc/nginx/nginx.conf`
```sh
echo "include $(pwd)/nginx.conf" > /etc/nginx/nginx.conf
```
6. In the current nginx.conf replace the `include` to you directory
```sh
sed "s|#Sites|include $(pwd)/nginx/sites/\*\.conf|g" nginx.conf
```
7. Test configuration
```sh
nginx -t
```
8. Reload nginx
```sh
nginx -s reload
```
