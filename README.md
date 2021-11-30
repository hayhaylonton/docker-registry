# docker-registry

step 1:<br>
create virtual host listen http

step 2:<br>
run command<br>
docker-compose run --rm  certbot certonly --webroot --webroot-path /var/www/certbot/ --dry-run -d sample.local --agree-tos -m your-email@local

step 3:<br>
run command<br>
docker-compose run --rm  certbot certonly --webroot --webroot-path /var/www/certbot/ -d sample.local

step 4:<br>
update virtual host add listen https

note:<br>
--reload nginx<br>
docker-compose exec reverse_proxy nginx -s reload

--add user basic auth<br>
docker run --entrypoint htpasswd httpd:2 -Bbn <user> <pass> > auth/htpasswd

--create random password<br>
openssl rand -base64 32

--Garbage collection<br>
docker-compose exec registry bin/registry garbage-collect /etc/docker/registry/config.yml