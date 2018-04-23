# Redirect request from http to https using cloudflare ssl certificate

If you want to redirect part of a site not the whole website using CloudFlare SSL certificate, add this line below to nginx configuration file.
 Make sure you use "Flexible SSL" there so CloudFlare proxies traffic from HTTPS to Nginx's HTTP port (80)

```
 location  /login {
        if ($http_cf_visitor ~ '{"scheme":"http"}'){
                rewrite ^(.*) https://$host$request_uri break;
}
```


