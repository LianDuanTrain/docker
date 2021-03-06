# Sidecar Design Pattern 
- What is sidecar design pattern?
- How to use Docker compose implement sidecar design pattern?
  
## What is a sidecar design pattern?   

## How to use Docker compose implement sidecar design pattern?
- Multi-stage build Dockerfile
  - Src https://github.com/LianDuanTrain/DockerSpringBootDemo/tree/buildWarFile
- docker-compose.yml
  - Two services
    - warfile
      - Build war file
    - jetty
    
  - networks
     - webNet 
     - dataNet
  - volume
- Start Docker Compose   
  `docker-compose  up -d`   
- Check Docker Compose Status    
  `docker-compose ps`     
- Verify Network Isolated  
`docker network ls`      
`docker exec -it -u root  warfilev1 /bin/sh`  
    `apk add --no-cache ping`  
`docker network inspect XXX_dataNet`  
`docker network inspect XXX_webNet`  
- Verify Docker Volume  
   `docker volume ls`      
    `docker volume inspect dockercompose_war-data`   
    `docker container inspect wardatav1`   
    `docker container inspect jetty94v1`    
- Test API
  - Add user list  
    `curl -H "Accept: application/json" -H "Content-type: application/json" -d '{"lastName":"lian","firstName":"duan"}' -X POST 192.168.31.231:8080/demo/users`
  - Get Users  
    `curl 192.168.31.231:8080/demo/users`
- Shutdown    
`docker-compose down --help`    
`docker-compose down -v`  
- Combination Command  
  `docker-compose build --help`  
`docker-compose down -v && docker-compose build --no-cache && docker-compose up -d`
    


