## Dockerfiles for research
### Run on GPU
- build
```
$ git clone https://github.com/johshisha/docker_for_research && cd docker_for_research
$ docker build -t [tag]:[version] -f ./Dockerfile.gpu ./ --build-arg PASSWD=docker_user_password
```
- run jupyter notebook
```
$ nvidia-docker run --rm -it -p 8888:8888 -v "$PWD":/home/docker/work [tag]:[version] jupyter-notebook --ip=0.0.0.0
# access `http://0.0.0.0:8888/?token=~~~`
```

- run bash
```
$ nvidia-docker run --rm -it -p 8888:8888 -v "$PWD":/home/docker/work [tag]:[version] /bin/bash
```

### Run on CPU
- build
```
$ git clone https://github.com/johshisha/docker_for_research && cd docker_for_research
$ docker build -t [tag]:[version] -f ./Dockerfile.cpu ./ --build-arg PASSWD=docker_user_password
```
- run jupyter notebook
```
$ docker run --rm -it -p 8888:8888 -v "$PWD":/home/docker/work [tag]:[version] jupyter-notebook --ip=0.0.0.0
# access `http://0.0.0.0:8888/?token=~~~`
```

- run bash
```
$ docker run --rm -it -p 8888:8888 -v "$PWD":/home/docker/work [tag]:[version] /bin/bash
```


