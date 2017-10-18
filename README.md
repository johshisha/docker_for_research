## Dockerfiles for research

### Install dockers
- [install docker on ubuntu](./install_dockers.md)

### Sample
Sample for creating new environment on gpu.  
(If you want to create environment on cpu, replace `for_research_on_gpu` to `for_research_on_cpu` in Dockerfile.)
```
$ wget https://raw.githubusercontent.com/johshisha/docker_for_research/master/sample/Dockerfile
$ touch requirements.txt # and edit if you want
$ docker build -t sample/sample .
$ nvidia-docker run --rm -it -p 8888:8888 -v "$PWD":/home/docker/work sample/sample /bin/bash # If on cpu, replace nvidia-docker to docker
```


## Build and Run on GPU
- build
```
$ git clone https://github.com/johshisha/docker_for_research && cd docker_for_research
$ docker build -t [tag]:[version] -f ./dockers/build/Dockerfile.gpu . --build-arg PASSWD=docker_user_password
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

## Build and Run on CPU
- build
```
$ git clone https://github.com/johshisha/docker_for_research && cd docker_for_research
$ docker build -t [tag]:[version] -f ./dockers/build/Dockerfile.cpu . --build-arg PASSWD=docker_user_password
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
