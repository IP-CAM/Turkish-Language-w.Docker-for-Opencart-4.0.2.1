# Docker compose Opencart-4.0.2.1 with Turkish language implemented

## Overview
- Opencart 4.0.2.1 Turkish
- Docker
- mysql
- phpmyadmin
- php-8.x


## ENV VARIABLES 

- [DockerOpencart/docker-compose.yml](./DockerOpencart/docker-compose.yml)

```yml 
version: '3.0'

services:
  opencart4x_tr:
    restart: always
    build: .
    ports:
      - 9060:80     # opencart http port mapping
    environment:
      installation_db_hostname: mysql_db
      installation_db_port: 3306
      installation_db_database: 'acunstoredb'  # default database
      installation_db_username: 'root'    # mysql db user
      installation_db_password: 'root'    # mysql db pass
      installation_username: 'bolubeyi'  # Admin panel (/vezir) username
      installation_password: 'koroglu'   # admin pass
      installation_email: 'shamancoders@gmail.com' # admin user email
  
  mysql_db:
    image: mysql:latest
    command: --default-authentication-plugin=mysql_native_password
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: ${installation_db_password}
      MYSQL_DATABASE: ${installation_db_database}

  phpmyadmin:
    image: phpmyadmin:latest
    restart: always
    ports:
      - 9061:80   # PhpMyAdmin port mapping
    environment:
      - PMA_ARBITRARY=1
```

## Docker Compose

```bash
docker compose -f "DockerOpencart\docker-compose.yml" up -d --build
```
or
```bash
cd DockerOpencart

docker compose up -d --build
```

## License

[MIT License](./LICENSE)

## For more information

[https://miajupiter.com](https://miajupiter.com)