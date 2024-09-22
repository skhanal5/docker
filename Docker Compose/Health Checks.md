### About
* You can configure a `healthcheck` for your service to determine whether or not the container is healthy
#### Configuration
* Define the `healthcheck` block like so:
```yaml
healthcheck:
  test: ["CMD", "curl", "-f", "http://localhost"]
  interval: 1m30s
  timeout: 10s
  retries: 3
  start_period: 40s
  start_interval: 5s```
* `test` is the command to trigger a health check
* `interval` is how frequently to run a health check
	* the first check will run after however many of seconds you specify
	* subsequent attempts will be triggered the same amount of seconds after the previous check
* `timeout` is how long the check will wait
	* if it takes longer than this duration, then the check failed
* `retries` is the number of consecutive times it will take for the status to be `unhealthy` for that container
* `start_period` is how long the container needs to bootstrap
	* any failures during this time isn't counted in the `retries` counter