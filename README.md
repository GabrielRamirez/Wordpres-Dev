# Development WordPress Website

This repository contains the configuration files for setting up a development WordPress website using Docker containers. The version of WordPress used is "3".

## Services

The following services are included in this setup:

### db

- Image: mysql:5.7
- Restart policy: always
- Environment variables:
  - MYSQL_ROOT_PASSWORD: password1
  - MYSQL_DATABASE: wordpress
  - MYSQL_USER: admin
  - MYSQL_PASSWORD: password1

### wordpress

- Image: wordpress:latest
- Restart policy: always
- Environment variables:
  - WORDPRESS_DB_HOST: db
  - WORDPRESS_DB_USER: admin
  - WORDPRESS_DB_PASSWORD: password1
  - WORDPRESS_DB_NAME: wordpress

### phpmyadmin

- Image: phpmyadmin/phpmyadmin
- Restart policy: always
- Environment variables:
  - PMA_HOST: db
  - PMA_PORT: 3306
  - MYSQL_ROOT_PASSWORD: password1
  - MYSQL_USER: admin
  - MYSQL_PASSWORD: password1

### nginx

- Image: nginx:latest
- Restart policy: always
- Ports:
  - 80:80
- Volumes:
  - ./nginx.conf:/etc/nginx/conf.d/default.conf

## Usage

To set up the development WordPress website using these Docker containers, follow these steps:

1. Clone this repository to your local machine.
2. Make sure you have Docker installed.
3. Open a terminal or command prompt and navigate to the cloned repository.
4. Run the following command to start the containers:

```shell
docker-compose up -d
```

5. Wait for the containers to start up. Once they are running, you should be able to access the WordPress site at `http://localhost` and the phpMyAdmin interface at `http://localhost:8080`.
6. You can modify the `nginx.conf` file to customize the Nginx configuration for the website.

## License

This project is licensed under the [MIT License](LICENSE). Feel free to use and modify the files as needed.
