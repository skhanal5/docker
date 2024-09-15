### About
* `watch` is a dev tool that automatically updates and previews your running Compose services as you update your code
### Configuration
* `watch` needs two settings:
	* `path`
		* the files in the path to observer
	* `action`
		* trigger an action when a modification is detected
* Needs some [prerequisites](https://docs.docker.com/compose/file-watch/#prerequisites) to run as intended
#### Path and Target
* `path` is used to define a general file path
* `target` is used to define where to pass in the updated files that are observed in the path
	* this is where the syncing takes place
#### Example
```yaml
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
  redis:
    image: "redis:alpine"
```
### Running with Watch
* `docker compose watch` or `docker compose up --watch`
### Resources
1. [Compose Watch](https://docs.docker.com/compose/file-watch/)
