# Certboot Notes

### How to issue certificate using certboot.
After installing certboot tool. You can issue the following command to request SSL Certificate. In this command we used challange dns method.
with this certboot ask you to add TXT request on your domain's Authorotive DNS server.

```shell
# certbot certonly --manual --preferred-challenges dns --server https://acme-v02.api.letsencrypt.org/directory --manual-public-ip-logging-ok -d '*.manintheit.org'
```

After you the TXT record verified on your DNS server, it will issue SSL certificate with the following message. 

```console
IMPORTANT NOTES:
 - Congratulations! Your certificate and chain have been saved at:
   /etc/letsencrypt/live/manintheit.org/fullchain.pem
   Your key file has been saved at:
   /etc/letsencrypt/live/manintheit.org/privkey.pem
   Your cert will expire on 2021-04-09. To obtain a new or tweaked
   version of this certificate in the future, simply run certbot
   again. To non-interactively renew *all* of your certificates, run
   "certbot renew"
 - If you like Certbot, please consider supporting our work by:

   Donating to ISRG / Let's Encrypt:   https://letsencrypt.org/donate
   Donating to EFF:                    https://eff.org/donate-le
```


# LXC Notes

### Add port forwarding on LXC

```shell
#                 <container-name> <rule-name>    <IP and Port on host>  <IP and PORT on Container>      
# lxc config device add gohugo manintheit443 proxy listen=tcp:51.159.29.186:443 connect=tcp:127.0.0.1:443
```

### List Configs Device

```shell
#                      <container-name>
lxc config device list gohugo
```

### Remove Config Device

```shell       
#                   <container-name>   <rule-name>
lxc config device remove  gohugo manintheit443
```

