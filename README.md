# nginx-seesaw
nginx reverse proxy config for Seesaw

# Usage
Tested on nginx 1.10.3 on Ubuntu 16.04

You'll need a Linux machine ideally located in non-google-blocking destinations with decent access speed from mainland China. e.g HongKong, China

1. Install nginx and grab a wildcard *.yourdomain.com SSL certificate, using Let's Encrypt, example config uses let's encrypt and certificates are located under /etc/letsencrypt/live/yourdomain.com/
2. Generate df file by running 
`sudo openssl dhparam -out /etc/nginx/ssl/dhp-4096.pem 4096`
3. Add dns A record for the following domains (replace with your actual domain):
`ajax-googleapis.yourdomain.com`
`apis-google.yourdomain.com`
`seesaw-upload.yourdomain.com`
`seesaw-dynassets.yourdomain.com`
`seesaw-assets.yourdomain.com`
`seesaw-events.yourdomain.com`
`seesaw-imaging.yourdomain.com`
`seesaw-files.yourdomain.com`
`seesaw.yourdomain.com`
and point them all to your server's external IP address
4. replace yourdomain.com with your actual domain in the config by running (where xxx.com is your actual domain):
`sed -i 's/yourdomain.com/xxx.com/g' googleapis.conf`
`sed -i 's/yourdomain.com/xxx.com/g' seesaw.conf`
`sed -i 's/.yourdomain(rs)?\\.com/.xxx(rs)?\\.com/g' client.js`
`sed -i 's/yourdomain.com/xxx.com/g' client.js`

5. copy the seesaw.conf, googleapis.conf over to your nginx config directory, gzip.conf to /etc/nginx/, and client.js to /usr/share/nginx/googleapis/client.js
6. reload nginx and visit https://seesaw.xxx.com to see the seesaw login page.
