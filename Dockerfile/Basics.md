### Usage
* Think of it as a the instructions needed to create a Docker image
### Best Practices
#### Versioning
- Use explicit versions for base images 
	- Do not use "latest", it can break things unexpectedly
	- Explicitly defining a version ensures consistency
		- Using latest means one build to the next can be completely different
- For language specific images, make sure the versions line up for compatibility
- Define the SHA256 hash for the most precision when it comes to base images
#### File Management
- The image should only contain what you need for it to build your application
- View `.dockerignore` for more information on how to exclude certain things
#### Multiple Stages
* Separate the build stage from the stage that runs your application
#### Working Directory
- Use `WORKDIR` to establish the working directory for subsequent commands
	- Used by `RUN`, etc.
- Why?
	- Some commands assume the root directory
####  Root User
- Do not use the root user to execute commands
	- Principle of least privilege
- See if a user is already provided in the base image and use that with `USER`
- Else create your own user group and add your user to that group
### Debugging
- If one of your steps failed and you don't know what to do (error message isn't immediately obvious), there are a couple of options
- A:
	- Comment out problematic line and all lines after that, build again
	- Manually run the command in the container
- B: 
	- Use layer to start a new container
### Resources
1. [Dockerfile Reference](https://docs.docker.com/reference/dockerfile/)
2. [Building best practices](https://docs.docker.com/build/building/best-practices/)
3. [Java Containers Best Practices](https://docs.docker.com/reference/dockerfile/)

