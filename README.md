# ansible-role-compile-ambertools

Ansible role to compile ambertools and produce a binary tarball

## Compile using a docker container

Run a docker with mounting a volume that will have the binary tarball
The compilation will be dane manually for now

```
mkdir ambertar
export MDIR=`pwd`/ambertar
docker run -it -v /home:$MDIR -w /home lipcomputing/ansible-ubuntu16.04 /bin/bash
ansible-galaxy install git+https://github.com/LIP-Computing/ansible-role-compile-ambertools.git
export AMBERHOME=/home/amber16
cd $AMBERHOME
./configure -mpi -noX11 gnu
```
