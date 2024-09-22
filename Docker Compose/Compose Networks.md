### About
* Compose sets up a single network for all services in your app
* Each container corresponding to a service joins the network and is reachable by other contains on the network
### Learn by Example
#### Scenario
* If your project is in a directory called `app` and you define the following `compose.yml` file:
```yaml
services:
  web:
    build: .
    ports:
      - "8000:8000"
  db:
    image: postgres
    ports:
      - "8001:5432"
```
#### Network Creation
* Running `docker compose up` will trigger the following: 
	* A network called `app_default` is created
	* `web` container is made
		* `web` joins the network under the name `web`
	* `db` container is made
		* `db` joins the network under the name `db`
#### Network Discovery
*  `web` can connect to `db` using the URL `postgres://db:5432`
	* **Note:**
		* the hostname is resolved to the name of the service
		* the port is the exposed container port and not the machine port
### Resources
1. [Networking in Compose](https://docs.docker.com/compose/how-tos/networking/)\
