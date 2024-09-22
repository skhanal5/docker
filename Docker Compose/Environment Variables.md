### About
* Compose by default looks for a `.env` file in the root of the project directory
* Using this, it does simple find and replace for any environment variables in the compose file 
	* Those variables must be defined like so `${VALUE_TO_REPLACE}`
* **note**: any environment variables on your host take precedence over the ones in `.env`
#### Structure
* The `.env` file should look like this
```
ENVIRONMENT_VAR=value
```
### Passing Environment Variables
* You can use the `envrionment` block and pass in each environment variable one by one
* Example:
```yaml
services:
	foo:
		image: bar
		environment:
			- baz = bin
			- ban = ${bore}
```

### Passing Arguments
* Example:
```
services:
	foo:
		image: bar
		args:
			baz = bin
```