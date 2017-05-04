# ansible-role-compile-ambertools

Ansible role to compile ambertools and produce a binary tarball

## Compile using a docker container

Run a docker with mounting a volume that will have the binary tarball

```
mkdir ambertar
export MDIR=`pwd`/ambertar
docker run -it -v /home:$MDIR -w /home lipcomputing/ansible-ubuntu16.04 /bin/bash

```
