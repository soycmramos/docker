docker container run `
-dp 3306:3306 `
--name world-db `
--env MARIADB_USER=example-user `
--env MARIADB_PASSWORD=user-password `
--env MARIADB_ROOT_PASSWORD=root-secret-password `
--env MARIADB_DATABASE=world-db `
--volume world-db:/var/lib/mysql `
mariadb:jammy

docker container run `
--name phpmyadmin `
-e PMA_ARBITRARY=1 `
-dp 8080:80 `
phpmyadmin:5.2.0-apache

docker container run `
--name nest-app `
-w /app `
-p 80:3000 `
-v ${pwd}:/app `
node:18-alpine3.16 `
sh -c "yarn install && yarn start:dev"