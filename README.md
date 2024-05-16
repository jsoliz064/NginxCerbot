1. Crear los directorios:

```
sudo mkdir -p ./certbot/www/.well-known/acme-challenge/
```

2. Asignar permisos

```
sudo chown -R www-data:www-data certbot/www
sudo chmod -R 755 certbot/www
```

3. Ejecutar docker-compose

```
docker-compose up -d
```

4. Test para agregar SSL

```
docker compose run --rm certbot certonly --webroot --webroot-path /var/www/certbot/ --dry-run -d example.org
```

5. Agregar SSL

```
docker compose run --rm certbot certonly --webroot --webroot-path /var/www/certbot/ -d example.org
```

6. Reinicie los contenedores

```
docker compose restart
```
7. Reiniciar nginx
```
docker compose exec webserver nginx -s reload
```

8. Renovar SSL

```
docker compose run --rm certbot renew
```