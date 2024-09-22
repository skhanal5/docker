### Viewing Docker Info
View running containers:
`docker ps -a`

View all images:
`docker images`

### Building Images
Build image from Dockerfile:
`docker build -t [image name] [path to dockerfile]`

### Running Containers
Start container from image:
`docker run -ti [image id/name]` 

Create and enter container with bash:
`docker run -ti [image id/name] /bin/bash `

Publish a port in the container to a port in the local machine
`doocker run -p [local-machine-port]:[container-port]`
### Interacting with Containers
Enter running container with bash:
`docker exec -ti [image id/name] /bin/bash `