# dockerfiles


## Some images that should be used for data science

- jupyter/all-spark-notebook, docker-stacks repo
- rocker/rstudio
- tensorflow/tensorflow
- ubuntu
- alpine

## Case Problems

**when container can't use dns resolve hostname**

type on a host machine: `nmcli device list | grep 'IP4.DNS'` to find the ip

try run a container with `--dns <the ip>`
