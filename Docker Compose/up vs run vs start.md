### up
* Usage: `docker compose up`
* Used to start/restart all services in your YAML file
* compose will exit once the containers have been started, but the containers will run in the background 
### run
* Usage: `docker compose run`
* Used to run one off tasks
	* Examples:
		* Running tests
		* Admin tasks 
* Needs the service name that you want to run and will only start the necessary containers for that service
* Side effect: opens up a terminal to the container
### start
* usage: `docker compose start`
* Used to restart containers that were previously created but stopped