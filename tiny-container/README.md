## Docker build process

* build `docker build -t tiny-container .`
* list `docker image ls`
* run with your image id `docker run -it tiny-container /bin/bash repeat.sh 4 hello`

### Push to DockerHub

* docker login: `docker login -u <hub-user>`
* build and tag locally: `docker build . -t <hub-user>/<repo-name>`
* docker push <repository-name>
* Verify you can run it by pulling from Docker Hub:  https://hub.docker.com/r/fermiyon/tiny-container/tags
* docker pull fermiyon/tiny-container
* docker run -it <hub-user>/<repo-name>:latest /bin/bash repeat.sh 4 hello

211
* docker run -it fermiyon/tiny-container:latest
* `ls`
* `exit`

Example would be:
`docker run -it fermiyon/tiny-container:latest /bin/bash repeat.sh 4 hello`

### Run in Cloud9

* run locally:  `docker run -it fermiyon/tiny-container-demo:latest /bin/bash repeat.sh 4 hello`
* retag and push:  
Example (replace with your info): `docker push 561744971673.dkr.ecr.us-east-1.amazonaws.com/awscli:tiny`
* verify it runs in a new cloud9 instance: `docker run -it 561744971673.dkr.ecr.us-east-1.amazonaws.com/awscli:tiny /bin/bash repeat.sh 4 hello`