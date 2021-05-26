# Generar Certificado Wildcard

```bash
sudo certbot certonly --manual -d [*.dominio.wildcard] -d [dominio.com] --agree-tos --no-bootstrap --manual-public-ip-logging-ok --preferred-challenges dns-01 --server https://acme-v02.api.letsencrypt.org/directory
```



