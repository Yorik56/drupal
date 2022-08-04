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

> Clone this project 
```shell
git clone https://github.com/Yorik56/drupal9 project_name
```

> cd into the project_name folder
```shell   
cd project_name
```

> Run the following command to install the Docker images and run the containers
```shell    
docker-compose up
```

> Launch the PHP container
```shell
docker exec -it my_drupal9_project_php /bin/bash
```

> Run the following command to install Drupal 9 (at the root of the projet inside the container "/var/www/html")
```shell
composer install
```

> Create the "config/sync" folder and set the right permissions
```shell
mkdir /var/www/html/config &&
mkdir /var/www/html/config/sync &&
sudo chmod 777 /var/www/html/config &&
sudo chmod 777 /var/www/html/config/sync
```

> Launch the Drupal website, you will be redirected to the installation page of the website

http://drupal.docker.localhost:8000/

```yaml
# .env
DB_NAME=drupal
DB_USER=drupal
DB_PASSWORD=drupal
DB_HOST=mariadb
DB_PORT=3306
```


> Launch PHPMyAdmin

http://pma.drupal.docker.localhost:8000/

# Extensions & Themes installation

> Launch the PHP container
```shell
docker exec -it my_drupal9_project_php /bin/bash
```

> Installation Drush (at the root of the projet inside the container "/var/www/html")
```shell
composer require drush/drush:^10 -W
```
> Installation Admin toolbar drupal 8||9||10 (at the root of the projet inside the container "/var/www/html")
```shell
composer require 'drupal/admin_toolbar:^3.1'
```

> Installation of the theme Gin (at the root of the projet inside the container "/var/www/html")
```shell
composer require drupal/gin_toolbar:^1.0@beta drupal/gin:^3.0@beta
```

> Enable theme gin (at the root of the projet inside the container "/var/www/html")

```shell
vendor/bin/drush theme:enable gin
```

> Set gin as default theme (at the root of the projet inside the container "/var/www/html")

```shell
vendor/bin/drush cset system.theme default gin
Do you want to update default key in system.theme config? (yes/no) [yes]: (ENTER)
```
> Set gin as admin theme  (at the root of the projet inside the container "/var/www/html")

```shell
vendor/bin/drush cset system.theme admin gin 
Do you want to update default key in system.theme config? (yes/no) [yes]: (ENTER)
```

> Enable modules admin_toolbar, gin_toolbar  (at the root of the projet inside the container "/var/www/html")
```shell
vendor/bin/drush en admin_toolbar admin_toolbar_tools gin_toolbar
```
