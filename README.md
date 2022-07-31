# Envirionment docker4drupal and drupal-project

- PHP 8.1-dev-4.37.4
- nginx 1.21-5.24.1
- MySQL 5.7
- mariadb 10.8-3.21.0
- mailhog:latest 
- traefik:v2.0 
- phpmyadmin:latest
- Drupal 9-4.44.7

> You can change the specificities of the environment by editing the file `.env`

> Documentation
https://github.com/Wodby/docker4drupal
[How to use](https://wodby.com/docs/1.0/stacks/drupal/local/#usage)

# Installation

> Clone this repo 
```shell
git clone https://github.com/Yorik56/drupal9 project_name
```

> cd into the project_name folder
```shell   
cd projet_name
```

> Run the following command to install the Docker images and run the containers
```shell    
docker-compose up
```

> Launch the PHP container
```shell
docker exec -it my_drupal9_project_php /bin/bash
```

> Run the following command to install Drupal
```shell
composer install
```

> Launch the Drupal website
http://drupal.docker.localhost:8000/

> Launch PHPMyAdmin
http://pma.drupal.docker.localhost:8000/
