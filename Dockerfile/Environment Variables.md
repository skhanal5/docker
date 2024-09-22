### About
* 
### ARG
* variables defined with `ARG` are only available when the container is building
	* think of them as build-time vars
* When the container starts, you cannot reference them anymore inside of it
#### Usage
##### Defining ARG Values in the Dockerfile
* Example:
```yaml
ARG foo
ARG foo=default # uses default if foo is undefined
```
##### Providing ARG Values
* You can pass in `ARG` in the cli with `docker build --build-arg foo=bar`
* Alternatively, look at [[Docker Compose/Environment Variables|Docker Compose Environment Variables]] to see how it can be set using docker-compose
### ENV
* variables defined with `ARG` are available when the container is building **AND** when the container is running
#### Usage
##### Defining ENV Values in the Dockerfile
* Example:
```yaml
ENV foo=bar
ENV bar baz # = isn't needed
```
 * **Note**: unlike `ARG`, `ENV` doesn't allow for default values, you must have a default
##### Dynamic ENV Variables
* You can define an `ARG` as a placeholder default and and set it to an `ENV`
* Example:
```yaml
ARG FOO
ENV foo_actual = $FOO
```
* Here `foo_actual` starts with the value of `FOO` but can be overridden  
##### Providing ENV Values
* `docker run -e "foo_action=bar" ...`
	* `-e` flag to pass in env values
* Alternatively, look at [[Docker Compose/Environment Variables|Docker Compose Environment Variables]] to see how it can be set using docker-compose
### Aside: Helpful Tip
* Use `docker inspect [image-id]` to see which `ENV` have been set