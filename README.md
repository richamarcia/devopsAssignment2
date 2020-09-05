# devopsAssignment2

### creating directory
![image1](images/img1.png)

### creating compose file
![image2](images/docker-compose.png)

### docker-compose.yml
```commandline
version: '2'

services:

  drupal:
    build: .
    ports:
      - 8080:80
    volumes:
      - web-modules:/var/www/html/modules
      - web-profiles:/var/www/html/profiles
      - web-themes:/var/www/html/themes
      - web-sites:/var/www/html/sites

  postgres:
    image: postgres:12.1
    environment:
      POSTGRES_PASSWORD: admin
    volumes:
      - web-data:/var/lib/postgresql/data

volumes:
  web-data:
  web-modules:
  web-profiles:
  web-themes:
  web-sites:
```
### Running compose file
![image3](images/img3.png)
### creating Dockerfile
![image4](images/img2.png)
### Dockerfile
```commandline
FROM drupal:8
RUN apt-get update && apt-get install -y git && rm -rf /var/lib/apt/lists/*
WORKDIR ~/var/www/html/themes
RUN git clone --branch 8.x-3.x --single-branch --depth 1 https://git.drupal.org/project/bootstrap.git && chown -R www-data:www-data bootstrap
WORKDIR ~/custom-drupal

```

### List the container
![image5](images/ps.png)

### commit custom-image
![image6](images/commit.png)
### tag custom-image
![image7](images/tag.png)
### push to docker hub
![image8](images/push.png)
### config on port 8080

![image9](images/custom-image.png)

![image9](images/richacustom-image.png)


