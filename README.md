# Development WordPress Website

This repository contains the configuration files for setting up a development WordPress website using Docker Compose. The WordPress version used is the latest available.

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

To set up the development WordPress website using these Docker Compose services, follow these steps:

1. Clone this repository to your local machine.

```shell
git clone https://github.com/GabrielRamirez/Wordpres-Dev.git
```

2. Make sure you have Docker and Docker Compose installed on your machine.

3. Open a terminal or command prompt and navigate to the cloned repository.

```shell
cd Wordpres-Dev
```

4. Customize the `nginx.conf` file if needed, to customize the Nginx configuration for the website.

5. Start the containers by running the following command:

```shell
docker-compose up -d
```

The `-d` flag runs the containers in detached mode, allowing you to continue using the terminal without blocking.

6. Wait for the containers to start up. This may take a few moments as the required Docker images are pulled.

7. Once the containers are up and running, you can access the WordPress site by opening your web browser and navigating to `http://localhost`. You can access the phpMyAdmin interface at `http://localhost/phpmyadmin/index.php`.

8. To stop the containers and remove them, run the following command:

```shell
docker-compose down
```

This will gracefully stop the containers and clean up the resources.

## License

This project is licensed under the [MIT License](LICENSE). Feel free to use and modify the files as needed.
