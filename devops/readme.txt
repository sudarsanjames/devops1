#export DOCKER_HOME=localhost:4243
echo PWD
cd ${WORKSPACE}/devops/ubuntu
docker build -t james/ansible-ubuntu-1:jen .
cd ../centos
docker build -t james/ansible-centos:jen .
======================================

https://github.com/sudarsanjames/devops1.git

======================================
