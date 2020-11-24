# Advanced Wordpress Deployment

Scalable Wordpress deployment using [Swarm](https://docs.docker.com/engine/swarm/) and [Traefik](https://traefik.io/)

## Requirements
* [Docker in Swarm mode](https://docs.docker.com/engine/reference/commandline/swarm_init/)
* [Docker Compose](https://docs.docker.com/compose/)

## Run the app

```
# Init Docker Swarm
docker swarm init

# Create and start containers
docker-compose --compatibility up -d

# Wait until containers up, or you will get error 502
watch 'docker ps --format="table {{.Names}}\t{{.Status}}"'

# Access Wordpress endpoint
http://localhost

# If this the first time you run the app, you need to finish Wordpress installation
# https://wordpress.org/support/article/how-to-install-wordpress/#finishing-installation
 ```

## Scale the app

```
# Edit replicas and port ranges in docker-compose.yaml file

   deploy:
      replicas: 5 # e.g if you change the replicas from 3 to 5 
    ports:
      - "7000-7004" # you need to change the ports range from 7000-7002 to 7000-7004 as well

# Create and start containers
docker-compose --compatibility up -d

# Access Wordpress endpoint in your browser
http://localhost
 ```
