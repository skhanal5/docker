### About
- A YAML file to configure your app's services
- Defined by the `Compose Specification`
#### Offered Features
- Fragments
- Extensions
- Merging Compose Files
- Splitting/Reusing Compose files
### Learn from Example
#### Basic Compose File
```yaml
services:
  web:
    build: .
    ports:
      - "8000:5000"
  redis:
    image: "redis:alpine"
```
* Two services defined: `web` and `redis`
* Web:
	* Built from a [[Dockerfile/Basics|Dockerfile]]
	* Binds container port 5000 to a machine port 8000
* Redis:
	* Uses existing Redis image
* To run this, view [[Interacting with Compose]]
#### More Realistic Example
```yaml
services:
  frontend:
    image: example/webapp
    ports:
      - "443:8043"
    networks:
      - front-tier
      - back-tier
    configs:
      - httpd-config
    secrets:
      - server-certificate

  backend:
    image: example/database
    volumes:
      - db-data:/etc/data
    networks:
      - back-tier

volumes:
  db-data:
    driver: flocker
    driver_opts:
      size: "10GiB"

configs:
  httpd-config:
    external: true

secrets:
  server-certificate:
    external: true

networks:
  # The presence of these objects is sufficient to define them
  front-tier: {}
  back-tier: {}
```
### Include
* You can use the `include` top-level attribute in your compose.yaml to include an existing yaml file containing a service
* Example of a infra.yaml file:
```yaml
services:
  redis:
    image: "redis:alpine"
```
* Example of a compose.yaml file:
```yaml
include:
   - infra.yaml
services:
  web:
    build: .
    ports:
      - "8000:5000"
    develop:
      watch:
        - action: sync
          path: .
          target: /code
```

### Resources
1. [Getting Started with Compose](https://docs.docker.com/compose/gettingstarted/)
2. [Docker Compose App Model](https://docs.docker.com/compose/compose-application-model/) 