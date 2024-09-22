### About
* The `depends_on` attribute lets you configure the order services start and shutdown
#### Basic Example
```
services:
  web:
    build: .
    depends_on:
      - db
      - redis
  redis:
    image: redis
  db:
    image: postgres
```
* Here `redis` and `db` are created before `web`
	* They are also shut down before `web`
#### Advanced Example
```
services:
  web:
    build: .
    depends_on:
      db:
        condition: service_healthy
        restart: true
      redis:
        condition: service_started
  redis:
    image: redis
  db:
    image: postgres
```
* Here we specify that the condition of the dependent services `db` and `redis` must match before `service_healthy` and `service_created` before creating `web`
* `restart` is set to `true` which means this service is restarted once the dependent service is updated