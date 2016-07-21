# dockerfiles


## Some images that should be used for data science

- jupyter/all-spark-notebook
- rocker/rstudio
- ubuntu
- tensorflow/tensorflow

## Case Problems

**when container can't use dns resolve hostname**

type on a host machine: `nmcli device list | grep 'IP4.DNS'` to find the ip

try run a container with `--dns <the ip>`
