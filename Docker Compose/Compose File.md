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
* 


### Resources
1. [Getting Started with Compose](https://docs.docker.com/compose/gettingstarted/)
2. [Docker Compose App Model](https://docs.docker.com/compose/compose-application-model/) 